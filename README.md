# Folkbench 探针公开快照周报

由 Folkbench 维护，发布地址为 https://folkbench.github.io/integrity-weekly/ 。

只使用 [folkbench-data](https://github.com/Folkbench/folkbench-data) 中主站已公开的探针汇总。按公开 ID 与测量时间去重；同一记录取当周最后一次观察值。记录数不是当周运行次数，不根据单次一致率判断模型替换。

[主站公开结果](https://folkbench.com/arena?utm_source=github&utm_medium=pages&utm_campaign=integrity-weekly&utm_content=repo-about) · [方法说明](https://folkbench.com/methodology?utm_source=github&utm_medium=pages&utm_campaign=integrity-weekly&utm_content=repo-methodology)

## 自动发布与撤下

A、B 同时上线，无七天等待，也不要求逐期人工审核。每日自动展示当前周已有快照，明确进行中和截止日期；自然周结束后自动封存到 `reports/`，保留固定周 URL、RSS 和 1200×630 PNG。没有数据的日期和历史周不补造。

启用需要 `PUBLIC_DISTRIBUTION_ENABLED=true` 和完整 `FOLKBENCH_TOOLING_SHA`。Pages 使用 GitHub Actions；工作流通过正常 Git hooks 提交。

- 暂停后续自动发布：将仓库变量 PUBLIC_DISTRIBUTION_ENABLED 改为 false。
- 撤下或恢复当前周/某期周报：在 Actions 手动运行 weekly.yml，选择 withdraw / restore，week 填 current 或 YYYY-Www。只改变站点展示，数据与 Git 历史保留。
- 撤下整个站点：在 GitHub Settings → Pages 执行 Unpublish site；重新启用后手动运行 publish。
- 更正记录放在 corrections/，不覆盖已封存的周报文件。

所有回到主站的链接带 pages / integrity-weekly 的 UTM。默认不采集 github.io 站内访问量；后续如启用，只复用现有 PostHog 项目。

## 徽章

```markdown
[![公开快照](https://folkbench.github.io/integrity-weekly/badge.svg)](https://folkbench.github.io/integrity-weekly/)
```
