# mei-statusbar

《芽衣》角色卡的状态栏前端。GitHub 保存单文件构建产物，角色卡通过 CDN 加载，不再内嵌整个前端。

## 文件

- `mei-statusbar-index.html`：当前状态栏（JS/CSS 内联），保留单 canvas / 单 Pixi 应用与停止默认动作的修正。
- `live2d/`：现有 Live2D 资源。本次只更新前端，不上传角色卡、世界书或本地配置。

## CDN 加载

将下方 `<commit>` 替换为本次发布的完整 commit SHA，保留代码块围栏后放入角色卡的「状态栏界面」正则替换内容。

````html
```
<body>
<script>
$(function () {
  $('body').load('https://testingcf.jsdelivr.net/gh/shizakikanon1/mei-statusbar@<commit>/mei-statusbar-index.html', function (_response, status) {
    if (status === 'error') {
      $('body').text('状态栏加载失败，请检查网络后重试。');
    }
  });
});
</script>
</body>
```
````

占位符仍为 `<StatusPlaceHolderImpl/>`。保留原有 Vue、jQuery、酒馆助手与 MVU 环境依赖。

前端入口使用固定 commit；Live2D 资源固定到 `c1889c11cde6dd074fe891fd761a74c023542230`，不随 `main` 分支漂移。

## 维护

每次更新：上传最新前端 → 取得发布 commit SHA → 更新本地 CDN loader → 同步正则导出文件与角色卡。固定 SHA 无需刷新旧版本 CDN 缓存。
