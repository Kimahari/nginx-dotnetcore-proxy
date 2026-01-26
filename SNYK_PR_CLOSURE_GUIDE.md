# Snyk Pull Request Closure Guide

## Overview
This document provides a comprehensive analysis of open Snyk security and upgrade pull requests that are no longer required because their changes have been superseded by PR #101 (Consolidated Snyk security upgrades), which was merged on January 26, 2026.

## Current Repository Versions (as of PR #101 merge)

### Nginx Versions
- **nginx**: 1.29.3 (in `NginxUI/nginx.d/Dockerfile`)
- **nginx-alpine**: 1.29.3-alpine (in `NginxUI/Dockerfile`)

### Node Package Versions
- **bootstrap**: 5.3.5 (in `NginxUI/app/package.json`)
- **tslib**: 2.8.1 (in `NginxUI/app/package.json`)
- **Angular packages**: Mixed versions (inconsistent state)
  - `@angular/compiler`: ~19.2.18
  - `@angular/core`: ~19.2.18
  - `@angular/localize`: ~11.2.7
  - Other Angular packages: ~11.2.7
  - **Note**: This version inconsistency indicates an incomplete Angular upgrade

## Pull Requests to Close

### Superseded nginx Upgrades (9 PRs)
The following PRs upgrade nginx to versions **older than or equal to** the current version (1.29.3):

| PR # | Title | Target Version | Status |
|------|-------|----------------|--------|
| #93 | [Snyk] Security upgrade nginx from 1.26.2 to 1.29.2 | 1.29.2 | Superseded by 1.29.3 |
| #92 | [Snyk] Security upgrade nginx from 1.27.4-alpine to 1.29.2-alpine | 1.29.2-alpine | Superseded by 1.29.3-alpine |
| #91 | [Snyk] Security upgrade nginx from 1.26.2 to 1.29.1 | 1.29.1 | Superseded by 1.29.3 |
| #90 | [Snyk] Security upgrade nginx from 1.27.4-alpine to 1.29.1-alpine | 1.29.1-alpine | Superseded by 1.29.3-alpine |
| #89 | [Snyk] Security upgrade nginx from 1.27.4-alpine to 1.29.0-alpine | 1.29.0-alpine | Superseded by 1.29.3-alpine |
| #88 | [Snyk] Security upgrade nginx from 1.26.2 to 1.29.0 | 1.29.0 | Superseded by 1.29.3 |
| #85 | [Snyk] Security upgrade nginx from 1.26.2 to 1.28.0 | 1.28.0 | Superseded by 1.29.3 |
| #84 | [Snyk] Security upgrade nginx from 1.27.4-alpine to 1.28.0-alpine | 1.28.0-alpine | Superseded by 1.29.3-alpine |
| #83 | [Snyk] Security upgrade nginx from 1.26.2 to 1.27.5 | 1.27.5 | Superseded by 1.29.3 |

**Rationale**: All these PRs propose upgrading nginx to versions that are older than the current version (1.29.3/1.29.3-alpine) already in the repository. These upgrades were consolidated and applied in PR #101.

### Superseded Package Upgrades (1 PR)

| PR # | Title | Target Version | Status |
|------|-------|----------------|--------|
| #86 | [Snyk] Upgrade bootstrap from 5.3.3 to 5.3.5 | 5.3.5 | Already applied |

**Rationale**: Bootstrap 5.3.5 is already installed in the repository (as seen in `NginxUI/app/package.json`).

## Pull Requests to Keep Open

### PR #87: [Snyk] Security upgrade @angular/localize from 19.1.2 to 20.0.0

**Status**: Should remain open but requires careful consideration

**Rationale**: 
- The repository currently has an **inconsistent Angular version state**:
  - `@angular/compiler` and `@angular/core` are at ~19.2.18
  - `@angular/localize` and most other Angular packages are at ~11.2.7
  - This indicates a partial/incomplete Angular upgrade
- This PR proposes upgrading `@angular/localize` from 19.1.2 to 20.0.0, but:
  - The current version is actually ~11.2.7, not 19.1.2
  - The PR is based on incorrect version information
  - This would create further version mismatches
- The repository needs a comprehensive Angular upgrade to resolve version inconsistencies

**Recommendation**: 
1. Close this PR as it's based on incorrect version information
2. Create a new issue to address the Angular version inconsistency problem
3. Plan a comprehensive Angular upgrade to bring all packages to a consistent version

## Instructions for Repository Maintainers

### To Close These Pull Requests:

1. Navigate to each PR listed in the "Pull Requests to Close" section
2. Add a comment explaining why it's being closed, for example:
   ```
   Closing this PR as it has been superseded by #101 (Consolidated Snyk security upgrades), 
   which upgraded nginx to version 1.29.3/1.29.3-alpine. This is newer than the version 
   proposed in this PR.
   ```
3. Close the PR without merging

### Verification Steps:

Before closing, you can verify the current versions:

```bash
# Check nginx versions in Dockerfiles
grep "FROM nginx:" NginxUI/nginx.d/Dockerfile NginxUI/Dockerfile

# Check package versions
grep -E "(bootstrap|tslib|@angular)" NginxUI/app/package.json
```

Expected output:
- nginx: 1.29.3
- nginx-alpine: 1.29.3-alpine
- bootstrap: ^5.3.5
- tslib: ^2.8.1

## Summary

**Total PRs to close**: 10
- 9 nginx upgrade PRs (superseded by newer version)
- 1 bootstrap upgrade PR (already applied)

**Total PRs requiring review**: 1
- PR #87 (@angular/localize) - Recommend closing due to incompatibility with current Angular version

All security updates from these PRs have been addressed by PR #101, which consolidated multiple Snyk upgrades into a single, comprehensive update.
