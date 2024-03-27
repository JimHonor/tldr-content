---
ctime: 2024-03-27
title: "git errors"
---

运行 `git push` 命令遇到问题：
- `fatal: unable to access '<repo_url>': Failure when receiving data from the peer`

运行 `git push` 命令遇到问题：
- `fatal: unable to access '<repo_url>': Failed to connect to github.com port 443 after 21092 ms: Couldn't connect to server`

解决方法是，运行以下命令取消代理：

```bash
git config --global --unset http.proxy
git config --global --unset https.proxy
```
