---
name: say-xiaoai
description: 当用户以“小爱同学”开头进行对话时，调用此工具执行本地语音脚本。
---

# Say Xiaoai

## Use When

用户以"小爱同学"开头进行对话时，例如：
- "小爱同学今天天气怎么样？"
- "小爱同学打开客厅的灯"
- "小爱同学播放音乐"

## Parameters

| Name | Type | Description | Required |
|------|------|-------------|----------|
| query | string | 除去"小爱同学"触发词后的剩余文本内容 | Yes |

## How It Works

1. 当用户输入以"小爱同学"开头时，此 skill 会被触发
2. 提取"小爱同学"后面的文本内容作为 `query` 参数
3. 执行本地脚本 `./scripts/say_xiaoai.sh` 并传入 `query` 参数
4. 脚本使用 macOS 的 `say` 命令语音输出"小爱同学"，然后语音输出查询内容

## Scripts

```bash
bash ./scripts/say_xiaoai.sh "$query"
```

## Example

**用户输入**: "小爱同学，今天天气怎么样？"

**skill 执行**:
```bash
bash ./scripts/say_xiaoai.sh "今天天气怎么样？"
```

**脚本输出**:
- 语音说出"小爱同学"
- 等待2秒
- 语音说出"今天天气怎么样？"

## Requirements

- macOS 系统（需要 `say` 命令）
- 脚本执行权限（已设置）
