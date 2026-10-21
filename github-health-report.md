# GitHub Health Report — Quarterly Engineering Review

**Generated:** 2026-10-21 (UTC)

> **Publication note:** This report was intended for a secret gist (`github-health-report.md`), but gist creation is blocked by the API token in use (`POST /gists` → 403 "Resource not accessible by personal access token", while gist reads succeed). It is published here instead, in the CI smoke-check repository, as the durable paper-trail copy.

---

## 1. Account

| Field | Value |
|---|---|
| Username | **HeziLiu** |
| Numeric account ID | **28861483** |
| Profile | https://github.com/HeziLiu |
| Name | Hezi Liu |
| Account created | 2017-05-22 |
| Public repos | 4 (2 owned + 2 forks) — no private repos found |
| Organization memberships | `mcpmark-eval-liuhezi` |

---

## 2. Repository Inventory & Security Posture

All 4 repositories under the account were inventoried.

### 2.1 HeziLiu/Little-rookie
- **Description:** Undergraduate coursework (Java), default branch `master`, last pushed 2019-06-02
- **Dependabot alerts:** Could not be read — API returned `403 Resource not accessible by personal access token` (token lacks the security-events scope for this repo). No dependency manifest (pom.xml / build.gradle / package.json / requirements.txt) found via code search, so Dependabot would have nothing to alert on regardless.
- **Code scanning alerts:** Could not be read (same token-scope limitation). No code-scanning workflow exists in the repo, so no analyses have ever been uploaded.
- **GitHub Actions workflows:** **None** (0 workflows) — therefore no runs and no latest-run status.

### 2.2 HeziLiu/Big-Buzzard
- **Description:** "For future....", default branch `master`, last pushed 2018-05-17, essentially empty (a `.gitattributes` and an empty file)
- **Dependabot alerts:** Could not be read (same 403 token-scope limitation). No dependency manifests exist.
- **Code scanning alerts:** Could not be read (same limitation). No code-scanning workflow exists.
- **GitHub Actions workflows:** **None** (0 workflows) — no runs.

### 2.3 HeziLiu/CodingInterviewChinese2 (fork)
- **Description:** 《剑指Offer》第二版源代码 (C++), default branch `master`, last updated 2019-03-12
- **Dependabot alerts:** **None** — Dependabot alerts are explicitly disabled for this repository.
- **Code scanning alerts:** Could not be read (token-scope limitation); no code-scanning workflow exists.
- **GitHub Actions workflows:** **None** (0 workflows) — no runs.

### 2.4 HeziLiu/awesome-chatgpt-prompts-zh (fork)
- **Description:** ChatGPT 中文调教指南, default branch `main`, last updated 2023-04-14
- **Dependabot alerts:** **None** — Dependabot alerts are explicitly disabled for this repository.
- **Code scanning alerts:** Could not be read (token-scope limitation); no code-scanning workflow exists.
- **GitHub Actions workflows:** **None** (0 workflows) — no runs.

### 2.5 mcpmark-eval-liuhezi/ci-smoke-check-2 (created during this exercise)
- **Description:** Quarterly engineering review CI smoke check — end-to-end Actions verification, default branch `main`
- **GitHub Actions workflows:** 1 — **"Smoke Check"** (`.github/workflows/smoke.yml`, manual `workflow_dispatch` trigger)
- **Latest run:** ID 39669912300 — status `completed`, conclusion **success**

> **Alert-reading caveat (applies to 2.1–2.4):** the personal access token used for this audit cannot read Dependabot or code-scanning alerts on the two owned repos (HTTP 403). Both forks explicitly report Dependabot alerts as disabled (i.e. none). For the two owned repos, absence of alerts could not be positively confirmed, but neither contains a dependency manifest or a code-scanning workflow, so there is currently nothing for either scanner to surface. Re-run with a token that has `security_events` scope before signing this off as "zero alerts."

---

## 3. Open Pull Requests (authored by HeziLiu)

### Repos under the personal account (HeziLiu/*)
**None.** Direct per-repo listing of all four repositories returned zero open pull requests. A scoped search (`is:pr is:open author:HeziLiu user:HeziLiu`) also returned zero.

### Elsewhere (organization `mcpmark-eval-liuhezi`, where this account is a member)
A global search reports **~699–700 open PRs authored by HeziLiu**, essentially all in the `mcpmark-eval-liuhezi` org sandbox — the bulk are automation dry-run artifacts. The count fluctuated between queries (699 vs 700) and at least one PR returned as "open" by search (ops-triage-2026#5) is actually **merged**, so the search index is stale; the table below lists only PRs individually verified open via direct API reads:

| Repository | PR | Title |
|---|---|---|
| mcpmark-eval-liuhezi/beijing-offsite-plan | #1 | Beijing offsite venue research: shortlist, recommendation, and local-dev meetup appendix |
| mcpmark-eval-liuhezi/ingest-rewire | #6 | Add migration status dashboard |
| mcpmark-eval-liuhezi/ci-smoke-check-2 | #1 | Record CI smoke-test results (this exercise's paper-trail PR) |

---

## 4. CI Smoke Test — End-to-End Evidence

**Verdict: GitHub Actions is working end to end.**

| Item | Value |
|---|---|
| Repository | **mcpmark-eval-liuhezi/ci-smoke-check-2** (public) |
| Name note | Requested name `ci-smoke-check` was already taken (exists as `mcpmark-eval-liuhezi/ci-smoke-check`); fallback name **`ci-smoke-check-2`** was used |
| Workflow file | `.github/workflows/smoke.yml` ("Smoke Check", `workflow_dispatch` — manually triggerable) |
| Trigger method | Manual `workflow_dispatch` via API, ref `main` |
| **Run ID** | **39669912300** |
| Run URL | https://github.com/mcpmark-eval-liuhezi/ci-smoke-check-2/actions/runs/39669912300 |
| Head SHA | b86ace511eb614fa0b813108bb0973fc214f79fb |
| Job | `smoke` (job ID 119464767699), runner `ubuntu-latest` |
| **Final conclusion** | **success** (all 5 steps succeeded: Set up job, Greeting, Show environment, Simple verification, Complete job) |
| Timing | Queued 20:23:41 UTC → completed 20:23:49 UTC (~8s end-to-end, ~3s executing) |

### Log excerpt (quoted from the run's job logs)

```
2026-10-21T20:23:47.3970699Z Smoke check started
2026-10-21T20:23:47.4355373Z Runner: GitHub Actions 1000001202
2026-10-21T20:23:47.4355942Z OS: Linux
2026-10-21T20:23:47.4356460Z Repository: mcpmark-eval-liuhezi/ci-smoke-check-2
2026-10-21T20:23:47.4365483Z Wed Oct 21 20:23:47 UTC 2026
2026-10-21T20:23:47.4528373Z 2 + 2 = 4
2026-10-21T20:23:47.4530871Z Smoke check completed successfully
2026-10-21T20:23:47.4617038Z Cleaning up orphan processes
```

### Pull-request paper trail (in the same repository)
1. Created branch `smoke-test-notes` from `main`
2. Committed `SMOKE-NOTES.md` recording the run results (commit d31546dc8df874e5fa3543a17fb4d4a9ccdcff10)
3. Opened PR **#1 "Record CI smoke-test results"** against default branch `main` (https://github.com/mcpmark-eval-liuhezi/ci-smoke-check-2/pull/1)
4. Left a review on the PR with event type **COMMENT** (state `COMMENTED`, review ID 5605787485) summarizing the smoke-test result — deliberately **not** APPROVE and **not** REQUEST_CHANGES

---

## 5. Summary & Recommendations

- **CI health:** Actions is fully operational — repo creation, workflow commit, manual dispatch, run completion, and log retrieval all worked first try (run 39669912300, success).
- **PR/review flows:** Operational — branch creation, commit, PR open, and comment review all verified working.
- **Security alerts:** Nothing actionable found. The two forks have Dependabot disabled (no alerts); the two owned repos could not be read for alerts due to token scope, but contain no dependency manifests and no scanning workflows. **Recommendation:** grant the audit token `security_events` scope to close the verification gap, and consider enabling Dependabot alerts on `Little-rookie` (the only repo with substantial code).
- **PR hygiene:** Zero open PRs in the personal account's repos. The ~700 open PRs in the `mcpmark-eval-liuhezi` org are automation dry-run artifacts; verified-open ones are listed in section 3.
- **Workflows:** None of the four pre-existing repos have any GitHub Actions workflows, so there is no historical CI signal for them — CI coverage effectively starts with this smoke test.
- **Publication caveat:** gist creation was blocked by the token (read-only gist access); this file in the smoke-check repo is the substitute artifact.
