# Kimi 事件触发自动化 · MVP Demo

在线体验：https://bill306.github.io/kimi-event-trigger-case2/ （请用电脑上的 Chrome 或 Edge 打开）

场景：新会议录音 → 自动生成会议纪要。

1. **Configure**：用一句话描述自动化，生成 Automation Card，确认后选择一个本地文件夹。
2. **Detect**：往文件夹里保存录音（访达拖入，或用页面里的测试按钮写入）。Watcher 检测到变化后，等文件大小稳定，再做类型检查（扩展名 + 文件头）和 SHA-256 去重。
3. **Execute**：生成 Event Payload，组装最小必要 Context。在浏览器本地用 Whisper 转写；纪要由 Kimi 生成（需填写自己的 API Key），不填则用离线规则生成。
4. **Deliver**：发桌面通知，把纪要和 execution-log.jsonl 写到文件夹里的 `Kimi纪要/` 子目录。
5. **Validate**：页面上的验证清单会自动勾选“正常执行 / Duplicate Event / Incomplete File / Execution Failure”。

- 音频只在本机处理。只有填写了 Kimi API Key 时，转写文字才会发给 Kimi。
- API Key 只保存在页面内存里，刷新即清空。
- `samples/` 里的示例录音由 macOS 语音合成生成。
