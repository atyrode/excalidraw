# Fork documentation

## 🔁 Dev Flow

### `master` is a mirror of upstream:

```bash
git checkout master
git fetch upstream
git merge upstream/master
git push origin master
```

### `pad.ws` contains all customizations, rebased on `master`:

```bash
git checkout pad.ws
git fetch upstream
git checkout master
git merge upstream/master
git push origin master

git checkout pad.ws
git rebase master
```

# 🌿 Feature Development

All new work should go into feature branches that target `pad.ws`. Example:

```bash
# create a new feature
git checkout pad.ws
git checkout -b feat-better-selection-tool

# do work...

git commit -am "feat: improve selection behavior when dragging"

# merge into pad.ws
git checkout pad.ws
git merge feat-better-selection-tool
git push origin pad.ws
```

Alternatively, squash or rebase before merging if preferred:
```bash
git rebase -i pad.ws
```

## 🏷️ Versioning

The version of this package (in `/packages/excalidraw/package.json`) follows the same scheme as [zsviczian/excalidraw](https://github.com/zsviczian/excalidraw):

> It uses the same semantic version as the original Excalidraw codebase, with an additional `-x` suffix to indicate the internal fork version.

For example:
```
0.18.0-5
```
Means the 5th "sub-release" of the fork based on Excalidraw `0.18.0`.

This fork will periodically fetch and merge changes from the upstream repo:  
👉 https://github.com/excalidraw/excalidraw

## 📦 Publishing

```bash
cd packages/excalidraw
yarn install
yarn build:esm
npm login
npm publish --access public
```

This will publish the package under `@atyrode/excalidraw`.
