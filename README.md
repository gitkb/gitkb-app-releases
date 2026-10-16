# GitKB App Releases

Public release packages for first-party GitKB apps. GitKB Desktop installs and updates apps from here, so no GitHub account or token is needed.

| App | Package | Tags |
|-----|---------|------|
| ATC | `gitkb-app-atc.gitkbapp` | `gitkb-app-atc-vX.Y.Z` |

Each release carries the package and its `.sha256`. Apps share this repository, so a release tag always starts with the app's name; there is no single "latest" release.

## How releases get here

An app's release workflow publishes to its own repository, then sends an `app-release-created` dispatch with the app name and tag. The **Mirror App Release** workflow downloads that package, checks its SHA-256, publishes it here under the same tag, and fails unless the published assets are byte-identical to the app's release.

To add an app: add its name to `APPS` in `.github/workflows/mirror-app-release.yml`, and add the dispatch step to the app's publish workflow.
