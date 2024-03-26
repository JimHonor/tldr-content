---
ctime: 2023-11-26
publishAt: "2023-10-06"
title: "vite environment variable"
---

## 在哪里声明环境变量

`.env` 文件：
- 在 `vite.config.js` 里通过 `envDir` 指定环境变量文件所在目录。默认为 `root` 。
- 新建目录，新建文件，自定义环境变量。
- 对于 `VITE_` 开头的环境变量，将会暴露给客户端。
- [envdir | Shared Options | Vite](https://vitejs.dev/config/shared-options.html#envdir)

## 声明环境变量

Here's how you declare an environment variable:

```env
# .env
VITE_APP_TITLE=PayPayDuck
```

## 在 client side 读取环境变量

Then to use this environment variable in client side code, you can use the `import.meta.env` object:

```js
// /src/main.js
console.log(import.meta.env.VITE_APP_TITLE) // > PayPayDuck
```

These are all the properties that the `import.meta.env` object give us:

```json
{
  "BASE_URL": "/",
  "MODE": "development",
  "DEV": true,             // 是否运行在 development 模式下
  "PROD": false,           // 是否运行在 production 模式下
  "SSR": false,
  "VITE_APP_TITLE": "PayPayDuck"
}
```

## 在 vite.config.js 读取环境变量

To use the enviroment varible in server side code, you can use the `loadEnv`  function provided by Vite:

```js
import { defineConfig, loadEnv } from "vite";

export default defineConfig(({ mode }) => {
	const envDir = ''
	const envAll = loadEnv(mode, envDir, '');
	console.log(envAll.OUTPUT_DIR);
	
	return {
    // ...
  };
});
```

`loadEnv(mode, envDir, '')` 加载的是所有环境变量。

`loadEnv(mode, envDir)` 加载的是仅带有 `VITE_` 前缀的环境变量。

```js
import { defineConfig, loadEnv } from "vite";

export default defineConfig(({ mode }) => {
	const envDir = ''
	const envOnlyWithTheVITE_Prefix = loadEnv(mode, envDir);
	console.log(envAll, envOnlyWithTheVITE_Prefix);
	console.log(envAll.OUTPUT_DIR);
	return {
    // ...
  };
});
```

## my practical use case

1）通过环境变量将 build 和 watch 的 outputDir 区分开，前者是稳定版的，后者是开发中的。
- 思路：
- 实现：

```js
import { defineConfig, loadEnv } from "vite";
import { resolve } from "path";

const envDir = resolve(__dirname, "env");

export default defineConfig(({ mode }) => {
  const env = loadEnv(mode, envDir, "");
  return {
    envDir: "env",
    build: {
      outDir: env.OUTPUT_DIR,
    },
  };
});
```

## 环境变量的工作原理

当运行 `vite build` 命令时，会从 `.env.production` 文件(如果存在的话)加载环境变量。

## mode

可以通过 `--mode` option flag 来覆盖一个命令的默认模式。
- 示例：将 `vite build` 命令的模式改为 staging ，并从 `.env.staging` 文件中加载环境变量 :

```bash
vite build --mode staging
```

```env
# .env.staging
VITE_APP_TITLE=My App (staging)
```
