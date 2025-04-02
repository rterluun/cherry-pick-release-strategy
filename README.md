# cherry-pick-release-strategy

This repository contains a simple example of how to use the cherry-pick release strategy.

## Create a new feature branch

```bash
git checkout -b DATA-1234-my-feature # develop should be the base branch
```

## Trigger a build when a PR is created to the develop branch

The workflows file `.github/workflows/feature.yaml` is triggered when a PR is created to the develop branch.
Or the workflow can be triggered manually, to verify the deployment of your change on the cloud environment.

## Merge the feature branch to the develop branch

The feature branch is merged to the develop branch using a PR.

## Cherry-pick the develop branch to the release branch

```bash
git checkout -b release/1.0 # main should be the base branch
git cherry-pick <commit-hash>
```

