# 2026 程序练习课题 · 提交仓库

> 浙江工业大学 创游工坊 · 2026

## 这个仓库是干什么的

**只收链接，不收代码。**

你的 Unity 工程放在**你自己的 GitHub 仓库**里；这个仓库只登记一行信息：
仓库地址、游戏名、演示视频，方便助教统一验收。

提交方式：**Fork 本仓库 → 在 `submissions/` 下加一个文件 → 开 Pull Request**。

---

## 课题：复刻一个小游戏

从下面选一个，**一人一个，先到先得**。
选之前先看 `submissions/` 目录和开着的 PR，确认没被人占。

| # | 游戏 | 核心玩法 |
| --- | --- | --- |
| 1 | Flappy Bird | 点击控制高度，穿过管道 |
| 2 | 2048 | 滑动合并数字 |
| 3 | 贪吃蛇 | 吃食物变长，撞墙或撞自己结束 |
| 4 | 打砖块 | 挡板反弹球，清空砖块 |
| 5 | 俄罗斯方块 | 下落、旋转、消行 |
| 6 | 是男人就下 100 层 | 左右移动，踩平台往下 |
| 7 | Pong | 双人 / AI 对打乒乓球 |
| 8 | 跳一跳（简化） | 蓄力跳跃，落在方块上 |

**“复刻”的范围**：核心玩法 + 一个完整局（开始 → 玩 → 失败或通关 → 重开）+ 分数。
美术不考核，用现成素材或纯色方块都行。

---

## 你要做什么

### 第 0 步 · 准备环境

| 需要 | 要求 |
| --- | --- |
| Unity | **2022.3.62f3c1**（和美术课题同一个版本） |
| Unity Hub | 用 [unity.cn](https://unity.cn) 的 Hub 安装 |
| Git | 2.30 以上 |
| Git LFS | **必须**，否则图片音频会变成指针文件 |
| GitHub 账号 | 放工程、提交 |

装完 Git LFS 后执行一次：

```bash
git lfs install
```

> 版本必须完全一致。用 2022.3 的其他小版本也能打开，但助教验收时会提示版本不一致，
> 所以统一用 `2022.3.62f3c1`。

### 第 1 步 · 在 GitHub 建自己的工程仓库

1. GitHub → **New repository**
2. 名字：`game-<游戏名>-<姓名拼音>`，例如 `game-flappy-zhangsan`
3. 选 **Public**（私有仓库助教打不开；一定要私有的话，提前把助教加为 collaborator）
4. **不要**勾 README / .gitignore / license

### 第 2 步 · 本地建 Unity 工程并对接仓库

1. Unity Hub 新建 **3D (URP)** 工程，版本 `2022.3.62f3c1`
2. 在工程根目录执行：

```bash
git init
git lfs install
```

3. 在根目录放两个文件：

**`.gitignore`**：用 GitHub 官方的 Unity 模板
（`github/gitignore` 仓库里的 `Unity.gitignore`）。

> `Library/`、`Temp/`、`Logs/`、`obj/`、`Build/` **一个都不能进库**。
> 这几个目录加起来能有好几个 G，传上去仓库就废了。

**`.gitattributes`**：

```
* text=auto
*.png filter=lfs diff=lfs merge=lfs -text
*.psd filter=lfs diff=lfs merge=lfs -text
*.wav filter=lfs diff=lfs merge=lfs -text
*.mp3 filter=lfs diff=lfs merge=lfs -text
*.fbx filter=lfs diff=lfs merge=lfs -text
*.unity  merge=binary
*.prefab merge=binary
```

4. 关联远端并首次推送：

```bash
git remote add origin https://github.com/<你的账号>/<仓库名>.git
git add .
git commit -m "chore: 初始化 Unity 工程"
git push -u origin main
```

5. 推完去 GitHub 上看一眼：`Library/` 有没有被传上去。传上去就说明 `.gitignore` 没生效。

### 第 3 步 · 开发

- **每天至少一次有意义的提交**，不要最后一天一次性传完——提交历史是助教判断“是不是自己做的”的依据
- 场景、脚本、预制体分开提交，commit message 写清楚做了什么
- 大文件确认走了 LFS：

```bash
git lfs ls-files
```

- 建议目录：

```
Assets/
├── Scenes/        Main.unity
├── Scripts/       按功能分：Player/、Game/、UI/
├── Prefabs/
├── Audio/
└── Art/
```

### 第 4 步 · 自测（提交前必须做）

在你自己的机器上模拟一次“别人拿到我的仓库”：

1. 删掉本地 `Library/`，重新打开工程，Console 不能有报错
2. 按 Play 能完整玩一局：开始 → 玩 → 失败/通关 → 重开
3. 打一个 **WebGL** 构建，压缩后放到 GitHub **Release**
   （Release 单个文件上限 2GB，WebGL 一般 30–100MB，没问题）
4. 录一段 **30–60 秒**演示视频
5. 仓库根目录写一个 README，至少包含：
   - 游戏名、玩法、操作键位
   - 怎么运行（打开哪个场景 / 下载哪个包）
   - 参考了哪些教程或素材
   - 已知问题

### 第 5 步 · 提交

1. **Fork 本仓库**
2. 在 `submissions/` 下新建 `<学号>-<姓名拼音>.md`，内容按下节模板
3. Commit → Push → 开 **Pull Request** 到本仓库的 `main`
4. PR 标题写：`提交：<游戏名> - <姓名>`

### 第 6 步 · 返修

助教直接在 PR 里评论。改完后在**同一个分支**继续 commit + push，PR 会自动更新，不用重新开。

---

## 提交文件模板

文件名：`submissions/2026xxxx-zhangsan.md`

```markdown
# 复刻：Flappy Bird

- 姓名 / 学号：张三 / 2026xxxx
- 仓库：https://github.com/zhangsan/game-flappy
- Unity 版本：2022.3.62f3c1
- 运行方式：打开 Assets/Scenes/Main.unity 按 Play
- WebGL / 可执行包：<Release 链接>
- 演示视频：<链接>
- 参考的教程 / 素材：<链接>
- 我自己额外做的：最高分存档、难度递增
```

---

## 评分标准

| 项 | 权重 | 看什么 |
| --- | --- | --- |
| 核心玩法 | 40 | 复刻到位、能玩、有完整的开始/结束/重开 |
| 完成度与打磨 | 20 | 手感、音效、UI、难度曲线 |
| 代码结构 | 20 | 脚本组织、命名、有没有把逻辑塞进一个上千行的类 |
| 工程规范 | 10 | 版本锁、`.gitignore`、LFS、README |
| 演示与答辩 | 10 | 能否讲清自己写了什么、参考了什么 |

**技术门槛**：工程必须能被助教用指定版本打开并运行。打不开或跑不起来的，先打回修，不计分。

---

## 常见问题

| 现象 | 原因 | 处理 |
| --- | --- | --- |
| 仓库好几个 G | 把 `Library/` 传上去了 | 加 `.gitignore`，`git rm -r --cached Library`，重新提交 |
| 图片/音频只有 100 多字节 | 没装或没启用 Git LFS | `git lfs install` → `git lfs migrate import --include="*.png,*.wav"` |
| 助教打不开仓库 | 仓库是 Private | 改 Public，或把助教加成 collaborator |
| 打开工程一堆报错 | 版本不一致，或 `Packages/` 没提交 | 用 2022.3.62f3c1 重新打开；确认 `Packages/manifest.json` 在库里 |
| 按 Play 没反应 | 场景没加到 Build Settings，或者打开的是空场景 | 打开 `Assets/Scenes/Main.unity`；File → Build Settings 里加场景 |
| PR 里只有一行链接，助教怎么看代码 | 这是登记仓库，代码在你自己的仓库 | 正常，助教点链接过去看 |

---

## 截止时间

`2026-11-__ 23:59`（以 PR 创建时间为准）

有问题在 PR 里问，或在群里 @ 助教。
