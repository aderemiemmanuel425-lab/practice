---
id: git-version-control-model
title: "Version Control and Git's Local Model"
status: draft
difficulty: foundation
active_minutes: 100
prerequisites: [terminal-foundations]
outcomes:
  - id: git-distinguish-tool-repository-host
    level: L1
    statement: "Distinguish Git, a local Git repository, and a repository hosting service"
    assessed_by: [explanation]
  - id: git-explain-working-index-head
    level: L2
    statement: "Interpret observed working-tree and index differences relative to HEAD without forcing files into one exclusive state"
    assessed_by: [lab, explanation]
  - id: git-observe-object-relationships
    level: L2
    statement: "Use trusted Git observations to identify blob, tree, commit, and annotated-tag objects"
    assessed_by: [lab]
  - id: git-bound-integrity-claims
    level: L2
    statement: "Explain snapshot reuse, object-format qualification, and why an object ID does not authenticate an author"
    assessed_by: [lab, explanation]
applies_to:
  - technology: Git
    version: "2.55 documentation; lab verified with Git 2.55.0"
    lane: current
platforms: [linux, macos, windows]
verified_at: 2026-08-26
review_by: 2027-02-26
sources:
  - title: "Git glossary"
    url: https://git-scm.com/docs/gitglossary
    kind: official-docs
  - title: "Git repository layout"
    url: https://git-scm.com/docs/gitrepository-layout
    kind: official-docs
  - title: "Pro Git — Git Objects"
    url: https://git-scm.com/book/en/v2/Git-Internals-Git-Objects
    kind: official-docs
  - title: "Git hash function transition"
    url: https://git-scm.com/docs/hash-function-transition
    kind: official-docs
  - title: "git-status documentation"
    url: https://git-scm.com/docs/git-status
    kind: official-docs
---

# Version Control and Git's Local Model

## Why this matters

Version control records named project states and their relationships so you can
inspect, compare, and intentionally advance a history. Copying folders named
`final-2` can preserve bytes, but it does not by itself record a coherent
change, parent relationship, author/committer metadata, or a queryable project
history.

Git is one version-control system. A Git repository can exist and accept local
commits without GitHub, GitLab, a network, or any hosting account. A hosting
service stores and coordinates repositories plus service-specific features;
it is not Git itself.

## Distributed, with qualifications

Git is a distributed version-control system: an ordinary clone contains a
local object database and refs, enabling many history, commit, branch, and diff
operations without contacting a server. But “every clone always contains every
object” is too strong. Shallow clones intentionally limit history, and partial
clones may defer some objects. State the clone type before making disaster-
recovery or offline-completeness claims.

A centralized system can still be a deliberate organizational choice. Server-
side authorization, large binary workflows, existing tooling, and migration
costs are separate concerns from whether local commits are possible. This
course teaches Git; it does not claim that one architecture wins every context.

## Three locations, not three exclusive file states

For the next commit, reason about three representations:

```text
HEAD commit/tree  ← compare →  index  ← compare →  working tree
last committed                  proposed             editable files
snapshot                        next snapshot
```

- The **working tree** contains checked-out files available for editing.
- The **index** is Git's staging structure. It records the proposed content and
  paths for the next snapshot.
- **HEAD** normally identifies the currently checked-out commit through a ref,
  although detached HEAD is also possible.

These are not three boxes where each file lives in exactly one box. After you
edit an already tracked file, one version can be in HEAD and the index while a
different version is in the working tree. After you stage that edit, the new
version can match the working tree and index while HEAD still names the earlier
snapshot. A file can also be untracked or ignored.

The lab observes `git status --porcelain=v1`. Its two status columns compare
index-to-HEAD and working-tree-to-index. For its fixed file:

```text
?? note.txt   untracked
A  note.txt   added to the index
 M note.txt   working tree differs from the index
M  note.txt   index differs from HEAD
```

An empty porcelain response means no reported change under those options; it
does not prove the repository is backed up, published, or recoverable.

## Commits represent snapshots

At the conceptual object-model level, a commit points to a root tree describing
a project snapshot. Unchanged content can reuse existing objects, so Git does
not need to duplicate every file's bytes for every commit. Git can also store
objects efficiently in packfiles and use delta compression. That storage
optimization does not turn the commit's meaning into “only a diff.” Git can
compute diffs between states when requested.

A commit also records parent commit IDs (except a root commit), author and
committer metadata, and a message. Metadata is evidence stored in the commit;
plain name/email fields alone are not verified identity.

## Four object types and refs

Git's object database has four object types:

- A **blob** stores file content but not its pathname.
- A **tree** records names, modes, and object IDs for a directory-shaped
  snapshot.
- A **commit** points to a tree and records parents and commit metadata.
- An annotated **tag object** records a target, target type, tag name, tagger,
  message, and optional signature.

A lightweight tag is different: it is a ref that points directly to another
object, commonly a commit. It does not create a tag object. An annotated tag
normally has both a tag ref and a tag object.

## Object IDs: integrity with limits

For a loose Git object, the object ID is computed from the object type, a space,
the byte length, a NUL byte, and the content. That is why identical blob content
can reuse an object even under different pathnames.

Git repositories have an object format. SHA-1 remains common, while Git also
documents SHA-256 repositories and transition concerns. Observe the current
repository instead of hard-coding an ID length:

```bash
git rev-parse --show-object-format
```

An object ID allows Git to detect a content mismatch under its object model.
It is not proof that a claimed human authored the commit, and a hash alone is
not an authorization or backup system. Authentication and signed-object policy
are later topics.

## What a local commit does not guarantee

A commit is not automatically:

- copied to another device;
- pushed to a remote;
- reviewed or approved;
- retained forever after refs and reflogs stop reaching it;
- free of secrets or generated files;
- evidence that the program works.

Version control and backup overlap in recovery value but are not substitutes.
The later Git lessons add careful staging, commits, inspection, ignore rules,
and recovery without teaching destructive shortcuts first.

## Guided practice

Open [the lab](lab/README.md). Predict each status line, then run the checker.
The checker constructs a trusted temporary repository, makes two fixed commits,
and inspects object types. It disables system/global config for the fixture and
uses local identity flags. It never executes text from your YAML.

Fill one field at a time and rerun. Do not edit the checker to obtain a PASS.

## Common failure modes

### “A file moves from working tree to staging to repository”

The working file does not disappear when staged or committed. Instead, compare
representations across working tree, index, and HEAD.

### “Every commit stores a fresh physical copy of every file”

The commit identifies a snapshot through trees and blobs, while unchanged
objects can be reused and packfiles can compress storage.

### “There are four kinds of tags”

There are four object types. Only annotated tags create tag objects;
lightweight tags are refs.

### “A matching hash proves who wrote it”

It does not. It supports object integrity, not human identity authentication.

### “My local commit is safely backed up”

Not unless independent copies and recovery have been established and tested.

## Independent transfer

Given a tracked file where `git status --short` reports `MM file.txt`, explain
the two comparisons without running a repair command. Identify which
representations differ and why “the file is staged” is incomplete.

Then explain why a lightweight tag can resolve to a commit even though Git's
object database still has a distinct `tag` object type.

## Retrieval and remediation

From memory, draw HEAD, index, and working tree with both comparison arrows.
Label blob, tree, commit, annotated tag object, and lightweight tag ref.

If you still place a file in only one state, return to the lab's edit and
second-add observations. Do not proceed to `git restore` or `git reset` until
you can say which comparison each status column describes.

## Sources

- The [Git glossary](https://git-scm.com/docs/gitglossary) defines working tree,
  index, refs, HEAD, objects, shallow repositories, and related terms.
- [Git repository layout](https://git-scm.com/docs/gitrepository-layout)
  documents the repository's object and ref structures.
- [Git Objects](https://git-scm.com/book/en/v2/Git-Internals-Git-Objects)
  develops the blob, tree, and commit model.
- [Git's hash transition documentation](https://git-scm.com/docs/hash-function-transition)
  documents SHA-1/SHA-256 object-format design and transition constraints.
- [`git status`](https://git-scm.com/docs/git-status) defines the short and
  porcelain output used by the lab.