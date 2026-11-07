# Repolex Knowledge Graph of allenai/pier

RDF knowledge graph data for [allenai/pier](https://github.com/allenai/pier), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download allenai/pier
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── cadf04911612f63a7b900d40d21c92786f6bfd3d
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── cadf04911612f63a7b900d40d21c92786f6bfd3d
│           └── chunk-001.nq.gz
├── blob
│   ├── 00750b6f70ac0fdd1227f66ba387ad06e29dde09.nq.gz
│   ├── 03cdb171829534ef98f89cf5c1f908752172152e.nq.gz
│   ├── 0b73847dfd4adf2affcb2557abf353301ace5ec0.nq.gz
│   ├── 110198e8a465588ddef5af8d9c873960d4fcb896.nq.gz
│   ├── 175ebc5cd5a16e79d7838dad1b4f85b28976cd29.nq.gz
│   ├── 1b05aea9c4547848d3bbdce3dcea6bb046868cd9.nq.gz
│   ├── 216d3f1af6f3354828c463855e6aa0ff91b00ddd.nq.gz
│   ├── 21e8e4d579daa72c8c99d9e94d5f74aa6abac6ae.nq.gz
│   ├── 3a6fb973e4e5d3741e3e65c18764c43bdefb74e4.nq.gz
│   ├── 3dc1f76bc69e3f559bee6253b24fc93acee9e1f9.nq.gz
│   ├── 561bf1cd96c0f9207a5247fd8cd3410136f42102.nq.gz
│   ├── 5c973168ecdcfea58133a86af58a5906265cf35f.nq.gz
│   ├── 880302bcc19b7f496abd73f67a1150efb20f7251.nq.gz
│   ├── 8b5d905315f2db4ba8748eeb4358aabcd9388080.nq.gz
│   ├── 9dafb231281fb14906c7b05009e77136dbfb2c7c.nq.gz
│   ├── a7416668b41a55cb3fba7c0617e5a2c87dede77e.nq.gz
│   ├── af48256bb8824f7e5921dd9342bcc562550176d3.nq.gz
│   ├── cc4fd268647571f8c3436552eefce1b377d6df77.nq.gz
│   ├── d645695673349e3947e8e5ae42332d0ac3164cd7.nq.gz
│   ├── df95264c68c55ae919e93b3ac546a88f33bbc2e0.nq.gz
│   ├── e1032486205d9eb7c2f715e734b794e65f3a8371.nq.gz
│   └── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── cadf04911612f63a7b900d40d21c92786f6bfd3d.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 30 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[allenai/pier](https://github.com/allenai/pier)

---
*Parsed on 2026-11-07 by [repolex](https://repolex.ai)*
