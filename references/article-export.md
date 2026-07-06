# Article Export Reference

Use this reference only during the ending stage when the user stops the interview or confirms article export.

Do not load or apply this reference during the normal interview loop. Interview questions must continue to follow `SKILL.md`.

## Role

Article export is an ending-stage output format.

It is not the main task of the skill. It does not change the interview into writing coaching.

Use it to turn what the user already said into a readable article. Do not use it to invent what the user did not say.

## Execution Order

Follow this order. If later rules conflict with earlier rules, earlier rules win.

1. Confirm this is the ending stage; never use article export during normal interview.
2. Run readiness check; if not ready, stop with a brief reason and do not ask more questions.
3. Offer export only as an optional capability after the pause point.
4. State one internal article theme; if there is no clear theme, do not export.
5. Select material for that theme; do not include every interview answer.
6. Write with traceable user meaning, clean obvious speech errors, then follow the output contract.

Priority stack:

- No invention outranks fluency.
- Clear article theme outranks covering all user answers.
- User meaning outranks literal wording.
- File output outranks console output only when writing works.

## Readiness Check

Offer article export only when all four conditions are true:

- At least one material anchor was explained by the user in their own words.
- The user expressed at least one original judgment, analogy, objection, boundary, application, or new question.
- The interview contains a recognizable expression line that can be stated as one clear article theme.
- The article can be supported mainly by the user's words, not by the assistant's reflections.

Do not offer article export when:

- The user mostly repeated the material or the assistant's wording.
- The user mostly discussed personal situations without tying them back to material anchors.
- The interview produced only impressions, feelings, or fragments.
- The available material can only be turned into a chronological interview recap.
- The assistant cannot state the article's theme in one plain sentence before writing.
- The article would require adding material anchors the user did not discuss.
- The article would rely mainly on assistant-written summary.

If not ready, say briefly why. Do not ask follow-up questions. Do not restart the interview.

Example:

> 本轮先停在这里。本次保留暂停点，但不提供文章导出，因为目前主要是材料印象，还没有形成一个能独立站住的用户判断。

## Ending Prompt

When the interview is ready for article export, do not expose internal routing labels such as "Single-Point Argument" or "单点论证型".

Do not say:

> 本轮访谈素材已经足够导出一篇文章。它适合走“单点论证型”：主线是……

This sounds like an internal scoring report and may make the user accept the assistant's frame before seeing the article.

Say it as an optional capability after the pause point:

> 上面的访谈内容已经可以整理成一篇小短文：以你刚才说出的理解为原料，保留你的口吻和关键表达，同时做必要的整理。需要我现在导出吗？

Prompt rules:

- Mention that article export is optional.
- Say it uses the user's interview material as raw material.
- Mention user voice, key expressions, examples, or necessary editing.
- Do not mention the route type.
- Do not announce the article's main line.
- Do not mention "article body + AI advice" in the prompt.

## Route Selection

Do not use one fixed article template.

Choose one route from this fixed route library based on the interview result.

Before choosing a route, write one internal sentence:

> This article is about: <one clear user-owned theme>.

If that sentence cannot be written plainly, do not export an article. Keep the pause point and say the material is not yet organized enough for an article.

## Selection Over Coverage

The article is not a transcript, recap, or complete stitching of every user answer.

Use only the material that serves the article theme. It is correct to omit user statements that are true but do not help the article stand up.

Before writing, sort interview material into three groups:

- Core: must appear because it carries the theme.
- Support: may appear if it clarifies the theme.
- Left out: true but not needed, repetitive, too fragmentary, or only useful for `AI 建议`.

If a sentence only exists because "the user said it", delete it. A paragraph must have a job: opening the material trigger, stating the user's judgment, explaining the reason, showing an example, naming a boundary, or ending where the user's thought stops.

Do not preserve interview order by default. Choose the order that makes the user's thought readable.

### Single-Point Argument

Use when the user clarified one core judgment and gave a reason, analogy, example, or boundary.

Shape:

- Title from the user's core judgment.
- Open with the material point that triggered the user's judgment.
- Explain the judgment in the user's language.
- Add the user's reason, analogy, example, or boundary.
- End only where the user's thought actually ended.

Do not pretend this covers the whole material.

### Multi-Point Synthesis

Use when the user covered several material anchors and explained their relationship.

Shape:

- Title from the user's overall understanding.
- Open with the user's map of the material.
- Organize each touched anchor in the user's logic order.
- Show the relationship between anchors.
- End with the user's strongest synthesis or remaining question.

Do not add untouched chapters or concepts.

### Critical Response

Use when the user mainly objected to, revised, or limited the material.

Shape:

- Title from the user's objection or revision.
- State the material claim only as far as the user discussed it.
- Present the user's objection.
- Use the user's reason, example, or boundary.
- End with the user's correction, condition, or unresolved tension.

Do not turn emotional disagreement into an argument.

### Question-Generating Note

Use when the user did not reach a conclusion but generated meaningful questions from the material.

Shape:

- Title from the strongest question.
- Open with what in the material produced the question.
- Group related questions.
- Explain why each question matters based on what the user said.
- End without forcing an answer.

No conclusion is better than a fake conclusion.

### Narrative-Anchored Reflection

Use when the material is centered on a person, event, story, controversy, or concrete case.

Shape:

- Title from the user's interpretation of the story or event.
- Give only the minimum story context the user already mentioned.
- Present what the user thinks is the key turn.
- Explain what this story reveals according to the user.
- End with the user's boundary, misreading warning, or open question.

Do not retell the whole source story unless the user already did.

### Application Note

Use when the user mainly explained how the material applies to a concrete scene.

Shape:

- Title from the user's application judgment.
- State the material point being applied.
- Describe the user's concrete scene.
- Explain how the material helps in that scene.
- Add any limits or risks the user mentioned.

Do not turn the user's scene into life advice.

## Voice Priority

The user's voice outranks the assistant's style.

Language priority:

1. User's clean meaning.
2. User's strongest original phrases.
3. Light cleanup in the user's voice.
4. Necessary connecting sentences.
5. Assistant wording.

The assistant may:

- Reorder material.
- Remove repetition.
- Add transitions.
- Add necessary context.
- Smooth spoken fragments.
- Clarify ambiguous references such as "this" or "it".
- Correct obvious typos, speech-to-text artifacts, duplicated words, false starts, and malformed phrases.
- Merge two broken spoken clauses into one readable sentence when the meaning is clear.

The assistant must not:

- Invent user opinions.
- Insert source summary as article body.
- Replace the user's plain wording with polished AI prose.
- Turn ordinary user language into slogans.
- Elevate personal scenes into life lessons.
- Add new arguments for completeness.
- Add a conclusion when the user did not reach one.
- Translate a vivid user phrase into smoother written prose when the original phrase already works.
- Add technical failure modes, examples, risks, or concepts that the user did not say.
- Preserve accidental wording that makes the sentence confusing.
- Include every user answer merely because it appeared in the interview.

## Speech Cleanup

Preserving user voice means preserving meaning, rhythm, and strong phrases. It does not mean preserving typos, voice-input errors, or broken spoken fragments.

Clean these without asking:

- duplicated subjects or words
- obvious speech-to-text errors
- mid-sentence restarts
- filler particles that make written Chinese clumsy
- malformed phrases where the intended wording is obvious

Example:

- Bad: `每个人、每个体，它有自己的品格`
- Good: `每个个体都有自己的品格`
- Also acceptable: `每个人都有自己的品格`

Do not over-clean into generic essay prose. Keep useful spoken flavor, such as `更灵活这三个字，它没有标准呀`, when it carries the user's thought.

## Source Traceability

Every substantive sentence in the article must trace back to one of these:

- A user sentence or phrase.
- A direct, minimal cleanup of a user sentence.
- A necessary connector that does not add a new claim.
- A source-material anchor that the user explicitly discussed.

If the assistant can only justify a sentence by saying "this follows from what the user said", keep it out of the article. Put it in `AI 建议` if it is useful.

Traceability is not literal copying. A cleaned sentence may be traceable even when it fixes wording, removes repetition, or corrects an obvious speech error.

Before output, run this internal check on each paragraph:

- Which user answer supports this paragraph?
- What job does this paragraph do for the article theme?
- Did the user say this, or did I infer it?
- If I removed assistant-written polish, would the user's point still be visible?
- Did I add a new example, risk, failure mode, or conclusion?

Delete or move any paragraph that fails this check.

## Anti-Polish Rules

The article should feel like the user's spoken understanding organized on paper, not like an assistant's finished essay.

Prefer:

- User's original short sentence.
- Slightly cleaned spoken rhythm.
- Concrete words the user used.
- A plain ending where the user's thought naturally stops.
- A short article with a clear theme over a longer article that includes every answer.

Avoid:

- Slogan endings.
- Symmetric closing lines.
- Over-complete argument chains.
- Chronological stitching of all interview turns.
- Paragraphs that repeat the interview order but do not build an article.
- Dramatic line breaks around weak or unclear phrases.
- Extra rhetorical questions not asked by the user.
- Phrases that sound like an article template.
- Reframing user examples into universal lessons.

If the user says "更灵活这三个字，它没有标准呀", keep that flavor. Do not automatically rewrite it into a polished thesis unless the user asks for polishing.

## Prohibited Contrast Pattern

Do not generate "不是 xxx，而是 xxx" style sentences unless the user used that pattern in their own answer.

Allowed:

- Keep or lightly clean this pattern if it appears in the user's original words.

Forbidden:

- Add "不是……而是……" as an assistant-created rhetorical pattern.
- Add similar variants such as "并不是……而是……", "真正的不是……而是……", or "核心不是……而是……".
- Add variants such as "不只是……更是……", "与其说……不如说……", "不是为了……而是……", or "表面上……本质上……".

If a contrast is needed, write it plainly without that pattern.

Before output, scan the article body for these strings:

- 不是
- 而是
- 不只是
- 更是
- 与其说
- 不如说
- 表面上
- 本质上

If any appear in assistant-created sentences, rewrite them plainly or remove them.

## Output Contract

When the user confirms article export, prefer writing `article.md` in the active session directory.

If `references/session-persistence.md` has created an active session and file writing is available:

- Use `interview.md` as the source record.
- Write the article and `AI 建议` into `article.md`.
- Return only file paths in the console.
- Do not print the full article in the console unless the user asks to see it.

Console response after successful file output:

```text
已导出：
访谈记录：<interview.md>
文章：<article.md>
```

If file writing is disabled, unavailable, or fails, fall back to console output and include both sections below.

### article.md Shape

When writing to file, use this shape:

```markdown
---
title: "<文章标题>"
source_session: "./interview.md"
created_at: "<ISO 时间>"
material_scope: "<只覆盖本轮访谈 / 覆盖整个会话>"
---

# <文章标题>

> 这篇文章只基于本轮访谈中你已经说出的内容，不覆盖整份材料。

<文章正文>

## AI 建议

- <建议 1>
```

If there is no `interview.md`, omit `source_session` and state the source as the current conversation.

### Console Fallback

When writing to file is not available, output two sections in the console.

First, start with:

> 这篇文章只基于本轮访谈中你已经说出的内容，不覆盖整份材料。

Then output the article.

Article rules:

- Use a title based on the user's core judgment.
- Make the opening establish one clear theme, not just restate the first interview answer.
- Do not title it "读《XX》有感".
- Do not describe the interview process.
- Do not include material anchors the user did not discuss.
- Do not include all user statements by default.
- Do not preserve confusing oral fragments, typos, or voice-input artifacts.
- Do not add conclusions the user did not say.
- Do not include AI advice in the article body.

### Section 2: AI 建议

Use this heading exactly:

## AI 建议

This section may include:

- An example that may be slightly off from the material.
- A judgment that may not stand strongly yet.
- A risk if the user publishes the article.
- Material anchors not covered.
- Hidden questions worth continuing.
- External directions worth checking.

Rules:

- Keep this section separate from the article.
- Do not rewrite AI suggestions back into the article unless the user asks.
- Use at most five bullets.
- If using knowledge outside the interview or source material, frame it as "可以考虑", "需要核实", or "可能延伸".
- For factual, current, legal, medical, financial, or other high-stakes claims, state that verification is needed.
- Do not build a new conceptual frame for the user.
- Do not create a new binary question or polished thesis for an untouched anchor.
- For unfinished anchors, simply name the anchor and why it may be worth returning to.

Good:

> 下一次可以回到材料里的 corrigibility，看它和品格判断之间是什么关系。

Avoid:

> 下一步最值得追的是：corrigibility 到底是外部限制，还是一种阶段性的品格。

## Failure Modes

The export fails if:

- The article becomes a source-material summary.
- The article is more complete than what the user actually said.
- The article sounds like generic AI prose instead of the user.
- AI advice leaks into the article body.
- The assistant fills in untouched material anchors.
- Every interview is forced into the same article route.
- The article hard-threads every user answer into one essay.
- The article has a catchy title but no clear theme.
- The article preserves obvious typos, speech-to-text errors, or broken spoken fragments as if they were style.
- The article line-breaks a weak fragment to make it look profound.
- The ending stage starts asking new interview questions.
- The article contains assistant-created "不是 xxx，而是 xxx" style sentences.
- The ending prompt exposes internal route labels or announces the article's main line before the user confirms.
- The article contains technical risks, failure modes, examples, or publishing conclusions that the user did not say.
- The article ends with assistant-made slogan lines instead of the user's own stopping point.
