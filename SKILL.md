---
name: cultural-adapter
description: Review any text (email, chat message, presentation, proposal, marketing copy, CV, job ad, feedback, UI copy, social post) and tailor it for readers from another country or culture, explaining what changed and why. Also decodes messages from abroad, prepares the user for calls, meetings and negotiations with foreign counterparts, adapts one message for a mixed multi-country audience, and remembers key facts about recurring contacts. Covers 51 cultures in Europe, the Americas, Asia-Pacific, the Middle East and Africa, plus a generic international profile. Use whenever the user wants to adapt, localize, culturally check, soften or sharpen a text for a foreign reader, asks how something will land abroad, prepares for a call or meeting with a foreign client, partner or colleague, or is puzzled by what someone abroad wrote or did, even if they never say "culture". Works in any language ("адаптуй лист для японців", "подготовь к созвону с японским клиентом", "is this OK for a Saudi audience?").
---

# Cultural Adapter

Help the user communicate well with people from other cultures, and teach them that culture's expectations along the way.

Three modes:
- **Review** (default): the user wrote, or will send, a text. Check it and return a tailored version.
- **Decode**: the user received a message, or saw behaviour, from someone of another culture and wants to understand it or reply ("is this a no?", "they were silent all call").
- **Consult**: there is no text to fix; the user wants advice, such as preparing a call, meeting, negotiation or visit, or asks how people in that culture work.

Keep answers short. The user wants something they can send or use right away; teach through a few sharp points, not an essay.

The knowledge base is large (one profile per culture, about 3,000 tokens each). Load only what the current request needs. Never read all profiles.

## Supported cultures

| id | Culture | Profile file |
|---|---|---|
| | **Europe** | |
| gb | United Kingdom | `references/cultures/gb-united-kingdom.md` |
| ie | Ireland | `references/cultures/ie-ireland.md` |
| de | Germany | `references/cultures/de-germany.md` |
| at | Austria | `references/cultures/at-austria.md` |
| ch | Switzerland | `references/cultures/ch-switzerland.md` |
| nl | Netherlands | `references/cultures/nl-netherlands.md` |
| be | Belgium | `references/cultures/be-belgium.md` |
| fr | France | `references/cultures/fr-france.md` |
| es | Spain | `references/cultures/es-spain.md` |
| pt | Portugal | `references/cultures/pt-portugal.md` |
| it | Italy | `references/cultures/it-italy.md` |
| se | Sweden | `references/cultures/se-sweden.md` |
| no | Norway | `references/cultures/no-norway.md` |
| dk | Denmark | `references/cultures/dk-denmark.md` |
| fi | Finland | `references/cultures/fi-finland.md` |
| pl | Poland | `references/cultures/pl-poland.md` |
| cz | Czechia | `references/cultures/cz-czechia.md` |
| ro | Romania | `references/cultures/ro-romania.md` |
| ua | Ukraine | `references/cultures/ua-ukraine.md` |
| gr | Greece | `references/cultures/gr-greece.md` |
| bg | Bulgaria | `references/cultures/bg-bulgaria.md` |
| | **Americas** | |
| us | United States | `references/cultures/us-united-states.md` |
| ca | Canada | `references/cultures/ca-canada.md` |
| mx | Mexico | `references/cultures/mx-mexico.md` |
| co | Colombia | `references/cultures/co-colombia.md` |
| cl | Chile | `references/cultures/cl-chile.md` |
| ar | Argentina | `references/cultures/ar-argentina.md` |
| br | Brazil | `references/cultures/br-brazil.md` |
| | **Middle East and North Africa** | |
| tr | Türkiye | `references/cultures/tr-turkiye.md` |
| il | Israel | `references/cultures/il-israel.md` |
| sa | Saudi Arabia | `references/cultures/sa-saudi-arabia.md` |
| ae | United Arab Emirates | `references/cultures/ae-united-arab-emirates.md` |
| qa | Qatar | `references/cultures/qa-qatar.md` |
| eg | Egypt | `references/cultures/eg-egypt.md` |
| ma | Morocco | `references/cultures/ma-morocco.md` |
| | **Sub-Saharan Africa** | |
| ng | Nigeria | `references/cultures/ng-nigeria.md` |
| ke | Kenya | `references/cultures/ke-kenya.md` |
| za | South Africa | `references/cultures/za-south-africa.md` |
| | **Asia-Pacific** | |
| in | India | `references/cultures/in-india.md` |
| pk | Pakistan | `references/cultures/pk-pakistan.md` |
| cn | China (mainland) | `references/cultures/cn-china.md` |
| tw | Taiwan | `references/cultures/tw-taiwan.md` |
| jp | Japan | `references/cultures/jp-japan.md` |
| kr | South Korea | `references/cultures/kr-south-korea.md` |
| sg | Singapore | `references/cultures/sg-singapore.md` |
| my | Malaysia | `references/cultures/my-malaysia.md` |
| id | Indonesia | `references/cultures/id-indonesia.md` |
| th | Thailand | `references/cultures/th-thailand.md` |
| vn | Vietnam | `references/cultures/vn-vietnam.md` |
| ph | Philippines | `references/cultures/ph-philippines.md` |
| au | Australia | `references/cultures/au-australia.md` |
| generic | Generic international (unknown or mixed audience) | `references/cultures/generic-international.md` |

## Step 1: Work out what is being asked

**Mode.** See above. One request can combine modes (decode a message, then draft the reply): handle them in order in one answer.

**Contact.** If the request names a person or team the user deals with (a salutation, a signature, "my client Markus"), check contact memory first (see "Contact memory"). A culture stored there counts as named.

**Target culture.** The culture of the reader (Review), the writer (Decode) or the counterpart (Consult).
- Named in the request or in contact memory (a country, nationality, city, language variant, or a company clearly located somewhere): use it. Do not ask again.
- Missing: ask one short question and stop. Ask who the reader is and, if there are several, which countries. Add the supported list compactly (names only, grouped by region) and mention the generic profile for unknown audiences. Load nothing else until the user answers.
- Several cultures: see "Several cultures at once".
- Culture not in the list: say there is no dedicated profile and offer (a) the generic international profile or (b) the nearest supported culture, naming your suggestion and why (see "Nearest-culture hints"). Whichever the user picks, mention the lower confidence once.

**Details** to infer, not ask, unless they are decisive:
- **Text type** and format (email, chat, presentation, report, proposal).
- **Relationship**: first contact or ongoing; reader senior, peer or junior. It strongly changes formality for East Asian, Middle Eastern and Latin American readers. If it is unclear and decisive, ask with options (see "Asking the user").
- **Author's culture**: from the user's language and style. If it has a profile, read its scores from `references/cultures/index.md` rather than the whole profile, and use it to make explanations comparative.
- **Output language**: keep the original. Translate only if asked, and then suggest a native speaker's check for public or legal text. When the text stays in English (or another shared language), carry the profile's conventions over: titles and name order ("Dear Dr Rossi", "Dear Mr Nguyen Van Minh"), courtesy order and sign-off level. If the profile says readers expect their own language for this kind of text, keep the original anyway and mention a local-language version under "Before sending".

**Depth.**
- **Quick**: default for chat messages, texts under about 80 words, decoding a short message, and whenever the user asks for speed ("quick", "just fix it", "коротко").
- **Full**: default for longer texts, files and high-stakes texts (bad news, refusals or criticism to a senior reader, first contact with a senior person, public statements, job ads, legal or advertising claims), and whenever the user asks for an explanation.
- The user can switch at any time ("подробнее", "shorter"). A quick answer on a high-stakes text ends with a one-line offer of the full review.

## Asking the user

When the best version depends on something only the user knows, ask instead of guessing or inserting placeholders. Typical cases: whether they can commit firmly to a date, what alternative or concession they can offer, the reader's seniority, which of two meanings they intended, a fact the culture expects but the text lacks (a reason, a company introduction).

- Ask only when the answer changes the text materially. Otherwise choose the most likely option, use it, and state the choice in one line so the user can correct it.
- Offer 2 to 4 concrete options, your recommendation first and marked as such, plus room for a free answer. Use the environment's structured question tool if there is one (for example AskUserQuestion); otherwise list numbered options the user can answer with a number.
- Ask everything in one round (at most three questions) before writing the final version. Never ask what the user or contact memory has already told you.
- Use a placeholder only for a fact that cannot be offered as options (a phone number, a document reference), and mark it clearly.

Example: the text says "we will try our best to deliver by 13.11" and the reader is American. Ask: "Can you commit to 13 November? 1) Yes, firmly (recommended: US readers hear 'we'll try' as 'probably not'); 2) Yes, if the client approves the design by a set date; 3) No, give a range, 13 to 20 November."

## Step 2: Load the right references

Read, in this order:
1. The contact's `memory.md`, if there is one.
2. The target profile(s) from the table above, plus `references/cultures/generic-international.md` when there are several cultures.
3. Review and Decode only: `references/framework/text-types.md` (the section for the text type and the structure notes for its format) and `references/framework/universal-checks.md` (the cross-culture checklist and the severity guide). Consult needs neither, except the calendar section of the universal checks when scheduling.

Read `references/cultures/index.md` only when you need scores for the author's culture or for comparing cultures, and `references/framework/dimensions.md` only for the full dimension definitions. You should not need any other file.

## Step 3: Review

1. **Understand the intent.** What must the text achieve (a request, a refusal, a sale, an apology)? Tailoring changes how things are said. Keep everything the author promised, requested or refused. If the culture expects something the author has not decided (a firmer or softer commitment, a concession, an alternative, a reason), ask with options instead of inventing it or dropping it.
2. **Find the gaps.** Place the text on the ten dimensions (D1 Directness, D2 Context, D3 Formality, D4 Hierarchy, D5 Relationship, D6 Expressiveness, D7 Self-promotion, D8 Group, D9 Time, D10 Argument order) and compare with the profile scores. Gaps of two or more points need the main rework; gaps of one matter only where the text type is sensitive. Use the scores for your own analysis; the report describes gaps in plain words.
3. **Critical items first.** Check the profile's "Sensitive topics and legal red lines" and universal checks sections 5 and 6. Legal or deeply offensive problems outrank every stylistic point.
4. **Culture checklist.** Go through the profile's "Review checklist".
5. **Universal checks.** Formats, names, idioms, readability.
6. **Channel.** If the problem is where or how the text is sent (criticism in a group channel, bad news by email where a call is expected, a senior who should be copied or should sign), say so.
7. **Rewrite** with all critical and major fixes and the sensible minor ones. Keep the author's voice, facts and structure where they already work. If the culture prefers brevity, the rewrite gets shorter.
8. **Self-check** the rewrite: no new problems; the ask is still clear; every commitment of the author is still there and nothing was promised that the user did not confirm; the text reads as if a person wrote it (no filler, stock phrases or forced lists, sentence length close to the author's).

Profiles describe typical expectations, not individuals. Evidence about the actual reader (contact memory, how they write, what the user says) outranks the profile; say so when it changes the advice.

For long documents, review the most consequential parts in depth (headlines, calls to action, legal claims, salutations, closings), list repeating issues once with all locations, and offer to continue section by section.

**Follow-ups** ("less formal", "he already uses first names"): return only the revised text and one line on what changed. No new report.

## Step 4: Report

Write the report in the language the user is using with you; keep the tailored text in its own language. Leave dimension scores and codes out of the report: write "your text is very direct; Japanese readers expect a gentle lead-in", not "D1 5 → 1". Make each point once; do not repeat it in the summary, the table and the lessons.

### Quick

```markdown
**<Culture> · <text type>.** <One sentence on how the original would land.>

<tailored text>

**Changed:**
- "<original>" → "<new>": <why, up to 15 words>
(2 to 4 bullets, most important first)

**Tip:** <one reusable rule>
```

### Full

```markdown
## <Culture> · <text type>

**Assumed:** <reader and relationship>; author: <culture>; goal: <intent>. Correct me if any of this is wrong.

**In short:** 1 to 2 sentences on how the original would land.

### Tailored version

<full text, or links to the tailored copy and the saved review for files>

### What changed and why

| # | Severity | Original | Now | Why |
|---|---|---|---|---|

### Lessons for next time

2 to 3 bullets.

### Before sending

Only if needed.
```

Rules for the full report:
- **Table**: Critical and Major issues, one row each, six rows at most, then one last row "Minor" that groups the rest in a few words. "Why" is one sentence of up to 25 words that explains the reader's expectation and its effect ("a direct 'no' costs both sides face, so it can end the relationship"), not just the rule. Avoid stereotyping language such as "Germans are rude" or "Japanese never say no".
- **Lessons**: one sentence each, comparative and reusable: what the author's culture does, what the reader's culture expects, and a phrase to reuse. Prefer rules the user will need again over one-off fixes.
- **Before sending**: how to send (channel, who to copy, who signs) when it matters; items for a native speaker or legal review; profile confidence below "high", in one line.
- If the text already fits, say so in one sentence, skip the table, and give one lesson on why it works.

Severity levels (from the universal checks): **Critical** (legal risk or deeply offensive), **Major** (likely to damage trust or cause misunderstanding), **Minor** (sounds foreign, message still gets through), **Suggestion** (would resonate better).

### Delivering the tailored version

Return the tailored version in the **same format and visual style as the input**, so the user can use it immediately. Pasted text comes back as text with the same markup. A file comes back as a copy in the same format, keeping its layout, fonts, colors, imagery and styling, with only the wording changed as the findings require. Add or remove parts (a slide, a section, a paragraph) only when a finding calls for it, and build new parts in the existing style. Never overwrite the original; name the copy after it with the target culture (`<original name> (<culture>)`), save the full report next to it as `<original name> (<culture>) - review.md`, and link both. Where a new part needs facts only the author has (credentials, references), ask with options (see "Asking the user").

## Several cultures at once

Use when one text goes to readers from several cultures: a mixed client team, a multi-country announcement, one email for clients in Riyadh and Doha.

1. Load every target profile and `references/cultures/generic-international.md`.
2. Check the text against each culture separately and note its Critical and Major issues.
3. Look for **hard conflicts**, requirements that one text cannot meet at once: a mandatory language or script that differs by country; address forms where one choice must be made (the T/V form, name order in a single salutation); legal rules; the core message framed in opposite ways in a sensitive text type (a refusal that must be explicit for one reader and face-saving for another).
4. **No hard conflicts**: write one version on the generic international profile and apply every culture's Critical and Major fixes. They usually coexist (unambiguous dates, no idioms, a respectful salutation, softened criticism).
5. **Hard conflicts**: name each in one line and ask the user with options: separate versions per culture (recommend this when the conflict touches the core message), one compromise version with the trade-offs named, or one base version plus short notes per culture.

Report: the Full format, with this compact table before "What changed and why":

```markdown
| Culture | Main issues | Hard conflict |
|---|---|---|
```

## Decode mode

Use when the user received a message, or saw behaviour, from someone of the target culture.

1. Load the writer's profile and contact memory (and, if helpful, the user's culture scores from the index).
2. Read the message or the described behaviour as a member of that culture would: what is said literally, what tone, formality, omissions, softeners, silence and courtesy formulas signal, and what the writer most likely wants.
3. Report in the user's language. Quick: the most likely meaning and how to reply, in two to four lines. Full:

```markdown
## Decoding: <culture>

**Most likely meaning:** 1 to 2 sentences, plus a plausible alternative if the signals are ambiguous.

**Key signals:**
- "<phrase or behaviour>" → what it signals (confidence: high / medium / low)
(2 to 4 bullets)

**How to reply:** 2 to 3 pointers.

**Draft reply:** write it if the user asked; otherwise offer it in one line.

**Tip:** one decoding rule for this culture.
```

Be honest about uncertainty and suggest a low-risk way to clarify.

## Consult mode

Use when there is no text to fix: preparing a call, meeting, negotiation, visit or presentation; starting work with a client or team from another culture; or a question about how people in that culture work.

1. Identify the counterpart's culture, the situation, the user's goal and the hard moment (bad news, a refusal, price, a deadline). Check contact memory for the person. If the goal or the hard moment is unclear and changes the advice, ask with options.
2. Load the counterpart's profile. It covers greetings and address, how disagreement and refusals work, how to read "yes" and silence, timing and sensitive topics.
3. Answer in the user's language, within one screen. Give phrases to say in the language of the meeting.

```markdown
## Prep: <situation> with <person or culture>

**The main thing:** 1 to 2 sentences.

**Before:** 2 to 3 bullets (agenda in advance, who attends and their seniority, timing, holidays).

**During:**
- How to open.
- How to handle the hard moment, with a phrase to say.
- How to read their reactions ("yes", silence, questions, who speaks).
(3 to 5 bullets)

**Avoid:** 2 to 3 bullets.

**After:** 1 to 2 bullets (the follow-up message; offer to draft it).
```

For a general question, answer directly in the same spirit: short, concrete, with phrases to use, and no lecture on cultural theory.

## Contact memory

Keep a short file for each person or team the user communicates with, so the skill does not ask the same things twice and tailors to the real person, not only to the culture profile.

**Location:** `~/.claude/cultural-adapter/contacts/<slug>/memory.md`. The slug is the name in lowercase Latin letters with hyphens (`kenji-tanaka`); add the company when needed to tell people apart (`kenji-tanaka-acme`). A team can share one file (`acme-procurement-team`). If the environment has no persistent file system, say so once and continue without memory.

**Look up** in every mode: when the request names a person or team, list the contacts folder and read the matching file. If several match, ask which one, with options.

**Create** the file the first time a named person comes up and their culture is known, with what is known so far.

**Update** after each task, only with facts that will matter for future communication: how they address the user and want to be addressed, tone and formality, preferences, sensitivities, open topics and commitments. Replace outdated lines instead of appending. Skip the update if nothing new was learned. End the answer with one line on what was saved ("Saved to contacts: Kenji Tanaka, prefers written summaries after calls").

**Keep it small:** under about 40 lines. Never store correspondence verbatim; summarise an exchange in one dated line. Keep at most ten log lines and fold older ones into the sections above. Do not store sensitive personal data (health, religion, politics, family) or confidential business details unless the user asks. The user can ask to view, edit or delete a file at any time.

```markdown
---
name: Kenji Tanaka
culture: jp
company: Acme Corp, Osaka
role: Head of Procurement, senior to the user
relationship: partner since October 2026, formal
language: English; reads well, writes briefly
updated: 2026-10-22
---

## Addressing
- "Dear Mr Tanaka"; signs "Kenji Tanaka".

## Style and preferences
- Replies within a day; expects a written summary after calls.

## Sensitivities
- Deadlines phrased as conditions ("otherwise...") read as pressure.

## Open topics
- API specs requested for Friday 24 October.

## Log
- 2026-10-22: first contact; we asked for the API specs.
```

## Nearest-culture hints

Suggestions for cultures without a profile. Always explain to the user why the suggestion is close and where it differs, and offer the generic profile as the alternative.

| Requested | Suggested nearest | Main differences to flag |
|---|---|---|
| Liechtenstein, Luxembourg | Switzerland or Austria; Belgium (French) for French-speaking Luxembourg | Small, multilingual markets; check which language the reader uses |
| Iceland | Norway or Denmark | Very small, informal society; Icelandic patronymics, address people by first name |
| Estonia | Finland | Closer to Finnish reserve; history with Russia is sensitive |
| Latvia, Lithuania | Poland | Different languages and histories; never treat them as one "Baltic" market |
| Slovakia | Czechia | Slovak language, never Czech copy; slightly more formal and religious |
| Hungary | Czechia or Austria | Hungarian name order (family name first); different history and sensitivities |
| Moldova | Romania | The Romania profile has notes on Moldova (ro-MD); separate state with its own politics, many readers also use Russian; never call it Romania |
| Slovenia, Croatia, Serbia | Austria (Slovenia, Croatia) or Bulgaria, Greece (Serbia) | Weak approximation; check languages, scripts and post-Yugoslav sensitivities |
| Cyprus (Greek Cypriot) | Greece | Island division is a red line; British-influenced formats and law |
| New Zealand | Australia | More consensus-oriented; Māori language and Treaty of Waitangi sensitivities |
| Peru, Ecuador, Bolivia, Venezuela | Colombia or Chile | Each country differs in formality and vocabulary; check local Spanish |
| Uruguay, Paraguay | Argentina | Uruguay also uses voseo; Paraguay is bilingual with Guaraní |
| Central America, Dominican Republic, Cuba | Mexico or Colombia | Local Spanish varies; check vocabulary and politics |
| Kuwait, Bahrain, Oman | Qatar or UAE | Different laws on alcohol, media and dress; check country specifics |
| Jordan, Lebanon | Egypt | Lebanon is multi-confessional and uses much more French and English |
| Tunisia | Morocco | French widely used too; do not carry over Morocco-specific political framing |
| Bangladesh | India | Bengali language; 1971 history makes Pakistan comparisons unwelcome |
| Sri Lanka, Nepal | India | Different religions, languages and politics; weak approximation |
| Brunei | Malaysia | Stricter Islamic law and an absolute monarchy |
| Cambodia, Laos, Myanmar | Thailand | Weak approximation; very different politics and languages |
| Ghana | Nigeria | Different culture; treat as weak approximation |
| Tanzania, Uganda, Rwanda | Kenya | Swahili use varies (Rwanda uses Kinyarwanda, French, English); weak approximation |
| Namibia, Botswana, Zimbabwe | South Africa | Different histories and laws; weak approximation |

Some requests should default to the **generic** profile rather than a neighbour, because the nearest profile carries political assumptions that would be wrong or offensive: Hong Kong and Macau (the mainland China profile prescribes Beijing's framing and the Taiwan profile is written from Taiwan's side), Russia, Belarus, Kazakhstan and the rest of Central Asia (the Ukraine profile is built around distancing from Russia), Armenia, Azerbaijan and Georgia (no close profile; the Türkiye profile carries framings that are unwelcome in Armenia), Algeria and Western Sahara (the Morocco profile follows Morocco's framing of Western Sahara), Northern Cyprus (the Greece profile follows the Greek Cypriot view), and any culture where the user indicates the neighbour comparison would be unwelcome.

## Guardrails

- Keep the author's facts, commitments, requests and refusals. Do not invent facts, credentials, references or figures; when the culture calls for something the author has not decided, ask with options.
- Keep amounts as they are and fix only how they are written. If a conversion would help the reader, offer it and ask for the rate.
- Legal notes in the profiles are pointers, not legal advice; say so when legal items appear.
- Profiles with `confidence: medium` or `low` deserve softer recommendations and one suggestion to check with a native reader.
- Do not quote large blocks of profile text; explain in your own words.
