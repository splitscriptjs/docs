---
cover: ../.gitbook/assets/core cli.png
coverY: 0
---

# cli

### help

Get a list of commands

```sh
splitscript
# or
splitscript -h
# or
splitscript --help
```

### help \[command]

Get help for a specific command

```bash
splitscript help [command]
# or
splitscript [command] -h
```

### add \<package>

Add an event listener

```bash
splitscript add <package>
```

Select an event to create and hit `ENTER`

This will create a file in the `functions/` folder with some boilerplate code (types included) which will [automatically be cjs, esm or ts](cli.md#finding-type-of-project)

### remove \<package>

Remove an event listener

```shell
splitscript remove <package>
```

This will look for all existing events. Select an event to delete. Then, select the files you want to use with `SPACE`, then hit enter to submit

### dev \[file]

Enable developer mode

```bash
splitscript dev [file]
```

This will watch for new files under the `functions/` folder, and add some boilerplate code (types included)

It will detect the [type of project](cli.md#finding-type-of-project) automatically and create code with the matching syntax

If `[file]` is provided, it will start that file as well. If it is a typescript file, it will compile, then run

## finding type of project

for `javascript` projects, we look in the `package.json` file of the cwd and check the type field. if that doesn't exist, we default to `commonjs`

to find if a project is `typescript`, we check if a `tsconfig.json` file exists, and if `typescript` is set to `true` in `ss.json`
