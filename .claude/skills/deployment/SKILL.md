---
name: deployment
description: Manages build, release, and deployment — version bumping, changelog, release builds, distribution channel uploads, and staged rollout. Manual approval required for production deployments.
disable-model-invocation: true
---

# Deployment & Release

Manages build pipeline and release process.

## Usage
`/deployment prepare <version>` — Prepare a release
`/deployment build <target>` — Build for target platform
`/deployment check` — Pre-release checklist

## Pre-Release Checklist

### Quality Gates (ALL must pass)
- [ ] All tests passing
- [ ] Code coverage >= 80%
- [ ] No linter/analyzer warnings
- [ ] Security audit passed
- [ ] Performance targets met
- [ ] Accessibility audit passed
- [ ] Version bumped
- [ ] Changelog updated
- [ ] No debug flags in release config
- [ ] API keys use production values
- [ ] Code signing configured (if applicable)

## Version Bump
1. Update version in project config (semver: MAJOR.MINOR.PATCH)
2. Update `CHANGELOG.md` with release notes
3. Create git tag: `git tag v{version}`

## Build Commands

Customize for your platform:

### Web
```bash
npm run build  # or: yarn build, pnpm build
```

### Mobile (Flutter)
```bash
flutter build appbundle --release  # Android
flutter build ipa --release        # iOS
```

### Backend
```bash
docker build -t app:version .
# or: go build, cargo build --release, etc.
```

## Release Flow
1. Version bump -> Changelog -> Tag
2. CI builds release artifacts
3. Upload to distribution channel (npm, PyPI, App Store, Play Store, Docker Hub, etc.)
4. QA verification
5. Staged rollout (if applicable): 10% -> 25% -> 50% -> 100% over 7 days

## Post-Release
- Monitor error tracking and crash reports
- Watch user feedback channels for first 48 hours
- Keep previous version available for emergency rollback
