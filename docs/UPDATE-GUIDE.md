# Terminal update guide

Requirements: Git, GitHub CLI (`gh`), `unzip`, `rsync`; a GitHub login allowed to push to `savaskarofficial/OsiNet`. Commands assume Linux/macOS/Git Bash with these utilities. Run from the directory containing the downloaded ZIP. Do not overwrite your existing working checkout: this procedure creates a fresh clone and preserves remote history.

## 1. Extract and authenticate

```bash
unzip OsiNet-GitHub-Updated.zip
gh auth status
# Only if authentication is needed:
gh auth login
gh auth setup-git
```

## 2. Clone and apply documentation

```bash
git clone https://github.com/savaskarofficial/OsiNet.git OsiNet-publish
rsync -av OsiNet-GitHub-Updated/repository/ OsiNet-publish/
cd OsiNet-publish
git status --short
git diff --check
git diff --stat
git add README.md CHANGELOG.md SECURITY.md .gitignore .github docs app-icon.png screenshots
git diff --cached --stat
git commit -m "docs: reconcile OsiNet APK 1.0.7 and refresh release documentation"
git push origin HEAD
```

Review the staged file list before committing. It should contain only docs, issue templates, icon/screenshots and ignore rules. No APK, application source, credentials or signing keys should be staged. The APK stays in the sibling `release-assets/` directory. If branch protection rejects direct pushes, push a new branch and open a PR instead; do not force push.

```bash
# Alternative when direct pushes are not permitted:
git switch -c docs/osinet-apk-1.0.7
git push -u origin docs/osinet-apk-1.0.7
gh pr create --repo savaskarofficial/OsiNet --title "Refresh OsiNet release documentation" --body "Reconcile APK metadata, update feature/changelog documentation and move binary distribution to Releases. No app source or keys included."
```

## 3. Verify the APK and publish a release

Run after the documentation commit is on the default branch (after merging the PR if required). From `OsiNet-publish/`:

```bash
(cd ../OsiNet-GitHub-Updated/release-assets && sha256sum -c SHA256SUMS.txt)
gh release create apk-v1.0.7 \
  ../OsiNet-GitHub-Updated/release-assets/OsiNet-1.0.7-debug.apk \
  ../OsiNet-GitHub-Updated/release-assets/SHA256SUMS.txt \
  --repo savaskarofficial/OsiNet \
  --target "$(gh api repos/savaskarofficial/OsiNet/commits/HEAD --jq .sha)" \
  --title "OsiNet 1.0.7 — readable case reports (testing)" \
  --notes-file docs/RELEASE-v1.0.7.md \
  --prerelease
gh release view apk-v1.0.7 --repo savaskarofficial/OsiNet --web
```

macOS without `sha256sum`: run `shasum -a 256 -c SHA256SUMS.txt` from the asset directory instead. A checksum mismatch means stop before uploading.

The existing `v1.1.0` tag is not deleted or repointed. The APK is not renamed to suggest a newer version. The dedicated tag is deliberate; the prerelease does not replace GitHub’s stable Latest release.

## If apk-v1.0.7 already exists

Inspect it before updating. The following commands intentionally replace same-named assets and release notes; they do not move its tag:

```bash
gh release view apk-v1.0.7 --repo savaskarofficial/OsiNet
gh release upload apk-v1.0.7 \
  ../OsiNet-GitHub-Updated/release-assets/OsiNet-1.0.7-debug.apk \
  ../OsiNet-GitHub-Updated/release-assets/SHA256SUMS.txt \
  --repo savaskarofficial/OsiNet --clobber
gh release edit apk-v1.0.7 --repo savaskarofficial/OsiNet \
  --title "OsiNet 1.0.7 — readable case reports (testing)" \
  --notes-file docs/RELEASE-v1.0.7.md --prerelease
```

## What changed / what you should publish

Commit README, CHANGELOG, SECURITY, `.gitignore`, `.github/ISSUE_TEMPLATE/` and `docs/`. Existing screenshot/icon/license/funding files are included for a complete repository. Publish only the APK and SHA256SUMS as release attachments. Do not upload the entire delivery ZIP to the repository or include app source, private keys, old `.git` files or personal case exports.

For a future production release, build/sign the private app project, increment its actual versionCode/versionName, verify the artifact, and update the metadata, checksum, release notes and download links together. Documentation cannot change the version embedded in an APK.
