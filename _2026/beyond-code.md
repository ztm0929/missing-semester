---
layout: lecture
title: "代码之外"
description: 了解开发者不可或缺的软技能，包括文档编写、开源社区的协作规范，以及与 AI 互动的基本礼仪。
thumbnail: /static/assets/thumbnails/2026/lec8.png
date: 2026-01-22
ready: true
video:
  aspect: 56.25
  id: 2DOEATfXT8k
---

成为一名优秀的软件工程师，不只是写出能运行的代码。更重要的是写出别人（包括未来的自己）能理解、能维护、并能继续构建的代码。这也意味着要清晰表达、审慎协作，并在你所参与的生态中——无论开源还是闭源——做一个负责任的公民。

# 单向沟通

软件工程中有大量工作，本质上是在为缺少当前上下文的人写作：后来加入的队友、接手你代码的维护者，或是六个月后已经忘了当初决策缘由的你自己。对于此类写作，一个关键建议是：**你的目标应是记录并传达「为什么」，而不只是「做了什么」。**「做了什么」往往一眼可见；真正来之不易、也最容易被时间冲淡的，是「为什么」。

工程师之间最常见的沟通形式（除代码本身外）大概就是注释。我个人一直觉得，很多注释并无价值。但注释完全本可以很有用！好的注释解释的是代码本身无法表达的内容：**为什么要这样做**，而不是它如何运作（代码已写得很清楚）。好注释能省下数小时困惑；坏注释只会制造噪音，甚至误导读者。

几乎总是值得写的注释类型包括：

- **TODO**：标记尚未完成或尚不完善的部分，但要留下足够上下文，让后来者知道还有什么没做、为何暂缓。`TODO: optimize` 是无效信息；`TODO: 这个 O(n²) 循环在 n<100 时可接受，但规模扩大后需要索引` 才具可执行性。
- **参考来源**：当代码实现了论文算法、改写了外部实现，或编码了文档规定的行为时，请附上外部来源链接（尽量用永久链接），并注明与原参考的差异。
- **正确性说明**：解释为什么一段非平凡代码能得到正确结果。代码展示步骤，注释补上「为何成立」。
- **踩坑经验**：如果你花了 30 分钟以上才排查出问题，而修复依赖某条不明显的「咒语」，请把它写下来。过去的你都没意识到它必要，未来读者更不会。
- **常量依据**：魔法数字都应有解释。为什么是 1492？为什么是 16 位？是随手选的、测试推导的，还是正确性要求？哪怕「随机选的」，也是有价值的信息。
- **关键实现选择**：若正确性依赖某个看似无害的实现细节（如「这里必须用 BTreeSet，因为后续依赖迭代顺序」），务必明确写出。
- **「为何不用」**：当你刻意避开显而易见的方案时，要解释原因。否则后人很可能「顺手修正」，结果反而引入问题。

README（你有吧？）也是其他开发者接触项目的常见第一入口。好的 README 应立刻回答四个问题：它做什么？我为什么关心？怎么用？怎么安装？而且按这个顺序组织。结构应像漏斗：顶部先给一句话概述，最好再加一个可视化演示，让人几秒内判断这是否解决自己的问题；随后再逐层展开细节。先讲用法，再讲安装——人们总想先知道值不值得，再决定是否投入配置成本。

提交信息（commit message）同样是常被忽视的「为他人写作」。它们常写成「fixed blah」或「added foo」；某些场景下也许够用，但别忘了：**提交历史是代码库为何演化至此的档案**。当有人（包括你自己）运行 `git blame` 去理解一处令人困惑的改动时，好的提交信息应能给出答案。

一般来说，提交正文应回答：
- 什么问题迫使你做这次改动？
- 你考虑过哪些替代方案？
- 有哪些权衡与影响？
- 这个方案里有什么可能让人意外之处？

> 当然，细节应与复杂度匹配。修一个单行拼写错误，只需一行标题；而一个耗费数小时才定位的微妙竞态修复，则值得用数段文字解释问题与解法。

对于复杂改动，采用「问题 → 方案 → 影响」的结构通常很有效：先交代触发变更的约束或痛点，再说明改了什么以及关键设计决策，最后列出值得关注的后果（正反两面都要写）。最后这部分尤为重要：真实工程总是在权衡中推进。把「这是有意取舍」写清楚，能避免后来者误以为你忽略了问题。

**LLM 的确可以帮助撰写提交信息。**但如果你只是把改动丢给它，让它直接生成提交说明，**它通常只看得到「做了什么」，看不到「为什么」**。结果往往是偏描述性的提交信息——这恰恰背离我们的目标。如果你本来就在同一会话中借助 LLM 完成这次改动，再让它写提交信息通常会好得多，因为你们的对话天然包含丰富上下文。否则（或除此之外），一个实用技巧是：明确告诉 LLM 你希望提交信息聚焦「为什么」（以及上述细节），并**要求它主动向你追问缺失上下文**。换言之，你是在把自己当作它可调用的「上下文工具（MCP）」。

随着改动复杂度上升，也要把提交按逻辑拆分（`git add -p` 很好用）。每个提交都应代表一个可独立理解、可独立评审的完整改动。不要把重构和新功能混在一起，也别把无关 bug 修复塞进同一提交——这会模糊「哪次改动修了什么问题」的叙事，并几乎必然拖慢评审节奏。它还会让你在 `git bisect` 时如有神助，不过那是另一个故事了。

> One note as you start being more diligent about technical writing, and
> using it more extensively, make sure you respect the reader. It's easy
> to end up over-explaining once you start, but you have to resist that
> urge lest the reader read _none_ of what you've written. Explain the
> "why" and trust them to figure out the "how" for their situation.

# Collaboration

As engineers, we may spend a large part of our job coding at our own
keyboard, but a sizeable chunk of our time is also taken up by
communicating with others. That time is usually split into collaboration
and education, and the payoff from investing in getting better at both is
significant.

## Contributing

Whether you are submitting a bug report, contributing a simple bug fix,
or implementing a huge feature, it's worth keeping in mind that there
are usually orders of magnitude more users than there are contributors,
and an order of magnitude more contributors than there are maintainers.
As a result, maintainer time is highly oversubscribed. If you want to
increase the likelihood that your contribution goes somewhere
productive, you have to ensure that your contributions carry a high
signal-to-noise ratio and are worth the maintainers' time.

For example, a good bug report respects the maintainer's time by
providing everything needed to understand and reproduce the problem:

- **Environment**: OS, version numbers, relevant configuration
- **What you expected** vs **what actually happened**
- **Steps to reproduce**: Be specific. "Click the button" is less useful
  than "Click the Submit button on the /settings page while logged in as
  an admin."
- **What you've already tried**: This prevents duplicate suggestions and
  shows you've done some investigation

> If you find a security vulnerability, don't post it publicly. Contact
> the maintainers privately first and give them reasonable time to fix
> it before disclosure. Many projects have a SECURITY.md file or
> similar for this purpose.

**Make sure you search for existing issues.** Your bug or feature
request may already be reported, and it's far better to add information
to existing discussions rather than creating duplicates. Not to mention,
it reduces noise for the maintainers.

Minimal reproducible examples are gold, if you can come up with one.
They save the maintainer a huge amount of time and effort, and
reliably reproducing the bug is often the hardest part of fixing it. Not
to mention, the effort you put into isolating the problem often helps
you understand it better too, and sometimes leads you to find a fix
yourself.

If you don't hear back right away, keep in mind that maintainers are
often volunteers with limited time. If you're waiting for a reply from
them, a polite follow-up after a couple weeks is fine; daily pings are
not. Similarly, "me too" comments, or bug reports that are just a
copy-paste of some terminal output tend to be a net-negative in terms of
getting traction for your issue.

If you're looking to make a code contribution, you'll also want to
familiarize yourself with the contribution guidelines. Many projects
have a `CONTRIBUTING.md` — follow it. You'll also usually want to start
small; a typo fix or documentation improvement is a great first
contribution as it helps you learn the project's processes without also
having to go through lots of back and forth on the content.

> Check what license the project uses, as any code you contribute will
> fall under the same license. In particular, look out for copyleft
> licenses (like GPL), which requires derivatives to also be open source
> and may have implications for your employer if you touch it!
> [choosealicense.com](https://choosealicense.com/) has more useful
> information.

When you've decided to open a pull request ("PR"), first make sure you
isolate the change you actually want to be accepted. If your PR changes
lots of other unrelated things at the same time, chances are the
reviewer will send it back to you asking you to clean it up. This is
similar to how you should break down your git commits into semantically
related chunks.

In some cases, if you have many seemingly-disparate changes but
they're all needed to enable one feature, it may be okay to open a
larger PR that captures all the changes. However, in this case, commit
hygiene is particularly important so that maintainers have the option
to review the change "commit by commit".

Next, make sure you explain the "why" behind the change well. Don't just
describe _what_ changed — explain _why_ the change is needed and _why_
this is a good way to address the problem. You should also proactively
call out parts of the change that warrant special attention in the
review, if any. Depending on `CONTRIBUTING.md` and the nature of your
change, reviewers may also expect to see additional information like
trade-offs you made or how to test the change.

> We recommend contributing back to upstream projects rather than
> "forking" the project, at least as a first approach. Forking (license
> permitting) should be reserved for when the contributions you want to
> make are out of scope for the original project. If you do fork, make
> sure you acknowledge the original project!

AI makes it incredibly easy to generate plausible-looking code and PRs
quickly, but this doesn't excuse you from understanding what you're
contributing. Submitting AI-generated code you can't explain burdens
maintainers with reviewing and potentially maintaining code that even
its author doesn't understand. It's fine to use AI to help you
identify issues and produce fixes/features, **so long as you still do
the due diligence** to polish it into a worthwhile contribution, rather
than passing that work on to the (already-overloaded) maintainers.

Remember that for maintainers, accepting a PR means accepting long-term
responsibility. They will be maintaining this code long after the
contributor has moved on, and so may decline changes that are
well-intentioned but don't fit the project's direction, add complexity
they don't want to maintain, or where the need simply isn't sufficiently
well-documented. It's on _you_ as the contributor to make the case for
why the accepting the contribution is worth the maintenance burden.

> When receiving feedback on a PR, remember that your code is not you!
> Reviewers are trying to make the code better, not criticizing you
> personally. Ask clarifying questions if you disagree — you might learn
> something, or maybe they will.

## Reviewing

You might think code review is something senior developers do, but
you'll likely be asked to review code much earlier than you expect, and
your perspective is valuable. Fresh eyes catch things that experienced
developers overlook, and questions from someone less familiar with the
code often reveal assumptions that should be documented or simplified.

Review is also one of the fastest ways to learn. You'll see how others
approach problems, pick up patterns and idioms, and develop intuition
for what makes code readable. Beyond personal growth, reviews catch bugs
before they reach production, spread knowledge across the team, and
improve code quality through collaboration. They are not merely
bureaucratic overhead.

Good code review is a skill you need to hone over time, but there are
some tips that can make them much better much faster:

- **Review the code, not the person**:
  "This function is confusing" vs "You wrote confusing code."
- **Prefer actionable comments**:
  "Can you replace these globals with a config dataclass" is an easier
  comment to address than "Don't use globals here"
- **Ask questions rather than making demands**:
  "What happens if X is null here?" invites discussion better than
  "Handle the null case."
- **Explain the "why"**:
  "Consider using a constant here" is less useful than "Consider using a
  constant here so we can easily adjust the timeout based on
  environment."
- **Distinguish blocking issues from suggestions**:
  Be clear about what must change versus what's a matter of preference.
- **Acknowledge what's good**:
  Pointing out clever solutions or clean implementations is encouraging
  and helps the author know what to continue doing.
- **Know when to stop**:
  Contributors only have so much time and patience, and it's not always
  best spent handling all the nits. Focus on the big things, and
  consider tidying up nits yourself after the fact.

> AI tools can catch certain issues, but they're not a substitute for
> human review. They miss context, don't understand product
> requirements, and can confidently suggest wrong things. They're worth
> using as a first pass, but not a replacement for thoughtful human
> review.

# Education

A lot of our non-coding time as engineers is spent either asking or
answering questions, possibly a mixture of both; during collaboration,
in dialogue with peers, or while trying to learn. Asking good questions
is a skill that makes you better at learning from anyone, not just
perfect explainers. Julia Evans has some excellent blog posts on "[How
to ask good questions](https://jvns.ca/blog/good-questions/)" and "[How
to get useful answers to your
questions](https://jvns.ca/blog/2021/10/21/how-to-get-useful-answers-to-your-questions/)"
that are worth reading.

Some particularly valuable pieces of advice are:

- **State your understanding first**: Say what you think you know and
  ask "is that right?" This helps the answerer identify your actual
  knowledge gaps.
- **Ask yes/no questions**: "Is X true?" prevents tangential
  explanations and usually prompts useful elaboration anyway.
- **Be specific**: "How do SQL joins work?" is too vague. "Does a LEFT
  JOIN include rows where the right table has no match?" is answerable.
- **Admit when you don't understand**: Interrupt to ask about unfamiliar
  terms. This reflects confidence, not weakness. Similarly, if they ask
  questions of you that you do not know the answer to, it's best to say
  "I don't know", and possibly follow up with "but I think ..." or even
  "but I can find out".
- **Don't accept incomplete answers**: Keep asking follow-ups until you
  actually understand.
- **Do some research first**: Basic investigation helps you ask more
  targeted questions (though casual questions among colleagues are
  fine).

Remember: well-crafted questions benefit entire communities. They
surface hidden assumptions that others need to understand too.

> Note that this advice applies just as much when communicating with
> LLMs!

# AI etiquette

With the growing use of LLMs and AI across software engineering, the
social and professional norms around are still in flux. We already
covered many of the tactical considerations in the [agentic coding
lecture](/2026/agentic-coding/), but there are also "softer" parts of
their use that are worth discussing.

The first of these is that when AI meaningfully contributed to your
work, **disclose it**. This isn't about shame — it's about honesty,
setting appropriate expectations, and ensuring the resulting work gets
the appropriate level of review. It's also worthwhile to disclose which
_parts_ you use AI for — there's a meaningful distinction between "this
whole thing is vibecoded" and "I wrote this backup tool and used an LLM
to style the web frontend". For example, we've used LLMs to help write
some of these lecture notes, including proofreading, brainstorming, and
generating first drafts of code snippets and exercises.

You'll also want to follow the norms of the teams and projects you're
contributing to here. Some teams have stricter policies around the use
of AI than others (e.g., for compliance or data residency reasons), and
you don't want to accidentally run afoul of that. Being open about your
use helps prevent potentially costly mistakes.

> If you're aiming to learn as part of the work you're doing, keep in
> mind that if you have AI do all or most of the work for you can be
> self-defeating; you're likely to learn more about prompting (and maybe
> reviewing AI output) than the task itself. Especially when you're
> learning, the point may be the journey, not the destination, so using
> AI to "get the solution quickly" is an anti-goal.

A related concern comes up in interviews and other assessment
situations. These are often intended to specifically evaluate _your_
skills and abilities, not those of an LLM. More companies now allow you
to use LLMs and other AI-assisted tooling in interviews as long as you
let them observe those interactions as part of the interview (i.e., they
are evaluating your skill in making use of those tools too!), but those
are still in the minority. If you are unsure about whether AI assistance
is in scope for a particular task, ask!

> It should go without saying that if an assessment situation explicitly
> calls for no external tools, no LLMs, etc., you should not use them.
> Trying to do so discretely without getting caught **will** come back
> to bite you.

# Exercises

1. Browse the source code of a well-known project (e.g.,
   [Redis](https://github.com/redis/redis) or
   [curl](https://github.com/curl/curl)). Find examples of some of the
   comment types mentioned in the lecture: a useful TODO, a reference to
   external documentation, a "why not" comment explaining an avoided
   approach, or a hard-learned lesson. What would be lost if that
   comment was not there?

1. Pick an open-source project you're interested in and look at its
   recent commit history (`git log`). Find one commit with a good
   message that explains *why* the change was made, and one with a weak
   message that only describes *what* changed. For the weak one, look at
   the diff (`git show <hash>`) and try to write a better commit message
   following the Problem → Solution → Implications structure. Notice how
   much work is required to reassemble the necessary context after the
   fact!

1. Compare the READMEs of three GitHub projects with 1000+ stars. Are
   all of them equally useful? Look for things that come across mostly
   as noise to you as a lesson for future READMEs you write yourself.

1. Find an open issue on a project you use (check the "good first issue"
   or "help wanted" labels if they have it). Evaluate the issue against
   the criteria from the lecture: does it seem like it values the
   maintainer's time and contains all the information necessary to debug
   it, or do you expect that the maintainer may need to go multiple
   rounds of questions with the submitter to get to the root problem?

1. Think of a bug you've encountered in software you use (or find one in
   an issue tracker). Practice creating a minimal reproducible example:
   strip away everything unrelated to the bug until you have the
   smallest case that still demonstrates the problem. Write up what you
   removed and why.

1. Find a merged pull request on a project you're familiar with that has
   substantive review comments (not just "LGTM"). Read through the
   review. Were all the comments equally productive? If you were the PR
   author, how would you find the experience of getting all those
   comments?

1. Go to Stack Overflow and find a question in a technology you know
   that has a highly-voted answer. Then find one that was closed or
   heavily downvoted. Compare them against the advice from the lecture;
   was it predictable which question would get better answers?
