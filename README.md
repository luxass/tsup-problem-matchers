# tsup-problem-matchers

[![vsmarketplace-installs][vsmarketplace-installs-src]][vsmarketplace-installs-href]

Inspired by [esbuild-problem-matchers](https://github.com/connor4312/esbuild-problem-matchers)

## Builtin Problem Matchers

- `$tsup` - Matches errors and warnings from `tsup --format esm,cjs` output
- `$tsup-watch` - Matches errors and warnings from `tsup --format esm,cjs --watch` output
- `$tsup-esm` - Matches errors and warnings from `tsup --format esm` output
- `$tsup-esm-watch` - Matches errors and warnings from `tsup --format esm --watch` output
- `$tsup-cjs` - Matches errors and warnings from `tsup --format cjs` output
- `$tsup-cjs-watch` - Matches errors and warnings from `tsup --format cjs --watch` output
- `$tsup-dts` - Matches errors and warnings from `tsup --dts` output
- `$tsup-dts-watch` - Matches errors and warnings from `tsup --dts --watch` output

## 📚 Usage

To use this, add the `tsup` or `tsup-watch` problem matcher to your tasks.json, as appropriate. For example:

```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "type": "npm",
      "script": "watch",
      "group": "build",
      "problemMatcher": ["$tsup-watch", "$tsup-dts-watch"],
      "isBackground": true,
      "label": "npm: watch"
    },
    {
      "type": "npm",
      "script": "build",
      "group": "build",
      "problemMatcher": ["$tsup", "$tsup-dts"],
      "label": "npm: build"
    }
  ]
}
```

<br/>
<br/>
<br/>


> [!NOTE]  
> If you are using [`Turborepo`](https://turbo.build/repo), you can use the following configuration

```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "type": "npm",
      "script": "watch",
      "group": "build",
      "problemMatcher": [
        {
          "base": "$tsup-watch",
          "background": {
            "beginsPattern": "^your-pkg-name:(.*): (ESM|CJS) Build start$",
            "endsPattern": "^your-pkg-name:(.*): (ESM|CJS) .* Build success|^your-pkg-name:(.*): (ESM|CJS) Build failed"
          }
        },
        {
          "base": "$tsup-dts-watch",
          "background": {
            "beginsPattern": "^your-pkg-name:(.*): DTS Build start$",
            "endsPattern": "^your-pkg-name:(.*): DTS .* Build success|^your-pkg-name:(.*): DTS Build failed"
          }
        }
      ],
      "isBackground": true,
      "label": "npm: watch"
    }
  ]
}
```

<!-- Badges -->

[vsmarketplace-installs-src]: https://img.shields.io/visual-studio-marketplace/i/luxass.tsup-problem-matchers?style=flat&colorA=18181B&colorB=4169E1
[vsmarketplace-installs-href]: https://marketplace.visualstudio.com/items?itemName=luxass.tsup-problem-matchers

## 📄 License

Published under [MIT License](./LICENSE).
