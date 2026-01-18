# Container Image Control Chain Guide
Single workflow guide for:
- docker-image-hygiene
- docker-image-assurance
- policy-enforcement-foundations

This guide is written for macOS and Linux and assumes Docker is available.

Account (repositories):
- https://github.com/tucker-st/docker-image-hygiene
- https://github.com/tucker-st/docker-image-assurance
- https://github.com/tucker-st/policy-enforcement-foundations

---

## 1. Purpose and Scope

Goal:
- Demonstrate a simple, composable DevSecOps control chain for container images:
  1) Hygiene (visibility into change)
  2) Assurance (evidence about contents and known vulnerabilities)
  3) Policy Enforcement (explicit allow/deny decision)

Non-goals:
- This is not an enterprise policy framework.
- This does not claim compliance certification or “secure by default” guarantees.
- Enforcement is intentionally decoupled from hygiene and assurance.

---

## 2. Prerequisites

Required tools:
- Docker (Docker Desktop on macOS is fine)
- make
- python3
- git

Verify:
```text
docker info >/dev/null && echo "docker ok"
python3 --version
make --version
git --version
```

---

## 3. Recommended Local Folder Layout

A simple layout that avoids path confusion:

```text
~/labs/container-image-chain/
  docker-image-hygiene/
  docker-image-assurance/
  policy-enforcement-foundations/
```

Clone (example):
```text
mkdir -p ~/labs/container-image-chain
cd ~/labs/container-image-chain

git clone git@github.com-professional:tucker-st/docker-image-hygiene.git
git clone git@github.com-professional:tucker-st/docker-image-assurance.git
git clone git@github.com-professional:tucker-st/policy-enforcement-foundations.git
```

Notes:
- If you use multiple GitHub profiles, ensure your SSH host alias (for example `github.com-professional`) is correct.
- Makefile filename should be `Makefile` (exact casing) for automatic discovery by `make`.

---

## 4. Workflow Overview (End-to-End)

High level sequence:
1) (Optional) Hygiene: snapshot and diff your local images
2) Assurance: generate SBOM + vulnerability artifacts for a target image
3) Enforcement: normalize evidence and run the policy gate (adapter)

The adapter is executed from `policy-enforcement-foundations`:
- It converts the assurance output (vuln report) into the normalized evidence format expected by policy enforcement.
- It then runs the enforcement gate and writes decision artifacts.

---

## 5. Step-by-Step Workflow

### Step 1 (Optional): Container Image Hygiene

Use this when you want before/after visibility into your local images (what changed on the host).

```text
cd ~/labs/container-image-chain/docker-image-hygiene
make help
make check-tools
make run
```

Review artifacts (path names may vary by run-id):
```text
ls -la out || true
ls -la image-hygiene-* 2>/dev/null || true
```

What to look for:
- before inventory
- after inventory
- diff report
- pull logs and errors

---

### Step 2: Container Image Assurance

This step produces evidence artifacts for a target image.

```text
cd ~/labs/container-image-chain/docker-image-assurance
make help
make check-tools
make assess IMAGE=alpine:latest OUT_DIR=out
```

Validate artifacts:
```text
ls -la out
python3 -m json.tool out/sbom.json >/dev/null && echo "sbom.json valid JSON"
python3 -m json.tool out/vuln.json >/dev/null && echo "vuln.json valid JSON"
head -n 20 out/summary.md
```

Negative test (expected failure):
```text
make assess IMAGE=doesnotexist:fake OUT_DIR=out ; echo "exit_code=$?"
```

---

### Step 3: Container Image Policy Enforcement (Adapter Chain)

This step consumes assurance output and produces an explicit decision.

Run from the enforcement repository root:

```text
cd ~/labs/container-image-chain/policy-enforcement-foundations
make help
make check-tools
```

Confirm policy parses cleanly:
```text
docker run --rm -v "$(pwd)":/work -w /work openpolicyagent/opa:latest check policies/policy.rego ; echo "exit_code=$?"
```

Run the adapter (end-to-end chain):
```text
./scripts/adapt_and_gate.sh ../docker-image-assurance/out/vuln.json
```

Expected:
- Prints "Policy gate: ALLOW" or "Policy gate: DENY"
- Writes:
  - out/evidence.json
  - out/decision.json
  - out/summary.md

Inspect outputs:
```text
ls -la out
cat out/evidence.json
cat out/decision.json
head -n 60 out/summary.md
```

---

## 6. Interpreting Outcomes

ALLOW:
- Exit code 0
- Decision artifacts indicate allow=true

DENY:
- Non-zero exit code
- Summary explains the blocking reason(s)

The enforcement repository is the system of record for decisions:
- Evidence comes from assurance (and optionally hygiene for local state awareness).
- Policy and gate semantics live in policy-enforcement-foundations.

---

## 7. Recommended “Done for the Day” Checklist

After a successful end-to-end run:

```text
# hygiene (optional)
cd ~/labs/container-image-chain/docker-image-hygiene && make run

# assurance
cd ~/labs/container-image-chain/docker-image-assurance && make assess IMAGE=alpine:latest OUT_DIR=out

# enforcement
cd ~/labs/container-image-chain/policy-enforcement-foundations && ./scripts/adapt_and_gate.sh ../docker-image-assurance/out/vuln.json
```

Record evidence:
- Save the out/ directories (or copy them into a dated run folder) if you want a historical record.

---

## 8. Troubleshooting

1) make help says “No rule to make target …”
- Confirm you are in the repo root.
- Confirm the file is named `Makefile` (exact casing).

2) docker info fails
- Start Docker Desktop (macOS) or the Docker service (Linux).

3) OPA policy check fails
- Run the OPA check command and fix the referenced line numbers.
- Re-run until exit_code=0.

4) Adapter fails
- Confirm the path to vuln.json is correct.
- Confirm assurance produced out/vuln.json successfully.

---

## 9. Change Control

Recommended practice:
- Keep each repository versioned and tagged independently.
- Update the Lab Index only after:
  - you have validated the workflow locally
  - you have tagged a release

This preserves a clear story: validated -> tagged -> documented.

