# LLMOS Charts
[![Release Charts](https://github.com/llmos-ai/charts/actions/workflows/ci.yaml/badge.svg)](https://github.com/llmos-ai/charts/actions/workflows/ci.yaml)

## Prerequisites
- Helm 3.x

## Adding the Chart
```
$ helm repo add llmos-charts https://llmos-charts.1block.ai
$ helm repo update
```

## Releasing New Charts
When ready to release a new chart version or add a new chart, copy the chart directory from the source repository into the `charts/` directory. Make sure the chart directory is named after the actual chart (for example: `kube-/`).

Once pushed, GitHub Actions will look for any changes to charts in the `charts/` directory since the last tagged release in the repository, package any changed charts, and then release them on `GitHub Pages`.

Note that changes should only be synced to this repository when ready for a new release. GitHub Actions will fail if making changes to the charts in this repository directly, as Chart Releaser will not attempt to override old chart releases.

## Branch Usage:
- `master` branch is used for latest manifests
- `release` branch is used for the latest version. It should be mostly in sync with the `master` and the latest stable branch. Only the chart version should be different.
- `release-<version>` branch is used for the previous versions.

We will create a `release-<version>` after we release a new version of Harvester. The `release` branch can keep going with the latest version.

### Releasing New Charts

To release a new chart version or add a new chart:
1. Copy the chart directory from the source repository into the charts/ directory.
    - Ensure the chart directory name matches the chart (e.g., `kube-prometheus-stack`).
2. Push your changes with a new PR and include the chart name in the PR title (e.g., `[kube-prometheus-stack] $your-commit-message`).

Once changes are pushed, GitHub Actions will:

#### For the `main` branch
- Detect updates to charts in the `charts/` directory since the last commit in the upstream branch.

#### For the `Realase` branch
- Package the modified charts.
- Publish them on GitHub Pages.

### Branch Usage
- **main branch**: Contains the latest manifests.
- **release branch**: Holds the latest stable version. This branch should align closely with master but may differ in the chart version.

### Important:
- Sync changes to the `release` branch only when ready for a new release.
- Avoid direct modifications to the charts in this repository. GitHub Actions will fail if old chart releases are overwritten, as Chart Releaser does not support overriding existing releases.
