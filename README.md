# cherry-pick-release-strategy

This repository contains a simple example of how to use the cherry-pick release strategy.

## Create a new feature branch and make changes

```bash
git checkout -b DATA-1234-my-feature develop # develop should be the base branch
```

## Pull request the feature branch to the develop branch
The workflows file `.github/workflows/feature.yaml` is triggered when a PR is created to the develop branch.

## Complete the feature pull request
Once the PR is approved and merged, the feature branch can be deleted.
Merge strategy: squash and merge.
The workflow file `.github/workflows/develop.yaml` is triggered when the develop branch is updated and deploys the changes to the develop environment.

## Create a release branch and cherry-pick the develop branch
```bash
git checkout -b release/1.0 main # main should be the base branch
git cherry-pick 192274f23abf0aeaadab4bd6b1981c4bec1935f8 # a commit from the develop branch
...
```

## Pull request the release branch to the main branch
The workflows file `.github/workflows/release.yaml` is triggered when a PR is created to the main branch.
This releases the changes to the acceptance environment.
The workflow file `.github/workflows/main.yaml` is triggered when the main branch is updated and deploys the changes to the production environment.

## Update the develop branch with the main branch
The develop branch should be updated with the changes from the main branch, so that released features are synchronized with the develop branch and un-released features are available for the next release.

```bash
git checkout develop
git rebase --reapply-cherry-picks --strategy-option=ours main
git push --force
```