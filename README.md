# mei-statusbar

《芽衣》角色卡的状态栏前端与 Live2D 立绘资源。

- `mei-statusbar-index.html` — 构建产物（单文件，JS/CSS 全内联），由角色卡正则通过 jsdelivr 加载
- `live2d/` — 四套 Live2D 模型，按场所切换

| 角色 | 校服 | 店内 |
|---|---|---|
| 芽衣 | `May_JK` | `May_JK_Pantie0` |
| 克雷塔 | `Creta_JK` | `Creta_Bikini` |

角色卡内的加载地址：

```
https://testingcf.jsdelivr.net/gh/shizakikanon1/mei-statusbar@<commit>/mei-statusbar-index.html
```

> 上线后请把角色卡 `正则/状态栏界面.html` 里的 `@main` 换成该 commit 的 SHA。
