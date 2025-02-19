---
title: path parse
categories: |
  path
version: 0.84.0
path: |
  Convert a path into structured data.
usage: |
  Convert a path into structured data.
---

# <code>{{ $frontmatter.title }}</code> for path

<div class='command-title'>{{ $frontmatter.path }}</div>

## Signature

```> path parse --extension```

## Parameters

 -  `--extension {string}`: Manually supply the extension (without the dot)


## Input/output types:

| input        | output |
| ------------ | ------ |
| list\<string\> | table  |
| string       | record |
## Examples

Parse a path
```shell
> '/home/viking/spam.txt' | path parse
╭───────────┬──────────────╮
│ parent    │ /home/viking │
│ stem      │ spam         │
│ extension │ txt          │
╰───────────┴──────────────╯
```

Replace a complex extension
```shell
> '/home/viking/spam.tar.gz' | path parse -e tar.gz | upsert extension { 'txt' }

```

Ignore the extension
```shell
> '/etc/conf.d' | path parse -e ''
╭───────────┬────────╮
│ parent    │ /etc   │
│ stem      │ conf.d │
│ extension │        │
╰───────────┴────────╯
```

Parse all paths in a list
```shell
> [ /home/viking.d /home/spam.txt ] | path parse
╭───┬────────┬────────┬───────────╮
│ # │ parent │  stem  │ extension │
├───┼────────┼────────┼───────────┤
│ 0 │ /home  │ viking │ d         │
│ 1 │ /home  │ spam   │ txt       │
╰───┴────────┴────────┴───────────╯

```

## Notes
Each path is split into a table with 'parent', 'stem' and 'extension' fields.
On Windows, an extra 'prefix' column is added.