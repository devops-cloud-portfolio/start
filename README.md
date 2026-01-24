# DevOps Cloud Project

## What this is

This is my DevOps project built like a small “mini-production” setup.\
It’s based on a real workload and a full delivery chain:

CI (GitHub Actions), container images (GHCR), GitOps (Argo CD), Kubernetes, security & observability, backup/restore drills, IaC (Terraform), host automation (Ansible), CKA practice.

Goal: in ~10 minutes you can click through the key parts and quickly verify the process and evidence.

## 10-minute demo path (v0)

1. **Docs hub (architecture and decisions)**
   Architecture v0:

- TODO: paste full GitHub URL to "devops-docs/docs/architecture/architecture-v0.md"
  ADR 0001 (repo structure):
- TODO: paste full GitHub URL to "devops-docs/docs/decisions/0001-repo-structure.md"

2. **CI evidence**

- Go to the **Actions** tab and check the latest runs:
  - `markdownlint`
  - `yamllint`
  - `actionlint`
- CI badge at the top of this README should match the workflow status (optional).

> Note: for v0 this is mostly documentation-driven. Live Kubernetes/GitOps deployment comes later.

## Repositories

- `start` - landing page
- `devops-docs` - architecture, ADRs, runbooks, drills, CKA notes
- `agent-service` - workload app (API, worker, Redis, Postgres) *(planned)*
- `platform-k8s-gitops` - Argo CD, dev stage, manifests Helm *(planned)*
- `infra-aws-terraform` - IaC (AWS, Terraform), remote state, CI *(planned)*
- `ansible-ops` - host bootstrap, self-hosted GitHub Runner *(planned)*
- `agent-service-gitlab-ci` - GitLab CI compatibility proof *(planned)*

## What you can check

### CI Quality gates

- [x] Pull Request flow (branch protection + PR template)
- [x] Required status checks on `main`
- [x] Docs linting in CI: markdownlint, yamllint, actionlint

### GitOps Kubernetes (planned)

- [ ] Argo CD sync from Git repo
- [ ] Environments: dev (auto-sync), stage (promotion via PR)
- [ ] Helm chart, manifest validation

### Security (planned)

- [ ] Secret scanning in CI
- [ ] Container image scanning in CI
- [ ] Kubernetes baseline security (PSA, non-root, RBAC, NetworkPolicy)

### Observability (planned)

- [ ] Metrics, alerts and dashboards
- [ ] Logs (Loki, Grafana)
- [ ] Runbooks for common failures

### DR / Backup & Restore (planned)

- [ ] Scheduled database backups
- [ ] Documented restore test and report

### IaC (planned)

- [ ] Terraform remote state and CI
- [ ] AWS auth via OIDC

## Roadmap (16 weeks)

- Week 1: repo structure, docs hub, CI quality gates ✅
- Week 2: minimal workload locally (API, worker, Redis, Postgres)
- Week 3-4: CI build policy and security scans
- Week 5: Ansible and self-hosted runner
- Week 6-10: Kubernetes, Helm, GitOps, secrets, NetworkPolicy
- Week 11-12: Observability and backup/restore drill
- Week 13-14: AWS Terraform, Terraform to Ansible chain and CKA simulation
- Week 15-16: incident drill, postmortem, GitLab CI proof and final pack

## Contract

- Everything goes through Pull Requests.
- No secrets in the repo.
- Key steps are reproducible and documented.
