Frontmatter
name: write-pr-description
description: Writes the pull request description that should accompany a code change — a diff, a branch, or a set of edited files. Produces a short, fixed-structure description covering what changed, why, and how a reviewer can verify it, plus a section flagging what the author is least confident about. Use this whenever the user asks to write, draft, or generate a PR description, commit summary for a PR, or "write-up" for a diff/branch/change — including phrasing like "write the description for this PR," "summarize this diff for review," or "what should I put in the PR body." Make sure to use this skill any time a code change is being prepared for review, even if the user just pastes a diff and says "describe this" or "write this up."
Write PR Description
What this is for
A PR description is not documentation and not a changelog entry. It exists to make one specific reader — the reviewer — fast and effective at their job in the next five minutes. Every sentence should either help them understand the change or help them check it. Nothing else earns a place in it, and this skill measures itself against that: if a sentence doesn't do one of those two jobs, cut it before finishing.
Before writing
Look at the actual change, not just what the user tells you about it. If given a diff, read it. If given a branch or files, use available tools (git diff, git log, file reads) to see the real edits before writing anything. A description written from a vague summary instead of the real diff is how "fixed the bug" descriptions happen — reviewers can smell it, and it defeats the point.
If the "why" isn't obvious from the code, the commit messages, or context the user gave you, don't invent a motivation. Either ask the user in one short question, or write the why section from what's genuinely inferable and flag the gap rather than fabricating a business reason.
Output structure
Always use exactly these four sections, in this order. Do not add extra sections (background, architecture diagrams, future work, checklists) unless the user explicitly asks — those pad the description past what the change deserves and get skipped.
## What changed
## Why
## How to verify
## Least confident about
What changed — The concrete edit, not the file list. Name the behavior that's different now, in terms a reviewer can picture. One or two sentences for a small change; a short list only if multiple unrelated things genuinely changed (and if that's true, say so — it's a sign the PR might be doing too much).
Why — The reason this change needed to happen: the bug, the request, the constraint, the linked issue. Not a restatement of "what changed" in past tense. If there's a ticket or issue, reference it instead of re-explaining it.
How to verify — Concrete steps a reviewer can actually run or check: commands, test names, a URL to click through, before/after output. "Should still work" is not verification. If there's no way to verify beyond reading the code, say that plainly instead of padding this section — it tells the reviewer to slow down and read closely.
Least confident about — The one (or two, rarely three) thing the author is genuinely unsure of: an edge case not tested, a performance tradeoff, a naming choice, an assumption about how another part of the system behaves, a spot where they took a shortcut. This is the highest-value section in the whole description — it points the reviewer's limited attention at the part of the diff that most needs a second pair of eyes. Never fill it with a throwaway line like "nothing, looks good" unless that's genuinely true; if the change is trivial enough that there's really nothing to flag, say so in one line rather than omitting the section.
Length discipline
Match the description's length to the change's size and risk, not to some template minimum:
•	A one-line fix or config tweak: a sentence per section, four sentences total. Skip elaboration.
•	A typical feature PR: two to five sentences per section.
•	A large or risky change (schema migration, auth, concurrency, public API): more detail is earned, but stay in bullet form and cut anything a reviewer wouldn't need in the first pass.
Before finishing, reread the draft and cut anything that restates the diff instead of orienting the reviewer. A description that's longer than the change itself is a description nobody will read — that failure mode is worse than being slightly too terse.
Example
Change: a diff adding a 500ms debounce to a search-as-you-type input, changing onChange to call a new debouncedSearch instead of search directly.
## What changed
Search input now debounces API calls by 500ms instead of firing one request per keystroke.

## Why
The search endpoint was getting hammered on fast typing, showing up as elevated p99 latency in the logs (#482).

## How to verify
Run the app locally, type a query quickly in the search box, and confirm only one network request fires ~500ms after the last keystroke (Network tab). `npm test -- search.test.ts` covers the debounce timing.

## Least confident about
Didn't test behavior when a user pastes a long query and hits Enter immediately — the debounce might delay a deliberate submit by up to 500ms, which could feel laggy.
What this skill does not do
It does not review the code, judge whether the change is good, or approve anything — that's review-pr. It only describes the change for the person who will.
<img width="468" height="658" alt="image" src="https://github.com/user-attachments/assets/56dc7aa4-4516-48c7-bdcb-bbda589fa212" />
