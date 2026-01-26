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
Closing this PR as it is based on incorrect version information and would exacerbate existing Angular version inconsistencies.

The repository currently has an inconsistent Angular version state:
- @angular/compiler and @angular/core are at ~19.2.18
- @angular/localize and most other Angular packages are at ~11.2.7
- This indicates a partial/incomplete Angular upgrade

This PR proposes upgrading @angular/localize from 19.1.2 to 20.0.0, but:
- The current version is actually ~11.2.7, not 19.1.2
- The PR is based on incorrect version information
- Applying this would create further version mismatches

A comprehensive Angular upgrade is needed to resolve the existing version inconsistencies and bring all packages to a consistent version.

I will create a separate issue to track the Angular version inconsistency problem.

See SNYK_PR_CLOSURE_GUIDE.md for complete details.
```

## Quick Reference

| PR # | Template to Use |
|------|----------------|
| #83-85, #88-93 | nginx upgrade template |
| #86 | bootstrap upgrade template |
| #87 | @angular/localize template |
