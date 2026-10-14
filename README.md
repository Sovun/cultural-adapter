# Cultural Adapter

The cross-cultural adaptation for your content.

A [Claude skill](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) that adapts any text for readers from another culture and explains every change, so you learn that culture as you go.

## Features

- **Review and adapt.** Emails, chat messages, presentations, proposals, marketing copy, CVs, job ads, UI text. The skill detects the text type and the relationship with the reader, then returns a report (what changed, why, and lessons for next time) and an adapted copy in the same format as the original.
- **Decode.** Explains what a message from someone in another culture most likely means and how to reply.
- **20 cultures plus a generic profile.** See [Supported cultures](#supported-cultures). For any other culture, the skill offers the generic international profile or the nearest supported one.
- **Light on context.** Only `SKILL.md` loads when the skill starts. A culture profile is read only after the target culture is known.

## Supported cultures

| Culture | Locale | Region |
|---|---|---|
| Brazil | pt-BR | South America |
| China (mainland) | zh-CN | East Asia |
| Finland | fi-FI | Northern Europe |
| France | fr-FR | Western Europe |
| Germany | de-DE | Central Europe |
| India | en-IN | South Asia |
| Indonesia | id-ID | Southeast Asia |
| Israel | he-IL | Middle East |
| Japan | ja-JP | East Asia |
| Mexico | es-MX | Latin America |
| Netherlands | nl-NL | Western Europe |
| Nigeria | en-NG | West Africa |
| Poland | pl-PL | Central Europe |
| Saudi Arabia | ar-SA | Middle East (Gulf) |
| South Korea | ko-KR | East Asia |
| Türkiye | tr-TR | Southeast Europe / West Asia |
| Ukraine | uk-UA | Eastern Europe |
| United Arab Emirates | ar-AE | Middle East (Gulf) |
| United Kingdom | en-GB | Northern Europe |
| United States | en-US | North America |
| Generic international | - | Unknown or mixed audience |

Dimension scores for every culture are in [references/cultures/index.md](references/cultures/index.md).

## Installation

The skill is installed straight from this repository: <https://github.com/Sovun/cultural-adapter>. You need [Git](https://git-scm.com/downloads).

### Claude Code: all projects

Clone the repository into your personal skills folder:

```bash
git clone https://github.com/Sovun/cultural-adapter.git ~/.claude/skills/cultural-adapter
```

### Claude Code: one project

From the root of your project, clone it into the project's skills folder:

```bash
git clone https://github.com/Sovun/cultural-adapter.git .claude/skills/cultural-adapter
```

Restart Claude Code (or start a new session) and the skill is ready. Check that it is listed by asking Claude "what skills do you have?".

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
- "Review this presentation for our client in Saudi Arabia"
- "My German client replied with this. Is it a yes or a no?"

If you don't name a culture, the skill asks which one before it starts.

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
