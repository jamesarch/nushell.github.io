---
title: math arctan
categories: |
  math
version: 0.84.0
math: |
  Returns the arctangent of the number.
usage: |
  Returns the arctangent of the number.
---

# <code>{{ $frontmatter.title }}</code> for math

<div class='command-title'>{{ $frontmatter.math }}</div>

## Signature

```> math arctan --degrees```

## Parameters

 -  `--degrees` `(-d)`: Return degrees instead of radians


## Input/output types:

| input        | output       |
| ------------ | ------------ |
| list\<number\> | list\<number\> |
| number       | number       |
## Examples

Get the arctangent of 1
```shell
> 1 | math arctan
0.7853981633974483
```

Get the arctangent of -1 in degrees
```shell
> -1 | math arctan -d
-45
```


**Tips:** Command `math arctan` was not included in the official binaries by default, you have to build it with `--features=extra` flag