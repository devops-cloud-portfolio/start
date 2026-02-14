# DevOps Cloud Project

[![ci](https://github.com/devops-cloud-portfolio/start/actions/workflows/ci.yml/badge.svg)](https://github.com/devops-cloud-portfolio/start/actions/workflows/ci.yml)

## What this is

This is my DevOps project built like a small “mini-production” setup.\
It’s based on a real workload and a full delivery chain:

CI (GitHub Actions), container images (GHCR), GitOps (Argo CD), Kubernetes, security & observability, backup/restore drills, IaC (Terraform), host automation (Ansible), CKA practice.

Goal: in ~10 minutes you can click through the key parts and quickly verify the process and evidence.

## 10-minute demo path (v0)

1. **Docs hub (architecture and decisions)**

   Architecture v0:

   - [Architecture v0](https://github.com/devops-cloud-portfolio/devops-docs/blob/main/docs/architecture/architecture-v0.md)
     ADR 0001 (repo structure):
   - [ADR 0001](https://github.com/devops-cloud-portfolio/devops-docs/blob/main/docs/decisions/0001-repo-structure.md)

1. **CI evidence**

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

## Roadmap

- [x] Basics: org, repo structure, PR rules, CI for docs (markdownlint, yamllint, actionlint)
- [ ] Workload MVP (local): API, worker, Redis, Postgres, docker-compose
- [ ] CI build/publish rules: PR no push, main SHA tag, release semver tag, GHCR
- [ ] Security in CI: secret scan, image scan, reports as artifacts
- [ ] Automation: Ansible bootstrap, self-hosted GitHub Runner, rebuild runbook
- [ ] Kubernetes deploy: probes, resources, RBAC, securityContext
- [ ] Helm: chart, manifest validation, basic security baseline
- [ ] GitOps: Argo CD (dev/stage), promotion via PR
- [ ] GitOps secrets: SOPS, age, NetworkPolicy
- [ ] Observability: dashboards, alerts, runbooks
- [ ] Backup/restore: scheduled backup, restore test report
- [ ] IaC: AWS, Terraform (OIDC), CI checks
- [ ] Incident drill: incident test, postmortem, GitLab CI proof
- [ ] Final: clean “10-min demo path”, links to evidence

## Contract

- Everything goes through Pull Requests.
- No secrets in the repo.
- Key steps are reproducible and documented.

## Security note

Never commit secrets. Use GitHub Secrets and encrypted GitOps secrets.
