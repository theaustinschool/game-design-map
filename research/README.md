# Notes corpus

The evidence base for the **Rulebook** (see `CONTEXT.md`). Each gather ticket writes exactly one ledger file here; synthesis merges them.

Branch: `research/notes-corpus`. Never merged to `main` until the map says so.

## One file per ticket

`research/<NN>-<slug>.md`, where `NN` is the GitHub issue number. Write only your own file. Never edit another ticket's file.

## File shape

```markdown
# <ticket title>

Ticket: <issue URL>
Scope: <what this sweep covers, in one line>
Swept: <YYYY-MM-DD>

## Claim ledger

| id | claim | quote | url | author | date | topics | accessed |
| -- | ----- | ----- | --- | ------ | ---- | ------ | -------- |

## Conflicts noticed

## Coverage log

| url | status | method | accessed | note |
| --- | ------ | ------ | -------- | ---- |

## Known gaps
```

### Claim ledger columns

- **id**: `<NN>-<seq>`, such as `14-007`. Stable once written.
- **claim**: one atomic statement about what makes a note good, or how to build one. Write it in English, in your own words, phrased as the source means it. One idea per row.
- **quote**: the verbatim source text that supports the claim, as short as carries the meaning. For German sources, give the German original followed by ` / ` and an English translation.
- **url**: the canonical URL of the exact page, with a `#anchor` where one exists. For forum posts, link the comment permalink.
- **author**: the person who wrote the quoted text, not the site.
- **date**: the publication date as shown on the page, or `unknown`.
- **topics**: one or more tags from the list below, comma-separated.
- **accessed**: the method and date, such as `curl 2026-11-04`, `WebFetch 2026-11-04`, or `chrome 2026-11-04`.

### Topic tags

`atomicity`, `title`, `linking`, `link-context`, `structure-note`, `hub`, `id`, `folgezettel`, `tags`, `sources`, `literature-note`, `own-words`, `writing-style`, `length`, `audience`, `evergreen`, `concept-oriented`, `densely-linked`, `process`, `review`, `inbox`, `failure-mode`, `tooling`, `other:<word>`

If you need a new tag, use `other:<word>` and add it under Conflicts noticed, so synthesis can promote it.

### Coverage log

Every URL you considered gets a row, whether or not it yielded claims. This log is what proves the sweep was complete.

- **status**: `read`, `read-no-claims`, `skipped`, or `failed`.
- **method**: how you accessed the page (curl, WebFetch, chrome, or an API).
- **note**: for `skipped` or `failed` rows, the reason.

No raw page text is committed. The URL plus the access method is the provenance.

## Rules for gatherers

- **Read every item in full, to the last word.** Don't truncate posts, skim, keyword-scan, sample, stop at saturation, or triage by title. `read` and `read-no-claims` in the coverage log mean every word was read. Anything less is not coverage.
- A Known gap is only something truly unreachable (HTTP error, no content exists), logged with the exact error. Anything behind a login is out of scope.
- Record claims. Don't resolve conflicts. When two sources disagree, record both claims and add a line under Conflicts noticed. Resolution happens in grilling, later.
- Leave out commentary and recommendations, and don't synthesize across files.
- Cover public content only. List paywalled or members-only material under Known gaps.
- Luhmann, Ahrens, and other outside authors enter only as cited by the source you are sweeping. Attribute such claims to the citing page and author, and note the original in the claim text.
