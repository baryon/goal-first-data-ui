# Goal-First Data UI

`goal-first-data-ui` 是一个面向 AI coding agent / 设计 agent 的 UI 审查与设计 skill。它帮助 agent 在做运营台、仪表盘、账户页、表单、列表/详情页、金融/Web3/SaaS 产品界面时，先从用户当前目标和决策出发，而不是从组件库、实现细节或装饰性页面结构出发。

核心原则很简单：**用户当前要做的决策，就是这个页面的中心。**

每条审计规则都锚定具体的设计大师原则（Cooper、Tufte、Nielsen、Norman、Krug、Rams、Tesler、Müller-Brockmann、Raskin、Gestalt、Fitts），不是凭感觉。

## 这个 skill 做什么

它会引导 agent 用一套 10 步的 Goal-First 审查流程：

1. **定义用户目标与决策**（Cooper：goal-directed design）
2. **划定页面边界 / 拆路由**（Cooper + Raskin + Nielsen H8）— 多个不相关目标拆成多个路由，而不是堆在同一页
3. **把每个元素映射到职责**（Norman + Tufte）— core evidence / context / trust-risk / action / feedback / advanced
4. **首屏一个视觉 hero**（Tufte + Müller-Brockmann）— smallest effective difference，禁止首屏等权 metric grid
5. **操作贴在驱动它的数据旁边**（Norman + Gestalt proximity + Fitts's law）
6. **删掉 wizard residue**（Cooper "perpetual intermediates" + Raskin "modes" + Nielsen H7）
7. **用用户的话写文案**（Nielsen H2 + Krug）— 三 pass：词汇换、系统口吻换用户口吻、长度砍一半再砍一半
8. **保留反馈与恢复路径**（Nielsen H1 + H9 + Norman feedback）
9. **密度与节奏平衡**（Tufte data-ink + Müller-Brockmann grid）
10. **每个元素三态判定**（Rams 5 "less but better" + Tesler 复杂度守恒）— 必现 / 状态触发 / 永不渲染

Step 10 不是最后清理，是贯穿 3–9 的纪律。每次给元素分职责（Step 3）、选 hero（Step 4）、写文案（Step 7）时同步问：这个元素是必现、状态触发，还是不该出现？

`SKILL.md` 末尾附了一个完整的 10 步 walkthrough（以一个 delegated-LP 投资 dashboard 为例），方便 agent 对齐输出粒度。

## 适合什么时候用

适合：

- dashboard / home / 数据看板
- account / profile / 账户状态页
- deposit / withdraw / submit 等表单流程
- list / detail 视图
- finance、Web3、SaaS、运营后台、交易型产品界面
- 页面看起来过度 wizard 化、chrome-heavy、工程中心化时
- 多页面任务流需要保持上下文连续性时
- 一页装了 2 个以上明显不同目标，怀疑该拆路由时

不适合作为默认审美套用到：

- 纯营销页
- 品牌叙事页
- editorial / 内容消费页
- 教育优先的解释型页面

除非你明确要对这些页面里的「任务流部分」做审查。

## 安装

用 `skills` CLI 安装即可：

```bash
npx skills add baryon/goal-first-data-ui
```

`skills add` 是问答式的，会继续询问安装范围、目标 agent、是否确认等选项；按提示选择即可。

## 使用方式

安装后，在支持 skills 的 agent 中提出类似请求即可触发：

```text
用 goal-first-data-ui 审查这个 dashboard。
```

```text
这个 Web3 账户页感觉太工程化，帮我按用户目标重构信息层级。
```

```text
检查这个提现流程的反馈、风险提示和移动端首屏密度。
```

agent 会读取 `SKILL.md`，按 10 步流程：先定义用户目标和信任焦虑，判断是否该拆路由，映射元素职责，确立首屏 hero，重排动作位置，用三 pass 翻译文案，保留反馈与恢复路径，最后用三态判定校准每个元素。

## 典型改进方向

- 把信息过载的单页拆成 `/portfolio`、`/transfer`、`/settings` 等独立路由（Step 2）
- 把首屏等权 metric grid 改成"一个 hero + 若干 supporting"的层级（Step 4）
- 把孤立的顶部 action bar 改成靠近数据的上下文操作（Step 5）
- 把"Step 1 / Step 2"回访页面改成自然的状态与上下文布局（Step 6）
- 把"Deposit submitted, please wait…"这类系统口吻文案改成"Sent. ~2 min."（Step 7 voice pass）
- 把套话和填充词的长文案砍到一半再砍一半，过 read-aloud test（Step 7 length pass）
- 把 raw address / hash / tick / nonce / params 收进 Advanced details（Step 7 vocabulary pass）
- 把 spinner + disabled button 改成可理解、可恢复、可追踪的反馈（Step 8）
- 把"为了保持视觉一致性"灰掉的占位 UI 改成只在状态触发时渲染（Step 10）
- 把因极简主义被砍掉的费率 / risk / freshness 加回来——三态判定里它们属于"必现"（Step 10）

## 更新

如果使用 `skills` CLI 安装，可以更新：

```bash
npx --yes skills update goal-first-data-ui
```

如果是手动 `git clone`，进入 skill 目录后拉取最新代码：

```bash
cd ~/.claude/skills/goal-first-data-ui
git pull
```

## 仓库结构

```text
goal-first-data-ui/
├── SKILL.md    # agent 实际读取的 skill 指令（10 步 workflow + 反例分组 + 端到端 walkthrough）
└── README.md   # 面向安装者/使用者的说明
```
