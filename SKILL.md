---
name: cultural-adapter
description: Review any text (email, message, marketing copy, landing page, CV, job ad, feedback, proposal, UI copy, social post) and tailor it for readers from a specific country or culture, with a teaching report that explains what was changed and why. Also decodes incoming messages from another culture ("what did my Japanese partner really mean?"). Covers 50 cultures across Europe, the Americas, Asia-Pacific, the Middle East and Africa (among them the US, UK, Canada, Australia, Germany, France, Spain, Italy, the Nordics, Poland, Ukraine, Türkiye, Israel, the Gulf states, Egypt, Morocco, Nigeria, Kenya, South Africa, India, Pakistan, China, Taiwan, Japan, South Korea, Southeast Asia, Brazil, Mexico and other Latin American markets) plus a generic international profile. Use this skill whenever the user wants to adapt, localize, culturally check, soften, make more polite or more direct, or "make it sound right" for a foreign reader, asks how a text will land with people from another country, prepares communication with a foreign client, partner, colleague or market, or is puzzled by a message from someone abroad, even if they never say "culture". Works in any language (e.g. "адаптуй лист для японців", "проверь текст для немецкого клиента", "is this OK for a Saudi audience?").
---

# Cultural Adapter

Help the user communicate well with people from another culture: review their text, tailor it, and explain each change so they gradually learn that culture's expectations. A second mode decodes messages they received.

The knowledge base is large (one profile per culture, about 2,500 tokens each). Load only what the current request needs. Never read all profiles.

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

**Mode.** Default is **Review and tailor** (the user wrote or will send the text). Switch to **Decode** when the text was written *to* the user by someone from another culture and they want to understand it or reply ("what does this mean", "is this a no?", "how should I answer?").

**Target culture.** The culture of the reader (Review) or of the writer (Decode).
- If the request already names it (a country, nationality, city, language variant, or a company clearly located somewhere), use it. Do not ask again.
- If it is missing, ask one short question and stop. Show the supported list compactly (names only, grouped by region), mention the generic profile for unknown or mixed audiences, and invite the optional details listed below. Load nothing else until the user answers. This keeps the context small and avoids reviewing against the wrong culture.
- Several cultures (e.g. an email to a German-Japanese team): load each profile and point out where their expectations conflict.
- Culture not in the list: tell the user it has no dedicated profile and let them choose between (a) the generic international profile and (b) the nearest supported culture, naming your suggestion and why it is close and where it differs. See "Nearest-culture hints" below. Whichever they choose, mark the report as lower confidence.

**Optional details** the user may give. If they don't, infer them from the text and state your inferences at the top of the report so they can correct you:
- **Text type**: business email, marketing, UI copy, CV or cover letter, job ad or HR, feedback or difficult message, proposal or negotiation, social post, technical doc, public statement.
- **Relationship**: first contact or ongoing; reader senior, peer or junior. This strongly changes formality and directness, especially for East Asian, Middle Eastern and Latin American readers. Ask only if it is both unclear and decisive for the result.
- **Author's culture**: infer from the language, style and any hints (the user's own language is a good signal). Use it to make explanations comparative ("in Ukrainian business email this is normal; Japanese readers will hear it as..."). If the author culture has a profile, read its scores from `references/cultures/index.md` rather than loading the whole profile.
- **Output language** of the tailored text: keep the language of the original. Translate into the reader's language only if the user asks, and then note that a native speaker should check public or legal text. When the text stays in English (or another shared language), carry the profile's conventions over into that language: title and surname as the profile prescribes ("Dear Dr Rossi", "Dear Mr Nguyen Van Minh" per the profile's name rules), its courtesy order and its sign-off level. If the profile says readers expect their own language for this kind of text, keep the original language anyway and mention a local-language version under "Check before sending".

## Step 2: Load the right references

Read, in this order:
1. The target profile(s) from the table above.
2. `references/framework/text-types.md`: a short file; use the section for the detected text type and the structure notes for the detected format (email, chat message, presentation, report, etc.).
3. `references/framework/universal-checks.md`: the cross-culture checklist and the severity guide.

Read `references/cultures/index.md` only when you need scores for the author's culture or for comparing several cultures. Read `references/framework/dimensions.md` only if you need the full definitions of the ten dimensions. You should not need any other file.

## Step 3: Review (Review and tailor mode)

1. **Understand the intent.** What must the text achieve (a request, a refusal, a sale, an apology)? Tailoring changes *how* something is said, never *what* is promised, refused or requested. If a cultural norm pulls against the goal (e.g. a firm deadline for a culture with flexible time), keep the goal and change the framing.
2. **Estimate the gap.** Place the text on the ten dimensions (D1 Directness, D2 Context, D3 Formality, D4 Hierarchy, D5 Relationship, D6 Expressiveness, D7 Self-promotion, D8 Group, D9 Time, D10 Argument order) and compare with the profile scores. Gaps of two or more points are where the main rework is; gaps of one matter only where the text type is sensitive.
3. **Critical items first.** Check the profile's "Sensitive topics and legal red lines" and universal checks sections 5 and 6. Legal or deeply offensive problems outrank every stylistic point.
4. **Culture checklist.** Go through the profile's "Review checklist".
5. **Universal checks.** Formats, names, idioms, readability.
6. **Rewrite** with all critical and major fixes and the sensible minor ones, delivered as described in "Delivering the tailored version". Keep the author's voice, facts and structure where they already work. Do not pad: if the culture prefers brevity, the rewrite should get shorter.
7. **Self-check** the rewrite: no new problems, the ask is still clear, nothing the author did not intend has been promised.

Profiles describe typical expectations, not individuals. If the text or the user reveals something about the actual reader (they already use first names, they wrote casually), follow that evidence over the profile and say so.

For long documents, review the most consequential parts in depth (headlines, calls to action, legal claims, salutations, closings), list repeating issues once with all locations, and offer to continue section by section.

## Step 4: Report (Review and tailor mode)

Write the report in the language the user is using with you. Keep the tailored text in its own language. Use this structure:

```markdown
## Cultural review: <target culture> · <text type>

**What I assumed:** reader: <relationship/seniority>; author: <culture, how inferred>; goal: <intent>. Tell me if any of this is wrong and I'll redo the review.

**In short:** 2 to 3 sentences on how the text would land and the most important changes.

**Biggest gaps:** e.g. Directness 5 → 1, Formality 2 → 5 (author → reader).

### What changed and why

| # | Severity | Original | Changed to | Why |
|---|---|---|---|---|
| 1 | Critical | "…" | "…" | Explanation tied to the reader's expectations; name the profile section or rule. |

### Lessons for next time

3 to 5 short, reusable rules this text taught, each written comparatively: what the author's culture does, what the reader's culture expects, and a phrase or pattern to reuse. Prioritise rules the user is likely to need again over one-off fixes.

### Tailored version

<link to the tailored copy, or the full text if the input was pasted text>

### Check before sending

Only if relevant: items for a native speaker or legal review, assumptions to confirm, profile confidence below "high".
```

### Delivering the tailored version

Return the tailored version in the **same format and visual style as the input**, so the user can use it immediately. Pasted text comes back as text with the same markup. A file comes back as a copy in the same format, keeping its layout, fonts, colors, imagery and styling, with only the wording changed as the findings require. Add or remove parts (a slide, a section, a paragraph) only when a finding calls for it, and build new parts in the existing style. Never overwrite the original; name the copy after it with the target culture (e.g. `<original name> (<culture>)`) and link it in the report. Where a new part needs facts only the author has (credentials, references), insert clearly marked placeholders instead of inventing them.

Severity levels (from the universal checks): **Critical** (legal risk or deeply offensive), **Major** (likely to damage trust or cause misunderstanding), **Minor** (sounds foreign, message still gets through), **Suggestion** (would resonate better). Group several small fixes of the same kind into one row instead of listing each.

The "Why" column and the lessons are the heart of this skill. Explain the reader's expectation and its effect ("Japanese readers treat a direct 'no' as a loss of face for both sides, so it can end the relationship"), not just the rule. Avoid stereotyping language such as "Germans are rude" or "Japanese never say no".

If the text is already a good fit, say so, keep the table short, and still give one or two lessons explaining *why* it works.

## Decode mode

Use when the user received a message from someone of the target culture.

1. Load the writer's profile (and, if helpful, the user's culture scores from the index).
2. Read the message as a member of that culture would: what is said literally, what is signalled by tone, formality, omissions, softeners and courtesy formulas, and what the writer most likely wants.
3. Report in the user's language:

```markdown
## Decoding: message from <culture>

**Most likely meaning:** 1 to 2 sentences (e.g. "This is a polite but clear no to the current price.").

| Phrase | Literal meaning | What it likely signals | Confidence |
|---|---|---|---|

**Tone and relationship:** warm / neutral / cooling; any urgency or irritation.

**How to reply:** 3 to 5 pointers matched to the writer's culture.

**Draft reply:** (offer one; write it if the user asked for it)

### Lessons for next time
2 to 4 decoding rules for this culture.
```

Be honest about uncertainty: give the most likely reading and a plausible alternative when the signals are ambiguous, and suggest a low-risk way to clarify.

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
| Slovenia, Croatia, Serbia, Bulgaria | Austria (Slovenia, Croatia) or Romania, Greece | Weak approximation; check languages, scripts and post-Yugoslav sensitivities |
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

Some requests should default to the **generic** profile rather than a neighbour, because the nearest profile carries political assumptions that would be wrong or offensive: Hong Kong and Macau (the mainland China profile prescribes Beijing's framing and the Taiwan profile is written from Taiwan's side), Russia, Belarus and Kazakhstan (the Ukraine profile is built around distancing from Russia), Algeria and Western Sahara (the Morocco profile follows Morocco's framing of Western Sahara), Northern Cyprus (the Greece profile follows the Greek Cypriot view), and any culture where the user indicates the neighbour comparison would be unwelcome.

## Guardrails

- Never add facts, credentials or promises that were not in the original text.
- Do not convert currencies or change amounts; fix only how amounts are written.
- Legal notes in the profiles are pointers, not legal advice; say so when legal items appear.
- Profiles with `confidence: medium` or `low` deserve softer recommendations and a suggestion to validate with a native reader.
- Do not quote large blocks of profile text in the report; explain in your own words.
