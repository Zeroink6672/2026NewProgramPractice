# 2026 程序练习课题 · 提交仓库

> 浙江工业大学 创游工坊 · 2026

## 这个仓库是干什么的

**只收链接，不收代码。**

你的 Unity 工程放在**你自己的 GitHub 仓库**里；这个仓库只登记一行信息：
仓库地址、游戏名、演示视频，方便助教统一验收。

提交方式：**Fork 本仓库 → 在 `submissions/` 下加一个文件 → 开 Pull Request**。

---

## 课题：复刻一款小游戏

根据下面任意一条教程（长度约 1 小时），复刻出教程里的游戏。
**工程文件保存在你自己的 GitHub 仓库里**，本仓库只登记链接。

| # | 游戏 | 教程 |
| --- | --- | --- |
| 1 | Floppy Bird | https://www.bilibili.com/video/BV1ZP411T7eW |
| 2 | Doodle Jump | https://www.bilibili.com/video/BV1mZ421J78K |
| 3 | Bubble Struggle | https://www.bilibili.com/video/BV1rZ42177xk |
| 4 | 愤怒的小鸟 | https://www.bilibili.com/video/BV1Xi421C7Bf |
| 5 | 平衡赛车 | https://www.bilibili.com/video/BV1uz421D79M |

五选一，**允许多人选同一个**，各自独立完成。

**“复刻”的范围**：跟着教程做出一款能完整玩一局的游戏（开始 → 玩 → 失败或通关 → 重开）。
美术不考核，用教程里的素材或纯色方块都行。

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

有问题在 PR 里问，或在群里 @ 助教。
