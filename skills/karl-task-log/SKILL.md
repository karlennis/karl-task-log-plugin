---
name: karl-task-log
description: Maintain Karl Ennis's persistent task register in the Google Sheet named "Karl Task Log". Use when Karl asks to log or add a task, record or correct time, change task status, identify who requested work, list open tasks, or summarize tasks or time by workstream.
---

# Karl Task Log

Use the connected Google Drive app to find and update the native Google Sheet named `Karl Task Log`. Work in the `Tasks` tab. Do not create a second register when an exact-title sheet already exists.

If Google Drive is unavailable, ask Karl to connect it and enable Google Sheets write actions. If more than one exact-title sheet exists, show the candidates and ask which one is authoritative before writing.

## Schema

Columns A:I are:

1. Task ID
2. Workstream
3. Task
4. Requested By
5. Time Spent (min)
6. Status
7. Date Added
8. Last Updated
9. Notes

Valid workstreams: `Braidwater`, `Bulki`, `Doctorate`, `Personal`, `Unclear`.

Valid statuses: `Not started`, `In progress`, `Completed`.

## Write rules

- Treat an explicit request to add or update a task as authorization for that sheet change, subject to any app confirmation.
- Before changing an existing row, identify it by Task ID. When Karl gives only a description, search for likely matches and ask one focused question if more than one row could apply.
- For new tasks, assign the next unused sequential ID in the form `TASK-0001`. Never reuse an ID.
- Use Karl's local `Europe/London` date in `YYYY-MM-DD` format for Date Added and Last Updated.
- Record time as whole minutes. Convert hours to minutes. Add newly reported time to the existing total unless Karl explicitly says it is a replacement or correction.
- If no time is given for a new task, enter `0`.
- If no status is given for a new task, use `Not started`.
- Infer the workstream from context. Slack, GitHub, and Linear references are normally Bulki unless strong evidence says otherwise. Messages to `karl.ennis@bulki.com` are normally Bulki. Braidwater email may concern Braidwater, Bulki, or Doctorate, so infer from content. When uncertain, use `Unclear` unless classification would affect another external update.
- Keep Notes concise. Do not paste raw messages, meeting notes, or sensitive content into the register.
- Preserve headers, formulas, validation, formatting, and the `Lists` tab. Append or update task rows only.

## Read and report rules

- `Open` or `active` means every row whose status is not `Completed`.
- For time reports, sum Time Spent (min) and present both minutes and hours when useful.
- Group by Workstream when Karl asks for a company summary. Keep Doctorate, Personal, and Unclear separate from company work.
- State when a report covers all records versus a requested date range. Do not infer historical daily allocation from Last Updated.

After each write, confirm the Task ID, workstream, resulting status, and total recorded time.

## Examples

- `Log a Bulki task: review the payment flow, requested by James.`
- `Add 45 minutes to TASK-0007 and mark it in progress.`
- `Mark the Braidwater board pack task complete.`
- `Show my open tasks by workstream.`
- `Summarize all recorded time by company.`
