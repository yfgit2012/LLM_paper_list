# 陈成's Post

𝕏 **Source:** X
**@陈成**

---

## Summary

The user reverse-engineered Claude Code's `/loop` command, revealing it functions as a cron wrapper with unique behavior: it converts user input into cron expressions, triggers tasks every second during REPL idle periods, and allows ±10% timing variance. The command's design balances automation with resource efficiency.

**Category:** AI agents and tools

---

## Original Content

我反编译了 Claude Code 的 /loop 命令，搞清楚它底层到底在干嘛。 结论：它就是一个 cron 包装器，但细节很有意思 👇 • 输入 /loop 5m 检查部署 → AI 解析时间 → 生成 cron 表达式 → 调用内部 CronCreate • 每秒 tick 一次，但只在 REPL 空闲时才触发 • 任务有 ±10%… &mdash; 陈成 (@chenchengpro) March 7, 2026

---

[View Original](https://x.com/chenchengpro/status/2030291945554108720)
[View on Nitter](https://nitter.net/chenchengpro/status/2030291945554108720)
