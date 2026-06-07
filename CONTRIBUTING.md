# Contributing to Socipoki

Thank you for your interest in contributing! This document explains how to set up the project locally, the conventions we follow, and the process for getting your changes merged.

---

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Workflow](#development-workflow)
- [Coding Conventions](#coding-conventions)
- [Commit Message Format](#commit-message-format)
- [Submitting a Pull Request](#submitting-a-pull-request)
- [Reporting Bugs](#reporting-bugs)
- [Requesting Features](#requesting-features)

---

## Code of Conduct

By participating in this project, you agree to abide by the [Code of Conduct](CODE_OF_CONDUCT.md). Please read it before contributing.

---

## Getting Started

### 1. Fork and clone

```bash
# Fork the repo on GitHub, then:
git clone https://github.com/<your-username>/SocialMediaApp.git
cd SocialMediaApp
```

### 2. Set up the development environment

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Configure environment variables

```bash
cp .env.example .env
# Edit .env — at minimum set SECRET_KEY and DEBUG=True
```

### 4. Run migrations and start the server

```bash
python manage.py migrate
python manage.py createsuperuser  # optional
python manage.py runserver
```

The app runs at [http://127.0.0.1:8000](http://127.0.0.1:8000).

---

## Development Workflow

1. Sync your fork with the upstream `master` branch before starting new work:
   ```bash
   git fetch upstream
   git checkout master
   git merge upstream/master
   ```

2. Create a branch with a descriptive name:
   ```bash
   git checkout -b feat/infinite-scroll
   git checkout -b fix/follow-self-bug
   git checkout -b docs/update-readme
   ```

3. Make your changes, then run a quick sanity check:
   ```bash
   python manage.py check
   python manage.py test
   ```

4. Commit and push your branch, then open a Pull Request.

---

## Coding Conventions

- Follow [PEP 8](https://peps.python.org/pep-0008/) for Python code style.
- Use meaningful variable and function names — avoid single-letter names outside of loops.
- Keep views thin; push business logic into model methods or service functions.
- Do not commit `db.sqlite3`, `.env`, or files under `media/`.
- Templates go in the relevant app's `templates/` folder or `layouts/` for shared partials.
- Static assets (CSS, JS, images) belong in `static/`.
- Add migrations for every model change:
  ```bash
  python manage.py makemigrations
  ```

---

## Commit Message Format

We use the [Conventional Commits](https://www.conventionalcommits.org/) specification:

```
<type>: <short summary in present tense>
```

**Types:**

| Type | When to use |
|---|---|
| `feat` | A new feature |
| `fix` | A bug fix |
| `docs` | Documentation changes only |
| `style` | Formatting, whitespace (no logic change) |
| `refactor` | Code restructuring without feature or bug change |
| `test` | Adding or updating tests |
| `chore` | Dependency updates, build tasks |

**Examples:**

```
feat: add pagination to explore page
fix: prevent users from following themselves
docs: update environment variable table in README
refactor: extract image resizing into post model method
```

Keep the summary under 72 characters and write in the imperative mood ("add", not "added").

---

## Submitting a Pull Request

1. Ensure your branch is up to date with `master`.
2. Fill out the pull request template completely.
3. Link any related issues with `Closes #<issue-number>`.
4. Keep PRs focused — one feature or fix per PR.
5. Add or update tests when your change affects app logic.
6. Request a review from the maintainer [@ofcskn](https://github.com/ofcskn).

A PR will be merged once it passes review and any CI checks.

---

## Reporting Bugs

Open an issue using the [Bug Report template](.github/ISSUE_TEMPLATE/bug_report.md). Include:

- Steps to reproduce
- Expected vs. actual behavior
- Django/Python version and OS
- Relevant logs or screenshots

---

## Requesting Features

Open an issue using the [Feature Request template](.github/ISSUE_TEMPLATE/feature_request.md). Check the [Roadmap](README.md#roadmap) first to see if the feature is already planned.

---

Thank you for helping make Socipoki better!
