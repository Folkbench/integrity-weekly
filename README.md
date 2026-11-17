# 中转站检测周报 · 模型身份探针公开快照

中转站检测周报汇总 AI API 中转站的模型身份探针公开结果：每个自然周整理一次各中转站申报模型与指纹识别的一致情况，供做模型检测时参考。当前周随每日快照自动更新，完整周结束后封存。单次结果不能证明模型被替换，判断某家中转站仍需结合多次结果和站方条款。

排序沿用主站规则，包含合作档位与运营加分。

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

## 兜底发布与 IndexNow

- 原定时任务保持不变，另有两个入口：数据仓库归档成功后的 `repository_dispatch`（`public-snapshot-archived`）通知，以及北京时间 23:35 的备用定时。自动触发时，如果线上 `publish-state.json` 已经是最新快照，就直接结束，不重复发布。
- 自动发布失败时，本仓库会开一个「公开快照站点自动发布失败」issue，之后发布成功会自动关闭。
- 配置仓库变量 `INDEXNOW_KEY` 后，发布产物输出 `/integrity-weekly/{key}.txt`；部署成功后，把 sitemap 中 lastmod 等于本次归档日期的 URL 推送到 IndexNow。推送失败只记日志，不影响发布结果。

## 其它公开快照视图

- [AI 中转站排行](https://folkbench.github.io/relay-rank/)：按模型的每日公开快照与历史名次
- [AI 中转站对比](https://ai-relay-bench.github.io/)：同一模型在各中转站的并排对比
- [AI API 价格对比](https://aiapi-rank.github.io/)：中转站公开标价与官方参考价
- [AI 中转站大全](https://ai-zhongzhuan.github.io/)：站点目录、公开资料与新手指南
- [模型检测快照](https://ai-model-check.github.io/)：每日模型身份探针汇总
