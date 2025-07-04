# get_news_from_newsnow 插件新闻源配置指南

## 概述

`get_news_from_newsnow` 插件现在支持通过Web管理界面动态配置新闻源，不再需要修改代码。用户可以在智控台中为每个智能体配置不同的新闻源。

## 配置方式

### 1. 通过Web管理界面配置（推荐）

1. 登录智控台
2. 进入"角色配置"页面
3. 选择要配置的智能体
4. 点击"编辑功能"按钮
5. 在右侧参数配置区域找到"newsnow新闻聚合"插件
6. 在"新闻源配置"字段中输入JSON格式的新闻源配置

### 2. 配置文件方式

在 `config.yaml` 中配置：

```yaml
plugins:
  get_news_from_newsnow:
    url: "https://newsnow.busiyi.world/api/s?id="
    news_sources:
      thepaper: "澎湃新闻"
      baidu: "百度热搜"
      cls-depth: "财联社"
      # 可以添加更多新闻源
      weibo: "微博头条"
      douyin: "抖音热搜"
      solidot: "奇客Solidot"
```

## 新闻源配置格式

新闻源配置使用JSON格式，格式为：

```json
{
  "source_id": "显示名称",
  "source_id2": "显示名称2"
}
```

### 配置示例

```json
{
  "thepaper": "澎湃新闻",
  "baidu": "百度热搜", 
  "cls-depth": "财联社",
  "weibo": "微博头条",
  "douyin": "抖音热搜",
  "solidot": "奇客Solidot"
}
```

## 默认配置

如果未配置新闻源，插件将使用以下默认配置：

```json
{
  "thepaper": "澎湃新闻",
  "baidu": "百度热搜",
  "cls-depth": "财联社"
}
```

## 使用说明

1. **配置新闻源**：在Web界面或配置文件中设置新闻源
2. **调用插件**：用户可以说"播报新闻"或"获取新闻"
3. **指定新闻源**：用户可以说"播报澎湃新闻"或"获取百度热搜"
4. **获取详情**：用户可以说"详细介绍这条新闻"

## 注意事项

1. 新闻源的 `source_id` 必须与API接口支持的ID一致
2. 配置更改后需要重启服务或重新加载配置
3. 如果配置的新闻源无效，插件会自动使用默认新闻源
4. JSON格式必须正确，否则会使用默认配置