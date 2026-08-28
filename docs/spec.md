# Source construction quality — specification

This document is **generated from the graph** by `tl docs`; `tl docs --check` gates it
in CI. The prose headings are hand-owned — everything between `tl:*` markers is injected
from the YAML items, so this document can never drift from the graph.

It carries
<!-- tl:count type == 'requirement' -->
7
<!-- tl:end --> requirements.

## Purpose

<!-- tl:item INT-0001 -->
**INT-0001 — A published standard is re-expressed as a graph without distortion or loss** — `intent`, status `approved`

> A throughline source exists so that a project can ground its own work in a published standard by composing it, rather than by retyping it. That is only worth doing if the rendering is faithful to the standard and legible to a reader who has not opened the original. A source that quietly distorts what it re-expresses is worse than no source at all, because it is trusted and composed at scale.
<!-- tl:end -->

## How this graph is applied

These requirements are applied **through construction, not by reference**. What
satisfies them is the generator that builds a governed source; what cites them is the
commit that changes that generator. The governed source itself stays a standalone cut
of its standard, with no dependency on this graph.

<!-- tl:item NG-0001 -->
**NG-0001 — This graph is not composed by the sources it governs** — `non_goal`, status `proposed`

> A governed source does not declare this graph as a `[[sources]]` dependency and does not name its UIDs in item links. tl-compose namespaces are not transitive, so a reference from a source to this graph forces every downstream consumer to declare a namespace it has no interest in or fail — `tl-compose check` exits 2 with "names namespace 'quality', which is not a declared [[sources]] namespace". Sources exist to be composed by other people, and loading them with the toolchain's own housekeeping is a cost every consumer pays forever. These requirements are applied through construction instead — the generator that builds a source satisfies them, and the commit that changes that generator cites them.

**origin**: hybrid
<!-- tl:end -->

## Requirements

<!-- tl:table type == 'requirement' -->
| UID | Type | Status | Title |
|---|---|---|---|
| REQ-0001 | requirement | proposed | A mechanically derived title is a complete statement, never a truncated fragment |
| REQ-0002 | requirement | proposed | A derived title is reproducible from the clause it labels |
| REQ-0003 | requirement | proposed | Clause text is reproduced as the publisher wrote it |
| REQ-0004 | requirement | proposed | A UID, once allocated to a clause, is permanent |
| REQ-0005 | requirement | proposed | Regeneration preserves hand-authored content |
| REQ-0006 | requirement | proposed | A clause the publisher has withdrawn gets no item |
| REQ-0007 | requirement | proposed | The publisher's own clause identifier lives in an attribute, not in the UID |
<!-- tl:end -->

### Titles

<!-- tl:item REQ-0001 -->
**REQ-0001 — A mechanically derived title is a complete statement, never a truncated fragment** — `requirement`, status `proposed`

> Where an item's title is derived from clause text rather than written by hand, the derivation yields a grammatically complete statement that identifies the clause. It never emits the fragment left behind by cutting the clause at a punctuation mark. Splitting on the first comma, semicolon or full stop does not satisfy this, because all three occur freely inside a sentence — inside subordinate clauses, inside parenthetical lists, and inside abbreviations such as "e.g." — and the result is a label like "That" or "Data selection or database queries (e" that identifies nothing. Taking the first complete sentence of the clause does satisfy it.

*Implements:* INT-0001

**priority**: must · **origin**: hybrid
<!-- tl:end -->

<!-- tl:item REQ-0002 -->
**REQ-0002 — A derived title is reproducible from the clause it labels** — `requirement`, status `proposed`

> The derivation from clause text to title is deterministic, so that the same clause always yields the same title. A reviewer can then re-run a generator and see that the titles it would write match the titles on disk, which is what makes an incorrect derivation detectable rather than a matter of taste.

*Implements:* INT-0001

**priority**: must · **origin**: hybrid
<!-- tl:end -->

### Fidelity to the published standard

<!-- tl:item REQ-0003 -->
**REQ-0003 — Clause text is reproduced as the publisher wrote it** — `requirement`, status `proposed`

> An item's text carries the clause verbatim. Mechanical normalisation is permitted where it loses no meaning — resolving a hyperlink to its label text, removing the publisher's internal cross-reference markers, collapsing runs of whitespace. Paraphrasing, summarising, correcting or truncating the clause is not, because a consumer grounding its work in a borrowed item is entitled to read what the standard actually says.

*Implements:* INT-0001

**priority**: must · **origin**: hybrid
<!-- tl:end -->

<!-- tl:item REQ-0006 -->
**REQ-0006 — A clause the publisher has withdrawn gets no item** — `requirement`, status `proposed`

> Standards bodies commonly retain the numbers of withdrawn clauses as tombstones so that existing citations keep resolving. A tombstone is not a requirement, and rendering one as a live item would invite a consumer to ground work in a clause the publisher has already withdrawn.

*Implements:* INT-0001

**priority**: must · **origin**: hybrid
<!-- tl:end -->

### Identity and stability

<!-- tl:item REQ-0004 -->
**REQ-0004 — A UID, once allocated to a clause, is permanent** — `requirement`, status `proposed`

> Consumers cite borrowed items by UID, and those citations live in repositories this source cannot see. Re-running a generator against a newer edition of the standard therefore allocates UIDs only to clauses that do not yet have one, and never renumbers, reuses or reorders a UID already published.

*Implements:* INT-0001

**priority**: must · **origin**: hybrid
<!-- tl:end -->

<!-- tl:item REQ-0005 -->
**REQ-0005 — Regeneration preserves hand-authored content** — `requirement`, status `proposed`

> Where a human has curated an item — a hand-written title, an added note — that content survives a re-run of the generator that produced the surrounding graph. A generator that overwrites curation makes the graph unimprovable by hand, so any bulk rewrite of generated content is an explicit operation that states what it will overwrite, not a side effect of ordinary regeneration.

*Implements:* INT-0001

**priority**: must · **origin**: hybrid
<!-- tl:end -->

<!-- tl:item REQ-0007 -->
**REQ-0007 — The publisher's own clause identifier lives in an attribute, not in the UID** — `requirement`, status `proposed`

> The published identifier of a clause — "V2.1.1", "1.4.3" — is recorded as an attribute of the item. It is not encoded in the UID, because the two are governed by different parties — the publisher renumbers its clauses between editions, while a UID must stay fixed for the consumers citing it.

*Implements:* INT-0001

**priority**: must · **origin**: hybrid
<!-- tl:end -->
