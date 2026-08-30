# Profitable AI List Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Publish a maintainable Awesome List of AI products with verifiable commercial traction.

**Architecture:** Keep the curated dataset in the root README using uniform, source-backed list entries. Put contribution governance in repository community files and enforce formatting and link health with GitHub Actions plus local checks.

**Tech Stack:** GitHub Flavored Markdown, GitHub issue forms, GitHub Actions, `awesome-lint`, Lychee.

**Spec:** `docs/superpowers/specs/2026-08-30-profitable-ai-list-design.md`

## Global Constraints

- Write public-facing content in English.
- Keep product descriptions neutral and end every list entry with a period.
- Label commercial evidence as exactly `Revenue`, `Customers`, `Funding`, or `Paid product`.
- Never present funding, pricing, users, or downloads as revenue.
- Include a direct source and visible year where the source exposes one.
- Apply the same evidence and disclosure rules to maintainer-associated products, including Formind and Veline AI.
- Order products alphabetically within each category.
- Use CC0 1.0 for the curated dataset.

---

### Task 1: Build the Curated README

**Files:**
- Modify: `README.md`

**Interfaces:**
- Consumes: Research results containing canonical URLs and evidence sources.
- Produces: The category anchors and entry format used by contribution templates and validation.

- [ ] **Step 1: Define the README structure**

Add the title, Awesome badge, theme description, scope note, flat `Contents`, commercial-signal legend, category headings, methodology, and contribution section specified in the design.

- [ ] **Step 2: Add researched products**

Normalize accepted research into this exact shape:

```markdown
- [Product](https://product.example) - Objective description. **Revenue:** Evidence claim ([source, 2026](https://source.example)).
```

- [ ] **Step 3: Run structural assertions**

Run:

```bash
rg '^## ' README.md
rg -n 'Formind|Veline AI' README.md
rg '^- \[' README.md | sort | uniq -d
```

Expected: all designed sections appear; Formind and Veline AI are present with the standard evidence format, and the duplicate-entry search prints nothing.

- [ ] **Step 4: Review every evidence sentence**

Read each entry and confirm that its wording matches its bold evidence label and linked source.

### Task 2: Add Contribution Governance

**Files:**
- Create: `CONTRIBUTING.md`
- Create: `CODE_OF_CONDUCT.md`
- Create: `.github/ISSUE_TEMPLATE/add-product.yml`
- Create: `.github/ISSUE_TEMPLATE/report-problem.yml`
- Create: `.github/ISSUE_TEMPLATE/config.yml`
- Create: `.github/pull_request_template.md`

**Interfaces:**
- Consumes: README evidence classes and entry format from Task 1.
- Produces: A single nomination workflow with disclosure and evidence requirements.

- [ ] **Step 1: Write contribution rules**

Document eligibility, exclusions, source priority, evidence labels, alphabetical placement, relationship disclosure, and the exact entry template.

- [ ] **Step 2: Add structured issue forms**

Require product URL, category, objective description, signal class, evidence claim, evidence URL, evidence date, and submitter relationship for nominations. Require affected entry, problem type, explanation, and supporting URL for corrections.

- [ ] **Step 3: Add pull-request checks**

Require contributors to confirm eligibility, direct sourcing, neutral copy, alphabetical placement, relationship disclosure, and local linting.

- [ ] **Step 4: Validate YAML syntax**

Run:

```bash
ruby -e 'require "yaml"; Dir[".github/**/*.yml"].each { |f| YAML.load_file(f); puts f }'
```

Expected: every YAML filename prints and the command exits zero.

### Task 3: Add License and Automated Quality Checks

**Files:**
- Create: `LICENSE`
- Create: `.github/workflows/awesome-lint.yml`
- Create: `.github/workflows/links.yml`

**Interfaces:**
- Consumes: Repository Markdown and URLs from Tasks 1 and 2.
- Produces: Automated formatting and link-health results on pull requests and a weekly schedule.

- [ ] **Step 1: Add the CC0 1.0 legal text**

Use the canonical Creative Commons CC0 1.0 Universal text in `LICENSE`.

- [ ] **Step 2: Add Awesome linting**

Create a least-privilege workflow that checks out the repository and runs `awesome-lint` on pushes and pull requests.

- [ ] **Step 3: Add link checking**

Create a least-privilege Lychee workflow for Markdown files on pull requests, pushes, manual dispatch, and a weekly schedule. Configure it to retry transient failures and upload no artifacts.

- [ ] **Step 4: Run local lint and link checks**

Run:

```bash
npx --yes awesome-lint
npx --yes lychee README.md CONTRIBUTING.md CODE_OF_CONDUCT.md
```

Expected: both commands exit zero, except explicitly documented anti-bot link failures that are rechecked manually.

### Task 4: Verify the Complete Repository

**Files:**
- Inspect: all changed files

**Interfaces:**
- Consumes: Deliverables from Tasks 1 through 3.
- Produces: Evidence that the repository meets the design and contains no accidental unrelated edits.

- [ ] **Step 1: Inspect repository state**

Run:

```bash
git status --short
git diff --check
git diff --stat
```

Expected: only planned files are changed, whitespace validation exits zero, and the stat matches the planned repository surface.

- [ ] **Step 2: Re-run all validation**

Run the YAML parser, `awesome-lint`, Lychee, duplicate checks, and excluded-name checks in one fresh verification pass.

- [ ] **Step 3: Review the rendered Markdown source**

Read the complete README and contribution guide for broken hierarchy, inconsistent labels, promotional wording, and unsupported claims.
