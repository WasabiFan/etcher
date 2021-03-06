Maintaining Etcher
==================

This document is meant to serve as a guide for maintainers to perform common
tasks.

Preparing a new version
-----------------------

- Bump the version number in the `package.json`'s `version` property.

- Bump the version number in the `package.json`'s `builder.win.version`
property.

- Add a new entry to `CHANGELOG.md` describing what has been added, changed, or
removed. Please use the imperative mode and capitalize the first letter of
each item.

- Link the `CHANGELOG.md` entry to the GitHub page displaying the diffs between
the previous and the current version.

```markdown
https://github.com/resin-io/etcher/compare/<previous>...<current>
```

- Re-take `screenshot.png` so it displays the latest version in the bottom
right corner.

- Re-install all dependencies and run `npm shrinkwrap` to update
`npm-shrinkwrap.json`.

- Commit the changes with the version number as the commit title, including the
`v` prefix, to `master`. For example:

```sh
git commit -m "v1.0.0" # not 1.0.0
```

- Create an annotated tag for the new version. The commit title should equal
the annotated tag name. For example:

```sh
git tag -a v1.0.0 -m "v1.0.0"
```

- Push the commit and the annotated tag.

```sh
git push
git push --tags
```

Upgrading Electron
------------------

- Upgrade the `electron-prebuilt` dependency version in `package.json` to an
*exact version* (no `~`, `^`, etc).

- Find the exact NodeJS version included in the desired Electron version and
update `engines.node` in `package.json` appropriately. This can be usually
found in the [Electron releases page][electron-releases].

- Update the `NODE_VERSION` environment variable in `.travis.yml`.

- Update the `nodejs_version` environment variable in `appveyor.yml`.

[electron-releases]: https://github.com/electron/electron/releases
