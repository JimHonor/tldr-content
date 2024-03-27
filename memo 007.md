---
ctime: 2024-03-27
title: "github actions checkout"
---

使用 actions/checkout 来 checkout 仓库时，要注意的是如果你的仓库包含了 submodule，那么需要添加 `submodules: true` 选项才会 checkout submodules 。

```yaml
- uses: actions/checkout@v4
	with:
	  submodules: true
```

source: https://github.com/actions/checkout