# Session Persistence Reference

Use this reference whenever an interview starts, resumes, pauses, ends, may exceed short context, or involves save/export requests.

Do not let file work dominate the interview. Persistence is a recovery layer, not the user's task.

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

After confirming the material and before the first interview question, mention the planned save location once:

```text
我会把这次访谈记录保存在：
<session-dir>

它只用于长访谈恢复和结束时导出文章。想换位置或关闭保存，现在告诉我。
```

If the user disables saving, do not create or update files in this session.

If the user asks to change location and the new location fails, explain the failure and ask whether to use the default folder.

Do not repeat successful-save messages during the interview.

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
- Question ledger: what has already been asked.
- User key expressions: preserve the user's own wording whenever possible.
- Article material pool: candidate judgments, examples, analogies, boundaries, titles, and open questions.
- Caution points: overextended analogies, weak evidence, unclear concepts, or places where AI should not overclaim.
- Next natural question: one concrete continuation question.

Do not rewrite user wording into polished assistant language.

## Transcript Rules

Append each completed interview turn to `对谈记录`.

Each turn should include:

- Turn number.
- Material anchor.
- AI question.
- User answer.
- Short AI echo or continuation note, only if useful for recovery.

The transcript may lightly clean formatting, but should preserve user wording.

## Write Cadence

Append the completed turn every round when file writing is available.

Update the snapshot when any of these happens:

- Every 3 to 5 turns.
- The interview switches to another material anchor.
- The user says "先到这里", "暂停", "结束", "收尾", or similar.
- The user gives a long answer that creates multiple article materials.
- The assistant notices two consecutive turns without returning to the source material.
- Before judging article export readiness.

Pause and end must flush `interview.md`.

Do not tell the user every time the file is updated. Only mention file status at opening, failure, pause, and final export.

## Recovery

When continuing an existing interview, first read:

1. `interview.md` status snapshot.
2. The latest five turns.
3. Earlier key expressions or article material only if needed.

After reading, state the recovery point:

```text
我从记录里恢复到这里：我们已经讲过 <已覆盖锚点>，现在停在 <当前锚点>。接下来我会从 <下一问题方向> 继续。
```

Do not pretend to remember details outside the record. If the file does not contain something, say that the record does not contain it.

If `interview.md` is missing or damaged, say the session cannot be fully recovered and continue only from the current context.

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

## Failure Modes

The persistence layer fails if:

- It interrupts the interview with frequent file-status updates.
- The snapshot becomes a polished summary that overrides user wording.
- The record tracks only personal examples and loses material anchors.
- The assistant pretends to remember content not present in `interview.md`.
- File failure is hidden from the user.
- Ending-stage article export uses assistant summaries instead of user words.
