# Snyk PR Closure Comment Templates

Use these templates when closing the Snyk PRs identified in `SNYK_PR_CLOSURE_GUIDE.md`.

## For nginx upgrade PRs (#83-85, #88-93)

```
Closing this PR as it has been superseded by #101 (Consolidated Snyk security upgrades).

The repository now uses nginx version 1.29.3/1.29.3-alpine, which is newer than the version proposed in this PR.

See SNYK_PR_CLOSURE_GUIDE.md for complete details.
```

## For bootstrap upgrade PR (#86)

```
Closing this PR as the upgrade has already been applied.

Bootstrap 5.3.5 is already in use in the repository (see NginxUI/app/package.json).

This was part of the consolidated upgrades in PR #101.

See SNYK_PR_CLOSURE_GUIDE.md for complete details.
```

## For @angular/localize PR (#87)

```
Closing this PR as it is based on outdated information and is incompatible with the current codebase.

The current version of @angular/localize is ~11.2.7, not 19.1.2 as this PR assumes. 

Upgrading to version 20.0.0 would require a major Angular framework upgrade from version ~11.2.7 to ~20.x, which is beyond the scope of a simple dependency update. This would require:
- Upgrading all Angular dependencies
- Significant code changes to handle breaking changes
- Comprehensive testing

If a major Angular upgrade is desired, please create a separate issue to plan and track this work.

See SNYK_PR_CLOSURE_GUIDE.md for complete details.
```

## Quick Reference

| PR # | Template to Use |
|------|----------------|
| #83-85, #88-93 | nginx upgrade template |
| #86 | bootstrap upgrade template |
| #87 | @angular/localize template |
