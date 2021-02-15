# NodeJS

List global top level NodeJS packages: `npm list -g --depth 0`

### Yarn

[Selective dependency resolution](https://classic.yarnpkg.com/en/docs/selective-version-resolutions#search), aka, force a package to use a specific version of a dependency.

In your package.json file to rewrite the usage of left-pad in the d2 library you're importing:

```text
  "resolutions": {
    "d2/left-pad": "1.1.1",
    "**/left-pad": "^1.1.2"
  }
```

`**` act as a wildcard if you'd like to change more than one parent library.

