# mei-statusbar

## 深紫酒红 · 普通着装立绘主视觉

新版将时间地点、关系进度、人物展示、独立心声面板、普通着装详情与存款分层排列。420px 及以下使用纵向心声布局，详情默认折叠，动画遵循减少动态效果设置。

人物只使用普通着装模型；不展示私密详情。每条消息仍只有一个 canvas / 一个 Pixi 应用，保留正常动作复位、表情切换与卸载清理。界面每 2 秒只读当前消息的 MVU `stat_data`，不会归一化或回写剧情变量。

仓库只发布前端构建入口与说明，不包含角色卡、世界书、聊天记录、预览数据或本地配置。维护源码保存在角色卡工程内。

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

前端入口使用固定 commit；Live2D 资源固定到 `907bc77b46ce9765c66bd2a06d01c57efcf5a894`，不随 `main` 分支漂移。

## 维护

每次更新：上传最新前端 → 取得发布 commit SHA → 更新本地 CDN loader → 同步正则导出文件与角色卡。固定 SHA 无需刷新旧版本 CDN 缓存。
