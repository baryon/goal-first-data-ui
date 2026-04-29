# Goal-First Data UI

`goal-first-data-ui` 是一个面向 AI coding agent / 设计 agent 的 UI 审查与设计 skill。它帮助 agent 在做运营台、仪表盘、账户页、表单、列表/详情页、金融/Web3/SaaS 产品界面时，先从用户当前目标和决策出发，而不是从组件库、实现细节或装饰性页面结构出发。

核心原则很简单：**用户当前要做的决策，就是这个页面的中心。**

## 这个 skill 做什么

它会引导 agent 用「Goal-First」方式审查或重构数据密集型 UI：

- 明确用户打开页面时想知道、决定、完成什么。
- 判断每个界面元素属于核心证据、上下文、信任/风险、动作、反馈/恢复，还是高级技术细节。
- 删除、降级或折叠与当前决策无关的内容。
- 把操作按钮放到驱动这个操作的数据旁边，而不是统一堆在顶部操作栏。
- 把工程语言翻译成用户能理解的业务语言。
- 保留加载、成功、失败、重试、撤销、收据、帮助等反馈与恢复路径。
- 检查移动端首屏密度、可访问性、长文本、本地化和 200% 字号缩放。

## 适合什么时候用

适合：

- dashboard / home / 数据看板
- account / profile / 账户状态页
- deposit / withdraw / submit 等表单流程
- list / detail 视图
- finance、Web3、SaaS、运营后台、交易型产品界面
- 页面看起来过度 wizard 化、chrome-heavy、工程中心化时
- 多页面任务流需要保持上下文连续性时

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

agent 会读取 `SKILL.md`，按照其中的流程先定义用户目标和信任焦虑，再映射元素职责、调整首屏优先级、重排动作位置、翻译工程语言，并保留必要的反馈与恢复路径。

## 典型改进方向

- 把「Step 1 / Step 2」式回访页面改成自然的状态与上下文布局。
- 把孤立的顶部 action bar 改成靠近数据的上下文操作。
- 把 raw address、hash、tick、nonce、params 等技术细节收进 Advanced / Technical details。
- 把空状态从 CTA billboard 改成解释状态、预期结果和可选下一步。
- 把 spinner + disabled button 改成可理解、可恢复、可追踪的操作反馈。
- 把堆叠 metric cards 改成更节省移动端首屏的连续信息结构。

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
├── SKILL.md    # agent 实际读取的 skill 指令
└── README.md   # 面向安装者/使用者的说明
```
