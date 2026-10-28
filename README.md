<p align="center">
  <img src="https://img.shields.io/badge/AstrBot-%3E%3D4.24.0-blue" alt="AstrBot">
  <img src="https://img.shields.io/badge/version-v0.1.0-green" alt="version">
  <img src="https://img.shields.io/badge/license-MIT-brightgreen" alt="license">
  <img src="https://img.shields.io/badge/platform-aiocqhttp%20%7C%20webchat-purple" alt="platform">
</p>

# 大肥鱼拟人度评测

只观测不干预：量化统计机器人回复到底像不像人

> 当前版本：**v0.1.0** · 许可证：**[MIT](LICENSE)** · 作者：**[Caoran1314](https://github.com/Caoran1314)**

---

## 为什么需要它

"这个机器人像不像人"通常靠感觉。但感觉会骗人，指标不会。

本插件**只观测，不改写任何回复**。每条出站消息被拆成 6 个指标：

| 指标 | 目标区间 | 为什么 |
|---|---|---|
| **平均字数** | ≤ 20 字 | 真人一条消息通常 5~15 字 |
| **多段率** | 50% ~ 100% | 真人习惯分多条发 |
| **问句结尾** | ≤ 30% | 每句都在问 = 客服腔 |
| **AI 腔命中** | = 0 | "作为一个 AI""有什么可以帮你的" |
| **标点违规** | = 0 | 句号 / 冒号 / 破折号 |
| **响应延迟** | 记录即可 | 太快反而不像人 |

## 报告长这样

```text
📊 近 24 小时拟人度（37 条）

  平均字数   7.2 字        ✅ 目标 ≤20
  多段率     89%           ✅ 目标 50%~100%
  问句结尾   5%            ✅ 目标 ≤30%
  AI 腔      0 次          ✅ 目标 0
  标点违规   0 次          ✅ 目标 0
  延迟中位数 1.35 s        ℹ️ 仅供参考

结论：5/5 达标，像人。
```

## 安装

### 方式一：插件市场

面板 → 插件 → 插件市场 → 切到「大肥鱼插件集」→ 安装。

### 方式二：手动

```bash
cd AstrBot/data/plugins
git clone https://github.com/Caoran1314/astrbot_plugin_dafeiyu_eval.git
```

> 无第三方依赖，纯标准库。

## 配置

| 配置项 | 类型 | 默认值 | 说明 |
|---|---|---|---|
| `enable` | bool | `true` | 只记录指标，不修改任何回复内容 |

## 命令

| 命令 | 作用 |
|---|---|
| `/eval` | 24 小时报告 |
| `/eval 72` | 72 小时报告 |
| `/eval export` | 导出盲测素材（去掉来源信息，拿去让人打分） |

## 盲测怎么用

`/eval export` 会导出一批 `{"id": 1, "text": "..."}` 的样本，混入**真人聊天记录**，
让你朋友猜哪边是 AI。猜不对，说明这条及格了。这比任何自动指标都可靠。

## 数据

- 数据在 `data/plugin_data/dafeiyu_eval/eval.db`
- 默认保留 `retention_days`（30 天），超期自动清理
- 只记录字数/结构/延迟这类统计特征，导出时不含用户身份

## License

[MIT](LICENSE)
