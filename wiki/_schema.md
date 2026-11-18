---
name: _schema
description: the layout and writing rules of this knowledge wiki; read before writing anything; never edit
---
This store holds the deal knowledge wiki, in the Agent Knowledge format:
every node is a markdown file with YAML frontmatter, and [[wikilinks]] in
the body are the edges between nodes. Layout (paths relative to the memory
root):

_index.md        the catalog a reader opens first: a short "Where to start"
                 map at the top (written at consolidation), then one line per
                 file, grouped under headings.
escalations.md   the ranked red-flag list, written at consolidation.
SKILL.md         a short note on how to read this wiki, written at consolidation.
_schema.md       this file. Never edit it.

SLUGS (the file names and link targets under entities/, relations/, metrics/
and open_questions/; the root files above keep their fixed names): lowercase
letters, digits and hyphens only - no underscores, dots or spaces. An entity's slug is its plain name with legal
suffixes dropped (squarespace, not squarespace-inc; permira; a person is
first-last: anthony-casalena); a shell or vehicle keeps the words that tell it
apart (spaceship-purchaser, spaceship-parent). A DOCUMENT's slug is its file
name without .txt, with every character that is not a letter or digit turned
into one hyphen (10k_fy2023.part1.txt -> 10k-fy2023-part1). Before creating ANY
file, glob the directory for the slug and near spellings of it; if a file for
the same real-world thing exists under another spelling, write into that file
and record the spelling you would have used as an alias - never a second node.

entities/<slug>.md   one node per real-world entity. Frontmatter:
    ---
    name: <slug>            (matches the filename, the link target)
    description: <one line: what this entity is + why it matters here>
    aliases: ["<every surface form seen, including code names>", ...]
                            (each alias in double quotes, so a name with a
                            comma in it stays one alias)
    metadata:
      type: company | person | fund | shell_entity | advisor | metric_definition | contract | event
    ---
    Body: bullet facts under topical `## <topic>` headings (for example
    ## Ownership, ## Deal terms, ## Red flags), one fact per line and each
    line a sentence or two, not a paragraph: readers find lines by searching
    and pay for every whole line they read. EVERY fact ends with
    `[source: <doc> | as-of: <date>]`. A node that has grown past about
    8,000 characters also gets, right after its frontmatter, a
    `## Current picture` section of at most 30 short lines: the facts a
    reader most likely wants, current values first and each with its source;
    one line per CONFLICT mark or superseded value recorded below; and a last
    line naming the node's other sections. Consolidation writes and maintains
    that section; an extractor only adds facts under the topical headings and
    never rewrites it.
    When a fact mentions another entity in the store, write it as a
    [[wikilink]] to that entity's slug - links are the wiki's edges, and
    every link you add is a constraint that keeps neighbors honest. A link
    is a bare slug ([[squarespace]]), never a path: a document's relations,
    metrics and open_questions files share the document node's slug, so name
    them in prose by path (relations/<slug>.md) and link the node itself.
    EVERY contract document (including each amendment, renewal, DPA, or
    side letter) owns a contract entity node whose slug is EXACTLY the
    document's slug by the SLUGS rule above (its file name; the [SOURCE]
    header carries no slug) - doc <slug> owns entities/<slug>.md, and ONLY
    the agent reading that document writes that node. If a document you are reading merely mentions or summarizes
    a contract that is its own document elsewhere in the data room, do NOT
    create a stub node for it - reference it as a [[redlink]] and put the
    summary facts in your own document's files; the contract's own reader
    fills the node. (Concurrent agents overwrite each other's contract
    nodes wholesale otherwise - one summary stub silently destroyed a full
    verbatim node.) Record the contract's operative
    provisions VERBATIM in that node - never only as a pointer to an index,
    and never scattered across the party entities instead. Party entities
    summarize and [[link]] to the contract node. An analyst reading one
    node must not chase pointers for the exact language.

relations/<doc-slug>.md   relationships found in ONE source document,
    one per line, subjects and objects as [[wikilinks]]:
    `[[<subject-slug>]] | <relation> | [[<object-slug>]] | valid_from=<date> | valid_to=<date or open> | [source: <doc>]`

metrics/<doc-slug>.md   reported financial figures from ONE source document:
    `<metric> | <value> | basis/definition | period | [source: <doc>]`
    NEVER merge figures computed on different bases (e.g. two EBITDA
    definitions) - record each with its basis and keep both.

open_questions/<doc-slug>.md   gaps raised while reading that document.
    ONE line per question: name the gap - and, for enforceability
    questions, the governing law and the applicable legal standard - then
    stop. The question, not an essay; analysis belongs to the analyst who
    picks it up. A [[wikilink]] to an entity that does not exist yet is
    GOOD - a redlink marks the frontier for the resolver and the
    consolidation. Never guess at missing facts.

SINGLE-WRITER RULE (relations/, metrics/, open_questions/): write ONLY
under your own document's slugs - never a shared file or another
document's file. Extraction agents run concurrently, and a shared
append-file invites one agent to overwrite another's work wholesale
(we learned this the hard way: one wholesale rewrite silently destroyed
other agents' verbatim provision text). Consolidation merges the
per-source files into unified views later.

ENTITY NODES ARE SHARED, keyed by real-world identity: one node per
entity, whichever agents touch it. If a node for your contract or
party already exists - even a stub filed from a summary document -
extend THAT node: read-then-merge, never rewrite, and never a duplicate
node under a new slug.
