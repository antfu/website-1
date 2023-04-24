```yaml
title: Exporting Icon Packages
types:
  IconSet: '../icon-set/index.md'
```

# Exporting icon set as icon package

This tutorial is part of [export functions documentation](./index.md) in [Iconify Tools](../index.md).

Function `[func]exportIconPackage()` creates icon package in specified directory.

These packages are used in offline icon components, like this:

```yaml
src: icon-components/common/offline.jsx
```

`[npm]@iconify-icons/bi` is a package generated by this function, used in example above.

See [split icon packages documentation](../../../icons/icons.md) for details.

## Usage

Function has the following parameters:

- `[prop]iconSet`, `[type]IconSet`. Icon set to export.
- `[prop]options`, `[type]object`. Options. See below.

Function returns array of generated files.

Function is asynchronous. That means you need to handle it as `[class]Promise` instance, usually by adding `[js]await` before function call.

### Options

Options object has the following mandatory property:

- `[prop]target`, `[type]string`. Target directory. If directory is missing, it will be created.

and the following optional properties:

- `[prop]cleanup`, `[type]boolean`. If `true`, target directory will be emptied before exporting icons. Default is `false`.
- `[prop]package`, `[type]object`. Properties for `[file]package.json`. Use this to set at least package name and version.
- `[prop]module`, `[type]boolean`. If `true`, function generates package with ES modules, if `false`, function generates package with CommonJS modules. Default is `true`.
- `[prop]typesContent`, `[type]string`. Custom content of `[file].d.ts` files.
- `[prop]customFiles`, `[type]Record<string, unknown>`. Custom files to export. Key is filename, value is content. See below.

### customFiles

`[prop]customFiles` option contains additional files you want to add to package. Key is filename, value can be one of these types:

- `[type]string`. Content of file.
- `[type]object`. JSON content that will be serialized before writing file.
- `[type]null`. If value is `[type]null`, file is deleted.

## Example

```yaml
src: tools/tools2/export/icon-package.ts
title: 'example.ts'
```