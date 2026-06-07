# Release Process

This document describes how to tag and publish a new release of Socipoki.

---

## Versioning

Socipoki uses [Semantic Versioning](https://semver.org/):

```
MAJOR.MINOR.PATCH
```

| Increment | When |
|-----------|------|
| `MAJOR` | Breaking changes or major rewrites |
| `MINOR` | New backward-compatible features |
| `PATCH` | Bug fixes and small improvements |

---

## Release Steps

### 1. Update CHANGELOG.md

Move items from `[Unreleased]` into a new versioned section:

```markdown
## [1.0.0] — YYYY-MM-DD

### Added
- ...

### Fixed
- ...
```

### 2. Bump the version (if tracked)

If a `VERSION` file or `__version__` variable exists, update it now.

### 3. Commit the release

```bash
git add CHANGELOG.md
git commit -m "chore: release v1.0.0"
```

### 4. Tag the release

```bash
git tag -a v1.0.0 -m "Release v1.0.0"
git push origin master --tags
```

### 5. Create a GitHub Release

1. Go to the repository on GitHub
2. Click **Releases** → **Draft a new release**
3. Select the tag you just pushed (`v1.0.0`)
4. Set the title to `v1.0.0`
5. Paste the relevant CHANGELOG section into the description
6. Publish the release

### 6. Deploy to Heroku (if applicable)

```bash
git push heroku master
heroku run python manage.py migrate --app <your-app-name>
```

---

## Hotfix Process

For urgent production fixes:

```bash
git checkout master
git checkout -b fix/critical-issue
# make the fix
git commit -m "fix: resolve critical issue"
git checkout master
git merge fix/critical-issue
git tag -a v0.1.1 -m "Hotfix v0.1.1"
git push origin master --tags
```

---

## Pre-Release Checklist

- [ ] All tests pass: `python manage.py test`
- [ ] No Django system check warnings: `python manage.py check --deploy`
- [ ] `DEBUG=False` in production environment
- [ ] `SECRET_KEY` is unique and not the development default
- [ ] `ALLOWED_HOSTS` set correctly
- [ ] Migrations applied: `python manage.py migrate`
- [ ] Static files collected: `python manage.py collectstatic --noinput`
- [ ] CHANGELOG.md updated
- [ ] Git tag created and pushed
- [ ] GitHub Release published
