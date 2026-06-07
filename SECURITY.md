# Security Policy

## Supported Versions

| Version | Supported |
|---------|-----------|
| latest (`master`) | Yes |
| older commits | No |

Only the latest commit on `master` receives security fixes.

## Reporting a Vulnerability

**Please do not open a public GitHub issue for security vulnerabilities.**

Report vulnerabilities privately by emailing **omer@chainabit.com** with the subject line:

```
[SECURITY] <brief description>
```

Include in your report:

- A description of the vulnerability and its potential impact
- Steps to reproduce or a proof-of-concept
- Affected component (e.g., authentication, file upload, comment system)
- Any suggested remediation if you have one

## What to Expect

- **Acknowledgement** within 48 hours
- **Status update** within 7 days (confirmed, rejected, or needs more info)
- **Fix timeline** communicated once the issue is confirmed
- **Credit** in the changelog if you wish, after the fix is released

## Known Security Considerations

The following are known areas that contributors and deployers should be aware of:

- **Media uploads:** User-uploaded images are processed with Pillow. Only image content types are accepted.
- **SECRET_KEY:** Must be set to a strong, unique value in production. Never use the development default.
- **DEBUG mode:** Must be `False` in production. Leaving it `True` exposes stack traces.
- **ALLOWED_HOSTS:** Must be set explicitly in production to prevent HTTP Host header attacks.
- **CSRF:** Django's built-in CSRF protection is enabled on all forms.
- **SQL injection:** Django's ORM is used throughout; raw queries are avoided.

## Deployment Hardening Checklist

Before deploying to production:

- [ ] `DEBUG=False`
- [ ] `SECRET_KEY` is a unique, randomly generated value
- [ ] `ALLOWED_HOSTS` lists only your domain(s)
- [ ] `DATABASE_URL` points to a managed PostgreSQL instance (not SQLite)
- [ ] Static files served via WhiteNoise or a CDN (not Django dev server)
- [ ] HTTPS enforced at the reverse proxy or platform level
- [ ] `media/` directory is not publicly writable beyond what Django controls
