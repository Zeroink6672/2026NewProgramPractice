# 给助教 · 2026 程序练习课题

> 学生看 [README.md](README.md)。这份是教师侧的操作手册。

## 1. 仓库设置（发题前）

| 项 | 建议 |
| --- | --- |
| 可见性 | Public（学生要 Fork，私有仓库 Fork 不出去） |
| 默认分支 | `main` |
| 保护规则 | `main` 禁 force push、禁删除；**不要**勾“Require a pull request”之外没人能推的选项，你自己要能合并 |
| Issues | 开启（学生可以在 issue 里问） |
| Discussions | 可选 |

学生能改的只有 `submissions/` 下的文件，代码在他们自己仓库，所以这个仓库不需要 CI。

## 2. 发题清单

发出去之前确认这几项都写进了 README：

- [ ] 五条教程链接（B 站）
- [ ] Unity 版本 `2022.3.62f3c1`
- [ ] 提交格式（`submissions/<学号>-<姓名>.md`）
- [ ] 你的联系方式

## 3. 验收流程

### 3.1 网页初筛（2 分钟 / 人）

1. 打开 PR，看 `submissions/` 里的 md：仓库链接、视频、WebGL 包是否齐全
2. 点进学生仓库，看根目录有没有：
   - `.gitignore`、`.gitattributes`
   - `Assets/`、`Packages/`、`ProjectSettings/`
   - 有没有误传 `Library/`（仓库体积会到 GB 级）
3. 看提交历史：是不是渐进式提交，有没有“最后一晚一次性传 300 个文件”
4. 点 Release 里的 WebGL 包，能玩就说明基本可运行
5. 不达标就在 PR 里写清楚，退回

### 3.2 本地验证（10–15 分钟 / 人）

```bash
git clone <学生仓库>
cd <仓库>
git lfs install
git lfs pull
```

用 Unity 2022.3.62f3c1 打开：

- [ ] Console 没有红色报错
- [ ] `ProjectSettings/ProjectVersion.txt` 是 2022.3.62f3c1
- [ ] `Packages/manifest.json` 在库里，能正常解析
- [ ] 打开主场景，Play 能玩
- [ ] 开始 → 失败/通关 → 重开，流程完整
- [ ] 脚本有分目录，命名能看懂

### 3.3 在 PR 里反馈

一条评论对应一个问题，写清楚“哪里、什么现象、怎么改”。学生改完 push，PR 自动更新。

## 4. 验收

不设权重，只看是否通过：

- [ ] 工程能被指定版本打开并运行
- [ ] 能完整玩一局：开始 → 玩 → 失败或通关 → 重开
- [ ] 代码有基本结构，不是全塞在一个脚本里
- [ ] `.gitignore`、LFS、README 齐全

通过或打回，评语写在 PR 里。需要打分的话，按学校要求另行处理。

## 5. 查重

公开仓库意味着互相能看，四个手段：

1. **选题可以重复**：只有 5 条教程，不靠题目唯一性查重
2. **提交历史**：一次性传完的、commit 内容明显是别人代码的，重点问
3. **随机答辩**：抽 3–5 人，现场改一个小功能（比如“把跳跃高度改成参数”）
4. **要求标注参考**：跟着教程做可以，但 README 里必须写清参考了哪个、自己改了哪些

## 6. 安全

**打开陌生 Unity 工程会执行编辑器脚本**（导入时的 `OnPostprocessAllAssets`、`InitializeOnLoad` 都会跑）。学生工程理论上可以执行任意代码。

建议：

- 在**虚拟机**或独立系统账号里打开
- 不要用管理员账号，不要在有敏感文件的目录里打开
- 先看 `Assets/Editor/` 和 `Assets/Plugins/` 里有没有奇怪的东西

一个班二十份作业，实际风险不高，但流程上要知道这件事。

## 7. 归档

收齐后：

1. 把每个学生仓库 clone 一份到本地硬盘（学生之后可能删库或改私有）
2. 或在组织下 fork 全部仓库，留作证据
3. 提交仓库的 PR 记录不要删，那是提交时间的证据

## 8. 批量收集

`submissions/` 里的 md 格式统一，可以用脚本汇总成表格：

```bash
grep -h "^- 仓库：" submissions/*.md
grep -h "^- 姓名" submissions/*.md
```

需要的话我可以写一个 `scripts/collect.py`，把 md 解析成 CSV。
