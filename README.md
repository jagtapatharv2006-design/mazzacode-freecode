<div align="center">

# MazzaCode Freecode

**Free base code built with security in mind, so your AI agent starts from a careful base instead of a blank page.**

[![License: MIT](https://img.shields.io/badge/license-MIT-7DB61C?style=flat-square)](LICENSE)
[![Status: early build](https://img.shields.io/badge/status-early%20build-E07020?style=flat-square)](#roadmap)
[![Website](https://img.shields.io/badge/web-mazzacode.com-1E2327?style=flat-square)](https://mazzacode.com)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-7DB61C?style=flat-square)](#contributing)

[Website](https://mazzacode.com) · [Catalog for agents](https://mazzacode.com/catalog.md) · [Use a module](#build-a-module-with-your-agent) · [Modules](#modules) · [Report a bug](https://instagram.com/mazzacode)

</div>

---

## Why this exists

AI can build you a website in an afternoon. The trouble is what you cannot see: API keys pasted into the code, a database anyone can read, a sign-in page that looks fine but is not, user data stored with no thought for privacy law. If you cannot read the code closely, you cannot tell. And the careful version usually sits inside a $299 starter kit.

**MazzaCode Freecode is that careful base, free for everyone, under the MIT licence.**

The risky parts (sign-in, database access, secrets, personal data) come already built with security in mind and tested. Your AI coding agent (Claude Code, Cursor, Windsurf and others) builds on top of that base instead of improvising it from scratch, following a written procedure step by step, and a check command shows whether the setup works on your machine.

## Who it is for

- **Freelancers** shipping sites and apps for clients, who want a careful starting point instead of a blank page.
- **People in industry** building an internal tool or a product prototype, who want sensible security choices made from the start.
- **Non-coders** building their own website with AI and worried the code it writes is not safe. You do not need to write code: if you can open a folder in an AI agent and read a page of instructions, you can use a module.
- **Students and hackathon teams** who want to skip the plumbing and spend their time on the idea.

## How modules are built

These are the practices every module follows, so your agent does not have to invent them from scratch:

- **Secrets kept out of the code.** Modules read keys from `.env.local`, filled in from a commented `.env.example`.
- **Sign-in through Supabase Auth** with Google or GitHub, rather than home-made login code.
- **Row-level security switched on** for database tables.
- **Tested versions.** Each edition pins the package versions it was tested with.
- **Security assumptions written down.** Every `sop.md` says what the module is designed to handle and what is left to you.
- **Reviewed instructions.** Each `sop.md` is reviewed before publishing to keep out risky steps, such as piping a downloaded script into a shell or switching off a safety check.
- **Checksums.** Every zip comes with a SHA-256 checksum, so you can confirm the file is unchanged.
- **Privacy basics included.** See [Privacy built in](#privacy-built-in).

> [!WARNING]
> These are good practices, **not a security guarantee**. You are responsible for reviewing, testing and securing anything you deploy. Read the [Disclaimer](#disclaimer) before using any module.

> [!NOTE]
> **Early build.** This repo is being set up now. The first modules arrive with Library v0.1 in November 2026. Star or watch the repo to follow along.

---

## Modules

| Module | Edition | What you get | Status |
| --- | --- | --- | --- |
| **App starter** | 2026 | A bare-minimum Next.js + Supabase site with working sign-in, database and AI connection, plus a privacy page and consent checkbox ready to fill in | In progress |
| **RAG chatbot** | 2026 | Chat over your own documents, with the "answers are AI-generated" notice built in | Planned |
| **Voice agent** | 2027 | A voice agent that asks for recording consent and tells callers they are talking to an AI | Planned |
| **Copy-paste components** | — | Flowbite-style UI components, open on [mazzacode.com](https://mazzacode.com) with no sign-in | Planned |

The full, always-current list lives in [`catalog.md`](https://mazzacode.com/catalog.md).

---

## What is inside a module

| File or folder | What it is for |
| --- | --- |
| `sop.md` | The standard operating procedure: numbered steps your agent follows, in order, to build and set up the module |
| `context.md` | Why the module is built this way and what each part does. Your agent reads it before it starts |
| `CONTRACT.md` | The rules every MazzaCode module follows: folder layout, environment variable names, how checks work |
| Source code | The working module, MIT-licensed |
| Check command | A script, named in `sop.md`, that tests the build and says plainly whether it works |
| Seed data | Sample data, so the module shows something useful straight away |
| Demo mode | Runs the module without any API keys or paid services, so you can try it first |
| `.env.example` | Every setting the module needs, with a comment for each |
| `LICENSE` + `THIRD_PARTY_NOTICES.md` | The module's licence, and every piece of outside code it includes with that code's licence |

---

## Build a module with your agent

These steps use Claude Code. Cursor, Windsurf and other coding agents work the same way.

1. **Get the module** into a new, empty folder: download the zip from its page on [mazzacode.com](https://mazzacode.com), or copy its folder from this repo.
2. **Read `sop.md` yourself first.** It takes five minutes and tells you what the agent is about to do, including any commands it will run.
3. **Open the folder in your agent** and give it one instruction:

   ```text
   Read context.md, then follow sop.md step by step. Stop and ask me before any step
   that needs an API key, a paid service or my personal details. When you finish,
   run the check command and show me the result.
   ```

4. **Try demo mode first.** You get a working module without signing up for anything.
5. **Run the check.** It prints a pass or fail for each part. A full pass means every check in the module passed on your machine.
6. **Add your own keys** only when you are ready to go beyond the demo: copy `.env.example` to `.env.local` and fill in the values. Never paste keys into the agent's chat.
7. **Found a bug?** DM [@mazzacode on Instagram](https://instagram.com/mazzacode) with the module name, your operating system, your Node.js version and the failing line from the check.

### Let your agent choose

[`mazzacode.com/catalog.md`](https://mazzacode.com/catalog.md) lists every live module and component in plain text, with a one-line purpose and links. It is made for agents to read:

```text
Read https://mazzacode.com/catalog.md. I want to build <what you want>.
Which module or components fit, and why? Then read that module's sop.md and
tell me what it will need from me before we start.
```

---

## Repository layout

Planned layout. Paths mirror the website, so `library/2026/app-starter/sop.md` here is `mazzacode.com/library/2026/app-starter/sop.md` there.

```text
mazzacode-freecode/
├── CONTRACT.md                     # rules every module follows
├── catalog.md                      # plain-text list of modules, for agents
├── library/
│   └── 2026/
│       └── app-starter/
│           ├── sop.md              # step-by-step build procedure
│           ├── context.md          # why it is built this way
│           ├── .env.example        # every setting, commented
│           ├── LICENSE
│           ├── THIRD_PARTY_NOTICES.md
│           └── ...                 # source, seed data, check script
├── LICENSE
└── README.md
```

### Editions

Modules are released as **yearly editions** (App starter 2026, App starter 2027, and so on). Inside an edition, package versions are pinned to the ones that were tested. If your agent wants to upgrade a package, say no unless `sop.md` says upgrading is fine; newer versions can break the build. A new edition is where the stack moves forward.

---

## Staying safe with agents

An AI agent does what the files it reads tell it to, on your computer. Every module's instructions are reviewed before publishing, but reviews can miss things, and these habits help with any project:

- **Read `sop.md` before you hand it over.** Be wary of any step that pipes a downloaded script into a shell (`curl … | sh`), sends your files somewhere, or switches off a safety check. MazzaCode modules are written not to ask for these. If you see one, stop and DM [@mazzacode on Instagram](https://instagram.com/mazzacode).
- **Keep secrets out of chat.** API keys go in `.env.local`, never in the agent's chat window or in a file you commit.
- **Work in a fresh folder,** not one that holds your other projects or personal files.
- **Approve commands one at a time** until you trust what the agent is doing.
- **Check the SHA-256** if you got a zip from anywhere other than the module's Download tab.

---

## Privacy built in

Deploy a module that stores email addresses and you become responsible for that data. Under India's Digital Personal Data Protection Act, 2023 you are the "Data Fiduciary", with the main duties applying from May 2027. Most starter kits leave you to find this out later.

Every MazzaCode module ships a `## Compliance notes` section at the end of its `sop.md` listing what the module collects and what you need to do before launch. The agent is told to show you that list rather than tick it off itself. The App starter also includes:

- a placeholder privacy page at `/privacy` with a banner that stays until you fill in every `[bracket]`
- an unticked consent checkbox on sign-up (sign-in buttons stay disabled until it is ticked)
- a `consents` table migration with row-level security on
- a `delete-account` action, so users can remove their account and data

The compliance notes are general information, not legal advice.

---

## Roadmap

- [x] Name, domain and MIT licence
- [ ] `CONTRACT.md` and the first module (Library v0.1, November 2026)
- [ ] Module pages, `catalog.md` and copy-paste components on mazzacode.com
- [ ] Signed-in zip downloads with SHA-256 checksums (December 2026)
- [ ] v1.0 launch (December 2026)
- [ ] RAG chatbot 2026
- [ ] Voice agent 2027

---

## Contributing

**Found a bug?** DM [@mazzacode on Instagram](https://instagram.com/mazzacode) with the module name, your operating system, your Node.js version and the failing line. Ideas and module requests are welcome there too.

The rule for everything here: **nothing ships unless it works.** A module pull request is merged only when:

- it follows `CONTRACT.md`
- it keeps secrets in `.env.example` / `.env.local` only, turns row-level security on for every table, and writes its security assumptions in `sop.md`
- it ships `LICENSE`, `THIRD_PARTY_NOTICES.md` (with "This module contains no code copied from other projects." if that is the case) and a `sop.md` with a `## Compliance notes` section
- its check command passes in demo mode, with no API keys
- it contains no code copied from GPL or AGPL projects, which would conflict with MIT
- its `sop.md` never pipes a downloaded script into a shell, sends files elsewhere or switches off a safety check

### Security

Please do not post a security problem publicly. DM [@mazzacode on Instagram](https://instagram.com/mazzacode) instead.

---

## Disclaimer

MazzaCode modules are written with care for security and quality, but they are free code provided **"as is", with no warranty of any kind**, under the MIT licence. By using any module, you accept that:

- **Security is your responsibility.** No code is fully secure. You decide whether a module fits your project, review it (or have it reviewed) before relying on it, and keep it and its dependencies up to date.
- **Costs and rate limits are yours.** Bills from hosting, databases, AI models or any other service, including overruns, rate-limit hits, abuse of your endpoints or unexpected charges, are your responsibility. Set spending caps and rate limits on every service you connect.
- **Your data, your legal duties.** If your app collects personal data, you are responsible for it under the laws that apply to you. Compliance notes in modules are general information, not legal advice.
- **Only official copies are ours.** Modules are published only in this repo and on [mazzacode.com](https://mazzacode.com). A copy changed or shared by anyone else is not a MazzaCode module, and its notes and checks do not apply.
- **No liability.** The author and MazzaCode are not liable for any damage, data loss, security breach, downtime, cost or other harm arising from the use of this code, as set out in the MIT licence.

If you need guaranteed security, have a qualified professional review your deployment.

---

## Licence

Released under the [MIT licence](LICENSE), which provides the software "as is", without warranty. Each module also carries its own `LICENSE` and `THIRD_PARTY_NOTICES.md`.

<div align="center">

**Code should be as free as AI is.**

Built by Atharv Jagtap · [mazzacode.com](https://mazzacode.com) · [Instagram @mazzacode](https://instagram.com/mazzacode)

</div>
