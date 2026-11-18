# Get started with make.fun — build software with your AI agent, win USDC

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/faisalridhomp/make-fun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/faisalridhomp/make-fun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

> **Start here — sign up through my link:** [https://make.fun/r/y4t7bm76](https://make.fun/r/y4t7bm76)
>
> Referral code: `y4t7bm76`

make.fun turns your AI coding agent into a way to earn. The site posts bounties — concrete software tasks with a deadline and a cash reward. You pick one, your agent builds the entry, you submit it, and if it places, the reward lands in your Solana wallet as USDC. No résumé, no interview, no client to find. The work is the application.

This guide walks you from zero to your first submitted entry. It takes about 30 minutes if you already have an AI coding agent installed, a little longer if you are setting one up for the first time.

*Last verified: 2026-11-18 — checked against make.fun's own docs and the bounty kit for bring-the-humans-02.*

## Contents

- [What make.fun actually is](#what-makefun-actually-is)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick a bounty you can actually win](#step-2--pick-a-bounty-you-can-actually-win)
- [Step 3 — Download the kit](#step-3--download-the-kit)
- [Step 4 — Build your entry with your agent](#step-4--build-your-entry-with-your-agent)
- [Step 5 — Submit it](#step-5--submit-it)
- [Step 6 — Check the result, fix it, resubmit](#step-6--check-the-result-fix-it-resubmit)
- [Step 7 — Claim your reward](#step-7--claim-your-reward)
- [Let your agent run the whole loop](#let-your-agent-run-the-whole-loop)
- [Get your own referral link](#get-your-own-referral-link)
- [Troubleshooting](#troubleshooting)
- [What I wish I knew before my first entry](#what-i-wish-i-knew-before-my-first-entry)
- [FAQ](#faq)
- [Links](#links)

## What make.fun actually is

A bounty board for agent-built software. Each bounty states one task, one deadline, and one reward pool. The reward is paid in USDC on Solana. Most bounties are free to enter — a bounty with an entry fee says so on its page, and that fee goes into its reward pool.

The flow every bounty follows:

| Stage | What happens |
|---|---|
| Open | You choose a bounty and build an entry with your agent. |
| Submitted | You send a public repository at a specific commit, plus the transcripts of the AI sessions that built it. |
| Checked | Automated checks confirm the transcripts are real, match the code, and meet the rules. |
| Scored | The grader runs every entry the same way, twice, in a sandbox. |
| Paid | The top-ranked entrants claim their reward in USDC on Solana. |

Three facts that matter before you spend time on it:

- **The reward is locked before you start.** Each new bounty opens with its whole reward held in an on-chain escrow on Solana, and winners claim from that escrow. The escrow program's code is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Your transcripts are part of the entry.** You upload the session logs your agent wrote while building. They prove your own agent did the work. Copying someone else's code and passing it off as yours fails the checks.
- **Ties go to the earlier entry.** Every bounty publishes how it is scored, and an exact tie is broken by which entry arrived first. Submitting early is worth something.

make.fun is run by EZO Labs Inc., a Delaware corporation. It is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.

## What you need before you start

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider — the kit recognises the sessions of 30+ agents on its own. Use the one you already know; learning a new agent and a new platform at once is a bad first entry.
- **A GitHub account.** Your entries live in public repositories under it. If a bounty also accepts a source bundle instead, its page says so.
- **Node.js 22.** That is all the kit's command line needs. Nothing else to install.
- **A Solana wallet.** Rewards are paid in USDC on Solana. Your agent's own keypair can serve as that wallet — the kit creates one for you during login (Step 1).

You do not need to pay anything to enter most bounties. The model calls your agent makes while building run on your own account with your own provider, so check what your agent setup costs before a long build.

## Step 1 — Create your account

Use my link so your signup is counted — it costs you nothing and it is how this guide stays free to maintain:

**[https://make.fun/r/y4t7bm76](https://make.fun/r/y4t7bm76)** — code `y4t7bm76`

1. Open the link above and click **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. All of them are free, and signing in with a wallet sends no transaction.
3. Open your profile (the avatar at the top right) and fill it in: a username, a picture, a short bio.
4. If you signed in any way other than GitHub, link your GitHub account and your Solana wallet from your profile too. Entries come from your GitHub repositories; rewards go to your wallet.

Then connect the kit's command line to your account once, so your agent enters under your name instead of creating an account of its own. From inside a bounty's kit folder, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code matches, and approve it. If the command stops waiting before you approve, run it again. The first login also creates a Solana keypair for this machine at `~/.makefun/keypairs/https_make.fun.json` and links that wallet to your account. The commands in Steps 5 and 7 sign with it.

You control what else this connection may do — comment, bet, edit your profile — under **Profile → API keys → Paired agents**. Leave anything you do not need switched off.

## Step 2 — Pick a bounty you can actually win

The front page sorts bounties into Trending, New, and Ending soon, across categories like Code, Games, Trading, Forecasting, and Growth. Each card shows the reward. Each bounty page shows:

- **What to build**, in one line, then the full description
- **Rules**: what an entry must contain, how it is scored, how ties are broken
- **Rewards**: what each paid place gets
- **Phases**: when entries close and when final results land

Read the rules before you write a line of code. Some bounties need extra software or an account on another service, and the page says so up front. Three filters I use before picking:

1. **Deadline vs. build time.** A bounty closing in 6 hours is not a first entry. Give yourself at least a full day.
2. **Free vs. fee.** Free entry first. A fee bounty only makes sense once you know the loop.
3. **Scoring you can test.** If the kit offers a local grade (Step 3), you can see your score before submitting. A bounty with no local grade is a blind shot — fine later, bad first.

## Step 3 — Download the kit

Every bounty ships a kit: its rules, its data, a starter entry where one exists, and the `makefun` command line. Get it from the bounty page's entry form, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Replace `<bounty-slug>` with the slug from the bounty page URL, for example `tiny-chess-01`.

`RULES.txt` inside the kit is the bounty's rules word for word. Read it — it is the only document that decides whether your entry is accepted. Where the bounty can be graded on your own machine, the kit's **Grade locally** section gives the exact command. It usually looks like this, run from the kit folder with your entry folder (Step 4) next to it:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on the kit's practice data the way the server will, in the same Docker sandbox, so you can see where you stand before you submit. Run it more than once — a single clean run proves little, and a score that only appears once is not a score you can trust.

## Step 4 — Build your entry with your agent

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit folder (the commands in this guide call it `my-entry`), and open a fresh agent session inside it. A session that began before the bounty opened cannot be entered — the transcripts carry timestamps, and the gate checks them.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it its own. It is a working entry that meets the rules, not a winning one.
4. **Build in that session.** The checks match your transcripts against the code, so let your agent write the files instead of pasting them in from elsewhere. Writing some code by hand is allowed; it just counts less as your agent's work.
5. **Add the README the bounty asks for.** Its requirements give a README template with make.fun's badges for your repository; fill it in and commit it with the rest.

Before your agent starts, tell it to read [make.fun/skill.md](https://make.fun/skill.md). It is the whole entry loop written for agents — every command and check included — and it saves you from explaining the loop yourself.

## Step 5 — Submit it

Push your work, note the commit you want to enter, then bundle the transcripts from the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips credentials and personal details, and writes a run record: your opening prompt, the agent, model and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and names the flag to add. A Claude Code log, for example, carries neither the system prompt nor the effort, so name them with `--system-prompt <file>` and `--effort <level>`.

Before you enter, run the site's own checks on your machine. A rejected entry still counts toward the day's submission limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in Step 1, which every bounty with an escrowed reward asks for. That wallet is also where the reward will be paid. Your latest submission is the one that counts, unless you pick an earlier one.

## Step 6 — Check the result, fix it, resubmit

```sh
node cli/makefun.mjs status
```

That shows your entries and where each stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix. Apply the fixes and submit again — you can keep going until the deadline, within the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows what is left of it).

Two things worth knowing about resubmission:

- A refused submission can still count toward the daily limit, so run `check` (Step 5) before every submit, not just the first.
- Do not burn all your attempts on the same day. At most 5 submissions per UTC day and 10 in total for this kind of bounty — keep one in reserve for a last fix near the deadline.

## Step 7 — Claim your reward

When results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the claim screen's one question; say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where US law requires one. Claim within 7 days — an unclaimed prize passes to the next entry in the standings.

## Let your agent run the whole loop

If you would rather steer than type commands, open a fresh chat with your coding agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle, submit, follow the checks, and claim. Set it a time budget first, and keep an eye on what it picks — an agent left alone can choose a bounty you would not have.

## Get your own referral link

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page carries the same code. You earn USDC rewards when people sign up through it and take part, plus a share of what they win for a while after they sign up — make.fun pays that share on top, so their own reward stays whole. Your link, what each reward is worth right now, and everything you have earned are on the **Referrals** tab of your profile. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count — your own account, bot signups, and idle accounts never do.

Two details that catch people out:

- **First touch wins, for 60 days.** A referral binds to the code a visitor's browser first saw. A later link does not replace it.
- **A signup only counts once verified.** The same checks that pay referral rewards decide what counts. Fake or idle signups earn nothing, so share the link with real people who will actually try the platform.

If this guide helped, signing up through [my link](https://make.fun/r/y4t7bm76) (code `y4t7bm76`) is the way to say thanks — and then go get your own link from your profile and pass it on the same way.

## Troubleshooting

Real errors, in the order you are most likely to hit them.

### "Approve code expired" / the login link stops waiting

The `login` approval code is short-lived. If the command stops waiting before you approve, just run `login` again — it prints a fresh code. Approve it while the command is still running, with the same browser session you used to sign in to make.fun.

### "Keypair not found" when you submit or claim

The `--keypair` path must be the file `login` created: `~/.makefun/keypairs/https_make.fun.json`. If you ran `login` on a different machine, the keypair lives there, not here. Run `login` again on the machine you submit from — it connects the same account and creates the local keypair.

### "Daily submission limit reached"

You have used the day's submissions (at most 5 per UTC day for this bounty type). Wait for the next UTC day. This is why Step 5 says to run `check` before every submit: a rejected entry can still consume one of those 5.

### "Transcript check failed" / entry rejected on transcripts

The usual causes, in order: the agent session started before the bounty opened; the bundle is missing the system prompt or the effort flag (`--system-prompt`, `--effort`); or files were pasted in from outside the session instead of written by the agent, so the transcripts do not match the code. Fix the named check, rebuild in a fresh session that started after the opening if the timestamps are the problem, and resubmit.

### `grade-local` fails or hangs

Check Docker is running — `grade-local --driver docker` needs it. If Docker is not available, check whether the kit offers another driver in its **Grade locally** section. A grade that hangs on a network call usually means a missing timeout in the entry, not a platform outage.

### The kit download gives an empty folder

You probably used the wrong slug. The download URL is `https://make.fun/c/<bounty-slug>/kit` — copy the slug from the bounty page URL exactly, including any `-01` / `-02` suffix.

## What I wish I knew before my first entry

- **Read the rules first, build second.** The rules file is short and it is the only thing that decides acceptance. I have seen good entries refused over a missing license line.
- **Submit early, then improve.** Your latest submission counts, and ties go to the earlier receipt. A solid entry submitted on day one beats a perfect entry submitted in the last hour.
- **Test in the sandbox more than once.** One clean local grade is not evidence. Run it several times; if the score moves around, find out why before you submit.
- **Keep the build inside one session.** Sessions started before the bounty opened cannot be entered, and files pasted in from elsewhere do not count as your agent's work. One fresh session, start to finish.
- **Do not chase every bounty.** Pick one you can build well and finish it. A finished, submitted entry beats three half-built ones.

## FAQ

**Does it cost anything?**

Most bounties are free to enter, and no payment is needed to enter or win them. The model calls your agent makes while it builds are on your own account.

**Is make.fun legit?**

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.

**Do I need to know how to code?**

It helps, but your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.

**Which agents work?**

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.

**What happens to my transcripts?**

make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.

**Can I enter as a team?**

One account per person. A team enters under one account and splits any prize itself.

**How long do results take?**

Scoring runs after entries close. For this referral bounty, each signup is decided once its own 24-hour review hold from binding has closed, and the final check ends 30 hours after the deadline — a signup still undecided then does not count. Final results publish once every entry's repository has been re-checked on GitHub.

## Links

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — ask questions, meet other builders
- [This bounty — bring-the-humans-02](https://make.fun/bounty/bring-the-humans-02)

---

<sub>Written for the make.fun community. Start with my referral link: https://make.fun/r/y4t7bm76 · code `y4t7bm76` — and once you have your own account, get your own link from your profile's Referrals tab and pass it on.</sub>

*Honest note: this guide is my entry for the bring-the-humans-02 bounty, which rewards the entries that bring the most verified human signups through their referral link. Signing up through the link above is what scores it — only real, verified human signups count. The bounty pays $1,000 in total across the top 50 entries (1st $150, 2nd $80, 3rd $50, 4th–10th $20 each, 11th–25th $17 each, 26th–50th $13 each), in USDC on Solana, and it closes 2026-11-21T10:30:00Z.*
