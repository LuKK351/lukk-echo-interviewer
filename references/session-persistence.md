# Session Persistence Reference

Use this reference whenever an interview starts, resumes, pauses, ends, may exceed short context, or involves save/export requests.

Do not let file work dominate the interview. Persistence is a recovery layer, not the user's task.

In clients that collapse tool/process messages, the next interview question must be the final visible response. Never put the user's next question only in a process message that may be collapsed after file writing finishes.

## Role

Session persistence has three jobs:

- Preserve enough context for long interviews.
- Keep the interview anchored to the material instead of drifting into the user's life story.
- Provide a reliable source for ending-stage article export.

It is not a note-taking product, writing workflow, or separate report format.

## Default Folder

When local file writing is available, prepare one session folder path by default:

```text
./lukk-echo-sessions/YYYY-MM-DD-HHMM-<material-slug>/
```

If the current working directory is not writable, use:

```text
$HOME/lukk-echo-sessions/YYYY-MM-DD-HHMM-<material-slug>/
```

If neither location is writable, continue the interview without file persistence and say so briefly.

Do not create an empty session folder before the user has a chance to disable saving when the environment allows you to wait. The first actual write can create the folder.

Rules:

- Do not hard-code `~/Documents`, `.codex/skills`, or a platform-specific path.
- Do not write to a hidden directory by default.
- Derive `<material-slug>` from the source title or filename.
- If no title or filename is available, use `untitled-material`.
- If the user gives a preferred folder, use it only if it is writable.

## Opening Prompt

After confirming the material and before the first interview question, explain the persistence mechanism once, then mention the planned save location.

The opening explanation should make these points in natural Chinese:

- The record exists because this skill may become a long interview.
- It preserves material anchors, questions already asked, the user's key wording, and article-ready material.
- It helps avoid context loss, repeated questions, and drift away from the source material.
- It also lets the user export an article later, only if the user confirms export.
- It is not a separate note-taking task, performance evaluation, surveillance, or a promise to publish anything.
- The user may change the folder or turn saving off.
- If the user directly answers the first interview question, treat that as consent to use the default save path.

Use this shape, adjusted to the actual material and path:

```text
这次访谈可能会聊得比较长，我会留一份轻量记录。它只做三件事：防止后面忘掉材料里的重点和你已经说清楚的内容；避免重复追问或被某个例子带跑；如果结束时你想导出文章，也能用你的原话和判断做素材。

记录会保存在：
<session-dir>

你可以直接回答下面的问题，直接回答就按默认保存继续；如果不想保存，或想换位置，现在告诉我就行。
```

If the user disables saving, do not create or update files in this session. If the user answers the first interview question without addressing saving, continue with default persistence.

If the user asks to change location and the new location fails, explain the failure and ask whether to use the default folder.

Do not repeat successful-save messages during the interview.

## Save Point Wording

Fixed save points are a recovery mechanism, not a user-facing event.

Do not announce save points with system-process wording, such as:

- "到第三个回答点了"
- "我会创建这次访谈的运行记录"
- "已运行命令"
- "我会把开场到这里的记录刷新到 interview.md"

Usually, save silently before the final visible response. If a transition is needed, use one short human sentence and continue the interview:

```text
我先把前面这段留个恢复点，然后继续问一个问题。
```

Do not explain file internals unless the user asks. Do not describe commands, turn counts, or implementation details.

## User-Visible Files

The session folder should contain at most two user-facing files: `interview.md` as the running interview record and recovery anchor, and `article.md` only after confirmed article export.

Do not expose extra state files as user-facing deliverables.

## interview.md Shape

Create or update `interview.md` with this shape:

```markdown
---
title: "<材料标题或文件名>"
source: "<材料路径、链接或用户描述>"
session_id: "<YYYYMMDD-HHMM-slug>"
created_at: "<ISO 时间>"
updated_at: "<ISO 时间>"
status: "active | paused | ended"
---

# <材料标题> 访谈记录

## 状态快照

- 材料地图：
- 当前锚点：
- 已覆盖锚点：
- 尚未触碰锚点：
- 锚点控制：入口锚点、进入方式、折返次数、冷却/封存状态
- 追问账本：
- 用户关键表达：
- 可用于文章的素材：
- 需要谨慎处理的点：
- 下一步最自然的问题：

## 对谈记录

### Turn 1

材料锚点：

AI 问题：

用户回答：

AI 回声：
```

## Snapshot Rules

The snapshot is for recovery, not for a polished summary.

Keep it short and factual:

- Material map: the source's main sections, claims, concepts, or scenes.
- Current anchor: the source anchor being explored now.
- Covered anchors: anchors already discussed and their depth.
- Untouched anchors: source anchors that should not be forgotten.
- Anchor control: entrance anchor, how each anchor entered the interview, repeat/fallback count, and any cooldown or sealed state.
- Question ledger: what has already been asked.
- User key expressions: preserve the user's own wording whenever possible.
- Article material pool: candidate judgments, examples, analogies, boundaries, titles, and open questions.
- Caution points: overextended analogies, weak evidence, unclear concepts, or places where AI should not overclaim.
- Next natural question: one concrete continuation question.

Do not rewrite user wording into polished assistant language.

## Transcript Rules

The user-facing question must remain visible after the turn finishes.

Append completed interview turns to `对谈记录` only at fixed save points. Do not decide based on whether writing seems quick. Persistence must never become a wait state on ordinary interview turns or hide the next question inside a collapsed process area.

Each turn should include:

- Turn number.
- Material anchor.
- AI question.
- User answer.
- Short AI echo or continuation note, only if useful for recovery.

The transcript may lightly clean formatting, but should preserve user wording.

## User-Facing Order

Do not make the user wait for persistence, and do not hide the next question in a collapsed tool/process area.

Preferred order after a user answer:

1. If this is an ordinary interview turn, do not write files. Make the final visible response a short echo plus one next question.
2. If this turn reaches a fixed save point, update `interview.md` before the final visible response.
3. After any save, make the final visible response the pause point, recovery point, or one next interview question.

Do not run file-writing tools after the final next question. In clients like Codex, that can cause the question to be grouped into the processed/tool area and collapse after completion.

If immediate writing is skipped, keep the turn in current context and flush it at the next fixed save point.

## Fixed Save Points

Final visible continuation outranks per-turn writing.

Ordinary one-question interview turns do not write files.

Flush pending turns and update the snapshot only when one of these fixed save points happens:

- Every 3 to 5 turns.
- The interview switches to another material anchor.
- The user switches to a different source material.
- An entrance anchor is sealed, cooled down, or hits non-consecutive over-depth.
- The user says "先到这里", "暂停", "结束", "收尾", or similar.
- The user explicitly asks to save,整理, output a record, or generate a report.
- The user gives a long answer that creates multiple article materials.
- The assistant notices two consecutive turns without returning to the source material.
- Before judging article export readiness.

Pause and end must flush `interview.md`.

Opening only prepares and announces the planned save location. Do not create an empty folder or write an empty `interview.md` at opening unless a fixed save point has been reached.

Do not tell the user every time the file is updated. Only mention file status at opening, failure, pause, and final export.

## Recovery

When continuing an existing interview, first read:

1. `interview.md` status snapshot.
2. The latest five turns.
3. Earlier key expressions or article material only if needed.

After reading, state the recovery point:

```text
我从记录里恢复到这里：我们已经聊过 <已覆盖内容>，上次停在 <当前材料位置>。接下来我会从 <下一问题方向> 继续。
```

Do not pretend to remember details outside the record. If the file does not contain something, say that the record does not contain it.

If `interview.md` is missing or damaged, say the session cannot be fully recovered and continue only from the current context.

## Switching Materials

When the user switches to a different source material mid-interview:

- Flush the current `interview.md` if file writing is available.
- Set the current session `status` to `paused`.
- Return the current material's pause point required by `SKILL.md`.
- Prepare a new session folder for the new material.
- Rebuild the material map and coverage ledger from the new material.

Do not mix two different source materials in one `interview.md`. If the user only switches sections, chapters, or anchors inside the same source, keep the same session and treat it as an anchor switch.

## Pause And End

When the user pauses or ends:

- Flush `interview.md`.
- Set `status` to `paused` or `ended`.
- Return the normal pause point required by `SKILL.md`.
- If article export is ready, mention the optional export capability after the pause point.
- If article export is not ready, say briefly that the record is saved and no article export is started.

Example when not ready:

```text
这次素材还不够形成一篇完整小短文，我就不启动导出。记录已经保存在 <interview.md>，下次可以接着问。
```

## Article Export Handoff

When the user confirms article export:

- Read `references/article-export.md`.
- Use `interview.md` as the source record when it exists.
- Write `article.md` in the active session folder when file writing is available.
- Return file paths instead of printing the whole article.

If file writing is disabled or unavailable, follow `references/article-export.md` console fallback.

## Failure Handling

If creating or updating files fails, say what failed in one short sentence, continue the interview, do not keep retrying every round, and use console output at final export if no file can be written.

If file persistence remains unavailable during a long interview, remind the user at most once every five additional turns, preferably at a state refresh point:

```text
文件保存仍不可用；本轮访谈记录目前只保留在当前对话上下文里。
```

Do not interrupt ordinary one-question turns just to repeat this warning.

## Failure Modes

The persistence layer fails if:

- It interrupts the interview with frequent file-status updates.
- The snapshot becomes a polished summary that overrides user wording.
- The record tracks only personal examples and loses material anchors.
- The assistant pretends to remember content not present in `interview.md`.
- File failure is hidden from the user.
- Ending-stage article export uses assistant summaries instead of user words.
