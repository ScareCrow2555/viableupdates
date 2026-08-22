# Viable Updates

Public release metadata and encrypted update assets for Viable Food applications.

## Purpose

This repository is a multi-application release hub. Application source code can remain private while deployed applications check public version manifests and download encrypted GitHub Release assets.

## Layout

```text
apps/
  job-board/
    latest.json
    releases/
      <version>.json
  news/
    README.md
```

Each application owns a stable `latest.json` plus immutable version manifests under `releases/`. Binary update packages are published as GitHub Release assets rather than committed to Git history.

## Security model

- Release manifests and notes are public.
- Private application source is not committed here.
- Update assets for private applications are authenticated and encrypted before publication.
- Decryption keys are never stored in this repository, release manifests, release notes, or assets.
- Applications verify the encrypted asset checksum, authenticated encryption, decrypted ZIP checksum, and ZIP paths before installation.
- A manifest marked `manual_required` must not be installed automatically.

## Applications

### Job Board

Application ID: `job-board`

Manifest: `apps/job-board/latest.json`

The baseline `1.1.0` manifest establishes version tracking while the browser updater is bootstrapped manually. It is intentionally marked `manual_required` and its placeholder release hashes are not an installable package. The first later automatic release will replace `latest.json` only after its encrypted GitHub Release asset is successfully published.

### News

Reserved for a future Viable Food news application update channel.
