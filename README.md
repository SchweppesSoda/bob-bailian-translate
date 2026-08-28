# 百炼翻译 for Bob

[![Verify](https://github.com/SchweppesSoda/bob-bailian-translate/actions/workflows/verify.yml/badge.svg)](https://github.com/SchweppesSoda/bob-bailian-translate/actions/workflows/verify.yml)

Bob 1.8+ 的阿里云百炼文本翻译插件，公开包支持按量付费和 Token Plan。插件直接使用你在 Bob 设置中保存的 API Key 请求百炼，不经过第三方服务器。

## 安装

从 [最新 Release](https://github.com/SchweppesSoda/bob-bailian-translate/releases/latest) 下载 `.bobplugin`，双击安装，然后在插件设置中填写对应计费模式的 API Key。

## 主要能力

- `$http.streamRequest` 流式翻译；首段立即显示，后续细碎事件合并成较少的累计全文回调。
- 订阅 Bob `cancelSignal`，取消后释放订阅并阻止晚到分片或完成回调。
- `qwen-mt-plus` 使用官方要求的英文完整语言名，并自动切换为非流式请求。
- 思考默认关闭；开启后可选择 Automatic、Low、Medium 或 High。
- 支持中国/新加坡按量付费、Workspace 地址和可信 HTTPS 自定义端点。
- 本地校验配置，不通过验证调用模型，也不会消耗额度。
- API Key 错误信息自动脱敏。

Token Plan 使用核对过的精确模型目录，API Key、计费模式、地域和 Base URL 必须配套。阿里云禁止 Coding Plan 用于自定义应用，因此公开 manifest 和运行时都不提供该线路。

## 验证状态

共享 Core、Bob 模拟宿主、macOS 合约 CI、流式分片、取消信号、Qwen-MT 请求和安装包结构均已自动测试。真实 Bob 应用内的安装与取消操作仍属于 Early Access 验证范围，欢迎在本仓库反馈结果。

## 源码关系

这是只负责 Bob 分发、appcast 和自动索引的薄仓库。权威源码位于 [`SchweppesSoda/manggo-bailian-plugin`](https://github.com/SchweppesSoda/manggo-bailian-plugin)，本版本由提交 [`fdf51b6`](https://github.com/SchweppesSoda/manggo-bailian-plugin/commit/fdf51b6e65e704b3bf4bb3e106e4e4b7b42d4a44) 构建。

## License

[MIT](LICENSE)
