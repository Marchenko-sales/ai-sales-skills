# AI Sales Skills

**An open library of Agent Skills for B2B sales.** Full cycle: segment prospecting → pre-outreach company dossier → decision-makers → cold outreach with follow-up cadence → qualification and objections → scrubbing AI clichés out of copy.

Every skill is battle-tested on real deals. Each one ships with instructions, a setup block for your product, and a worked input → output example.

> **Language note.** Skill bodies are written in Russian — they were built for a Russian-speaking sales team and the cold-email conventions of that market. Claude reads them natively: you can send requests in English and get results in whatever language you sell in. English skill bodies are on the roadmap; star the repo to vote for them. *[Краткое описание по-русски — внизу.](#по-русски)*

## Why this isn't "another prompt list"

- **Installs as a plugin.** [Agent Skills](https://github.com/anthropics/skills) format (Anthropic): a folder plus `SKILL.md`. The skill triggers itself when the task fits — no copy-pasting prompts into chat.
- **Full sales cycle.** Skills hand results to each other: the company dossier becomes the input for the outreach email, the email becomes the input for qualifying the reply.
- **A worked example in every skill.** Each folder has `ПРИМЕР.md` (example): one end-to-end fictional case — the same vendor and the same lead move through the whole library — with the structure and depth of a real working output. The data is invented on purpose: nothing from real deals leaves the building.
- **No paid services at the core.** Everything runs on Claude and the open web. The only optional paid step is an email verifier before sending to pattern-generated addresses, and you can skip it.

## Skills

| Skill | What it does | Status |
|---|---|---|
| [company-context](skills/company-context/) | Pre-outreach company dossier: legal entity, reputation, contact channels, current vendor in your category, buying signals with dates and links | ✅ |
| [segment-company-search](skills/segment-company-search/) | Finds candidate companies in a niche, verifies each against strict ICP criteria, saves a prioritized table | ✅ |
| [b2b-lead-contacts](skills/b2b-lead-contacts/) | Finds named decision-makers: roles, LinkedIn and Telegram, corporate email pattern with confidence levels | ✅ |
| [cold-outreach](skills/cold-outreach/) | First email / message plus a 4-touch follow-up cadence; CTA rules instead of dead closers; anti-template rules across contacts at one company | ✅ |
| [qualification-objections](skills/qualification-objections/) | Lead qualification (ICP / referral / decline), discovery questions, principles for handling price, timing, risk and incumbent-vendor objections | ✅ |
| [stop-slop-ru](skills/stop-slop-ru/) | Removes recognizable AI-writing patterns from Russian text; hard mode for cold outreach. Russian adaptation of [stop-slop](https://github.com/hardikpandya/stop-slop) | ✅ |
| company-profile | Builds your company context file: reads your website and materials on its own, fills the gaps with a short interview (uses connected services when available) | ⭐ unlocks at 50 stars |
| segment-research | Full market research as a multi-agent process: segment map → dossier per segment → competitors → messaging map → sales playbook → offer testing → audit. The process behind a real 18-segment study | ⭐⭐ unlocks at 100 stars |

## Install

**Claude Code** (personal skills, available in every project):

```bash
git clone https://github.com/Marchenko-sales/ai-sales-skills.git
cp -r ai-sales-skills/skills/* ~/.claude/skills/
```

For a single project only: copy the folders you need into `.claude/skills/` inside the project.

**Claude (web / desktop app):** paste the contents of a `SKILL.md` as project instructions or attach it to a request — the skills are written to work without installation too.

## Before you start: build a company profile file

Every skill opens by asking about your product, ICP and constraints. To answer once instead of every session, keep one Markdown file with your company context in the project — product and offer, ICP signals, competitor category, stop-niches, tone of voice — and the skills will read it themselves.

You can write that file by hand in half an hour. Or not: I'm preparing a separate skill, **company-profile**, that builds it for you — reads your website and materials on its own, then fills the gaps with a short interview. Want it? **Star the repo**: at 50 stars it ships here.

## How to use

Skills trigger on the task itself: "build a dossier on company X", "is this our lead?". The first thing a skill does is ask about your product and ICP if it doesn't know yet — the setup block lives inside each skill.

A working chain: `segment-company-search` finds 30 companies in a niche → `company-context` builds dossiers on the priority ones → `cold-outreach` writes the first email from the dossier → the lead's reply is handled by `qualification-objections` → every outgoing text passes through `stop-slop-ru` before sending. Each skill also works on its own.

## Author

Daniil Marchenko — CBDO at a fintech company. I build sales and business development on a "human + AI agents" pipeline and publish here what survived contact with real leads.

Telegram: [@stereonetip](https://t.me/stereonetip) · LinkedIn: [daniil-marchenko-sales](https://www.linkedin.com/in/daniil-marchenko-sales/)

Want these processes implemented in your team — from tuning the skills to your product up to a full market segmentation study — message me on [Telegram](https://t.me/stereonetip).

Questions and suggestions — [Issues](../../issues). If the library is useful, a star helps others find it.

## License

[CC BY 4.0](LICENSE) — use freely, including commercially, with attribution.

---

## По-русски

**Открытая библиотека AI-скиллов для B2B-продаж на русском языке.** Полный цикл: поиск компаний по сегменту → досье перед первым касанием → контакты ЛПР → холодное письмо с цепочкой follow-up → квалификация и возражения → чистка текста от ИИ-штампов. Каждый скилл обкатан в реальных сделках, у каждого — инструкция, настройка под ваш продукт и пример «вход → выход». Сами скиллы написаны по-русски; установка и описание — выше. Внедрение под ключ — в [Telegram](https://t.me/stereonetip).
