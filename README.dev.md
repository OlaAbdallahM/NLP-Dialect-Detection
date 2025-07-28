# 🧩 Development Workflow – Git Commit Enforcement

This document describes how to enforce consistent and meaningful Git commit messages using **Gitlint** and **pre-commit**. It follows the [Conventional Commits](https://www.conventionalcommits.org/) format to improve clarity, collaboration, and automation.

---

## 🔧 Setup Instructions

### 1\. Install Dependencies

Make sure you have Python and Git installed. Then install the required tools:

```bash
pip install pre-commit gitlint
```

---

### 2\. Add Gitlint to Pre-commit Configuration

Create a file named `.pre-commit-config.yaml` in the root of your project with the following content:

```yaml
repos:
  - repo: https://github.com/jorisroovers/gitlint
    rev: v0.19.1
    hooks:
      - id: gitlint
        stages: \[commit-msg]
```

---

### 3\. Install the Pre-commit Hook

Run this to activate the `commit-msg` hook:

```bash
pre-commit install --hook-type commit-msg
```

---

### 4\. Create a `.gitlint` Configuration File

Create a `.gitlint` file in your project root with the following content:

```ini
\[general]
ignore=body-is-missing

\[title-match-regex]
regex=^(feat|fix|chore|docs|refactor|test|ci)\\: .+$
```

---

## ✅ Valid Commit Examples

```bash
feat: add language detection API
fix: resolve crash on empty input
docs: update README installation section
refactor: clean up preprocessing logic
```

---

## 🚫 Invalid Commit Examples (Will Be Rejected)

```bash
update
test hocks
fix
bad message
testing commit
```