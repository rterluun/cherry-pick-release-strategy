# cherry-pick-release-strategy

This repository contains a simple example of how to use the cherry-pick release strategy.

## Create a new feature branch

```bash
git checkout -b DATA-1234-my-feature # develop should be the base branch
```

## Make some changes

```bash
echo "Hello, World!" > hello.txt
git add hello.txt
git commit -m "DATA-1234: Add hello.txt"
```

## Trigger a build when a PR is created to the develop branch

```bash
git push origin DATA-1234-my-feature
```
