# Cultural Adapter

The cross-cultural adaptation for your content.

A [Claude skill](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) that adapts any text for readers from another culture and explains every change, so you learn that culture as you go.

## Features

- **Review and adapt.** Emails, chat messages, presentations, proposals, marketing copy, CVs, job ads, UI text. The skill detects the text type and the relationship with the reader, then returns the adapted text in the same format as the original, with a short explanation of what changed and why.
- **Quick or full answer.** Short texts and chat messages get a quick answer: the adapted text, a few key changes and one tip. Longer or high-stakes texts get a compact full review. Say "quick" or "in detail" to switch.
- **Decode.** Explains what a message (or behaviour, such as silence on a call) from someone in another culture most likely means and how to reply.
- **Consult.** Prepares you for a call, meeting or negotiation: how to open, how to handle the hard moment, how to read reactions, what to avoid, what to send afterwards.
- **Several cultures at once.** Checks one message against each reader's culture. If nothing conflicts, it writes one version on the generic international profile; if something does, it explains the conflict and lets you choose separate versions or a compromise.
- **Asks instead of guessing.** When the right wording depends on your decision (can you commit to that date? what can you offer instead?), the skill asks with ready-made options instead of leaving placeholders.
- **Contact memory.** Keeps a short note about each person you communicate with, so it doesn't ask the same things twice and adapts to the real person. See [Contact memory](#contact-memory).
- **51 cultures plus a generic profile.** See [Supported cultures](#supported-cultures). For any other culture, the skill offers the generic international profile or the nearest supported one.
- **Light on context.** Only `SKILL.md` loads when the skill starts. A culture profile is read only after the target culture is known.

## Supported cultures

| Culture | Locale | Region |
|---|---|---|
| Argentina | es-AR | Americas |
| Australia | en-AU | Asia-Pacific |
| Austria | de-AT | Europe |
| Belgium | nl-BE | Europe |
| Brazil | pt-BR | Americas |
| Bulgaria | bg-BG | Europe |
| Canada | en-CA | Americas |
| Chile | es-CL | Americas |
| China (mainland) | zh-CN | Asia-Pacific |
| Colombia | es-CO | Americas |
| Czechia | cs-CZ | Europe |
| Denmark | da-DK | Europe |
| Egypt | ar-EG | Middle East and North Africa |
| Finland | fi-FI | Europe |
| France | fr-FR | Europe |
| Germany | de-DE | Europe |
| Greece | el-GR | Europe |
| India | en-IN | Asia-Pacific |
| Indonesia | id-ID | Asia-Pacific |
| Ireland | en-IE | Europe |
| Israel | he-IL | Middle East and North Africa |
| Italy | it-IT | Europe |
| Japan | ja-JP | Asia-Pacific |
| Kenya | en-KE | Sub-Saharan Africa |
| Malaysia | ms-MY | Asia-Pacific |
| Mexico | es-MX | Americas |
| Morocco | ar-MA | Middle East and North Africa |
| Netherlands | nl-NL | Europe |
| Nigeria | en-NG | Sub-Saharan Africa |
| Norway | nb-NO | Europe |
| Pakistan | ur-PK | Asia-Pacific |
| Philippines | en-PH | Asia-Pacific |
| Poland | pl-PL | Europe |
| Portugal | pt-PT | Europe |
| Qatar | ar-QA | Middle East and North Africa |
| Romania | ro-RO | Europe |
| Saudi Arabia | ar-SA | Middle East and North Africa |
| Singapore | en-SG | Asia-Pacific |
| South Africa | en-ZA | Sub-Saharan Africa |
| South Korea | ko-KR | Asia-Pacific |
| Spain | es-ES | Europe |
| Sweden | sv-SE | Europe |
| Switzerland | de-CH | Europe |
| Taiwan | zh-TW | Asia-Pacific |
| Thailand | th-TH | Asia-Pacific |
| Türkiye | tr-TR | Middle East and North Africa |
| Ukraine | uk-UA | Europe |
| United Arab Emirates | ar-AE | Middle East and North Africa |
| United Kingdom | en-GB | Europe |
| United States | en-US | Americas |
| Vietnam | vi-VN | Asia-Pacific |
| Generic international | - | Unknown or mixed audience |

Dimension scores for every culture are in [references/cultures/index.md](references/cultures/index.md).

## Installation

The skill is installed straight from this repository: <https://github.com/Sovun/cultural-adapter>. You need [Git](https://git-scm.com/downloads).

Claude Code loads skills from two folders:

| Scope | Folder |
|---|---|
| All your projects | `~/.claude/skills/` |
| One project (can be committed and shared with the team) | `.claude/skills/` in the project root |

The skill folder must be named `cultural-adapter` and contain `SKILL.md` at its top level.

### Claude Code: all projects (recommended)

Clone the repository into your personal skills folder:

```bash
git clone https://github.com/Sovun/cultural-adapter.git ~/.claude/skills/cultural-adapter
```

### Claude Code: one project

From the root of your project, clone it into the project's skills folder:

```bash
git clone https://github.com/Sovun/cultural-adapter.git .claude/skills/cultural-adapter
```

### Alternative: skills CLI

If you have Node.js, the [skills](https://skills.sh) CLI does the same in one command:

```bash
npx skills add Sovun/cultural-adapter
```

### Check the installation

Start a new Claude Code session and ask "what skills do you have?". `cultural-adapter` should be in the list. You can also call it directly with `/cultural-adapter`.

### Updating

Pull the latest version from the same folder you cloned into:

```bash
git -C ~/.claude/skills/cultural-adapter pull
```

### Claude.ai and Claude Desktop

1. On the repository page, click **Code → Download ZIP**.
2. Unzip it and rename the folder to `cultural-adapter`, then zip that folder again.
3. In Claude, open **Settings → Capabilities → Skills**, click **Upload skill** and select the ZIP.

## Usage

Ask in any language. For example:

- "Adapt this email for our Japanese partner. It's our first contact: ..."
- "Quick, fix this Slack message to our developer in India: ..."
- "Review this presentation for our client in Saudi Arabia"
- "My German client replied with this. Is it a yes or a no?"
- "Prepare me for tomorrow's call with our Japanese client. We have to tell them the release is late."
- "Check this announcement for our teams in Poland, India and the US"

If you don't name a culture, the skill asks which one before it starts. If the right wording depends on your decision, it asks with options, for example:

> Can you commit to 13 November?
> 1. Yes, firmly (recommended: US readers hear "we'll try" as "probably not")
> 2. Yes, if the client approves the design by a set date
> 3. No, give a range, 13 to 20 November

### Example

**Request:**

> Adapt this for Mr Tanaka, a new partner in Osaka. First contact. We're writing from our Berlin office:
>
> *Hi Kenji, we need your API specs by Friday, otherwise we can't start the integration. Let me know ASAP. Thanks, Frank*

**Result (full review, shortened):**

> ## Japan · business email
>
> **Assumed:** reader: new partner, first contact; author: German (you mentioned the Berlin office); goal: get the API specs by Friday. Correct me if any of this is wrong.
>
> **In short:** The request is clear, but to a Japanese reader it sounds like an order from a stranger. It needs a formal greeting, a short introduction and a softer ask. The Friday deadline stays.
>
> ### Tailored version
>
> > *Dear Mr Tanaka,*
> >
> > *My name is Frank, and I lead the integration project on our side. We are very glad to begin working with your team.*
> >
> > *Would it be possible to receive your API specifications by Friday, 24 October? This would allow us to start the integration on schedule.*
> >
> > *Thank you very much for your support. I look forward to working with you.*
> >
> > *Kind regards,*
> > *Frank*
>
> ### What changed and why
>
> | # | Severity | Original | Now | Why |
> |---|---|---|---|---|
> | 1 | Major | "Hi Kenji" | "Dear Mr Tanaka" | First names are for close relationships; in a first email, title and family name show respect. |
> | 2 | Major | "otherwise we can't start" | "so that we can start the integration on schedule" | A condition reads as a threat; a shared goal keeps the deadline without the pressure. |
> | 3 | Minor | "ASAP", no introduction | removed; short introduction added | Urgency words sound careless in a first contact, and the date already sets the timing. |
>
> ### Lessons for next time
>
> - A German email gets to the point in the first line; a first email to a Japanese partner introduces you and your company before the ask.
> - Keep deadlines, but give the reason behind them: "so that we can..." works better than "otherwise...".
>
> Saved to contacts: Kenji Tanaka (Japan, new partner, formal).

A short chat message gets a quick answer instead: the adapted text, two to four key changes and one tip.

## Contact memory

The skill keeps a short note about each person or team you communicate with, in `~/.claude/cultural-adapter/contacts/<name>/memory.md`. The note is created the first time a person comes up and updated when something new and useful turns up: how they like to be addressed, their tone, preferences, sensitivities and open topics, plus a short dated log.

It never stores your correspondence word for word, keeps each note under about 40 lines, and leaves out sensitive personal data unless you ask. Notes are plain Markdown: read, edit or delete them any time, or ask the skill to. What the note says about the real person outranks the general culture profile.

Memory needs a persistent file system, so it works in Claude Code. In Claude.ai the skill works without it.

## Repository structure

```text
SKILL.md                    workflow, supported cultures, report format
references/cultures/        one profile per culture, index.md, _template.md
references/framework/       dimensions, universal checks, text types
```

## Adding a culture

1. Copy `references/cultures/_template.md` to `references/cultures/<iso>-<name>.md` and fill in every section.
2. Keep the frontmatter scores and the dimension table in sync.
3. Add the culture to the table in `SKILL.md` and to [Supported cultures](#supported-cultures) in this README.

## Limitations

- Profiles describe typical expectations, not individuals.
- Legal notes are pointers, not legal advice.
- Profiles marked `confidence: medium` or `low` should be checked by a native reader.

## License

[MIT](LICENSE)
