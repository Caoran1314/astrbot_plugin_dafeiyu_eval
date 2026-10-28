# 大肥鱼拟人度评测

只观测不干预：统计机器人回复的字数、分条、问句比例、AI 腔和延迟

## 它解决什么问题

「像人」不能靠感觉判断。这个插件只观测不改写，把每条出站回复拆成 6 个指标：
平均字数、多段率、问句结尾率、AI 腔命中、markdown/冒号/破折号、响应延迟。
给每个指标一个目标区间，`/eval` 输出对照表，一眼看出哪里还不像人。

## 安装

### 方式一：插件市场

在 AstrBot 面板 → 插件 → 插件市场 里搜索 `dafeiyu_eval`。

### 方式二：手动

```bash
cd AstrBot/data/plugins
git clone https://github.com/Caoran1314/astrbot_plugin_dafeiyu_eval
```

然后重启 AstrBot，或在面板里点「重载」。

## 配置

装好后在 面板 → 插件 → 大肥鱼拟人度评测 → 配置 里调。

| 配置项 | 默认 | 说明 |
|---|---|---|
| `enabled` | true | 是否记录 |
| `retention_days` | 30 | 数据保留天数 |
| `report_hours` | 24 | 默认统计窗口 |

## 命令

| 命令 | 作用 |
|---|---|
| `/eval` | 24 小时报告 |
| `/eval 72` | 72 小时报告 |
| `/eval export` | 导出盲测素材（去掉来源，给人打分） |

## 依赖

无（纯标准库）

## 说明

- 只调用 AstrBot 自己的钩子，不修改框架代码
- 所有数据都在本地，不上传任何内容
- 适配平台：`aiocqhttp` / `webchat`

## License

MIT
