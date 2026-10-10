# Repolex Knowledge Graph of honojs/skills

RDF knowledge graph data for [honojs/skills](https://github.com/honojs/skills), parsed by [repolex](https://repolex.ai).

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
rlex download honojs/skills
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 5becff424255f5d1ec1b4f7b93b6f3480e55783b
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 5becff424255f5d1ec1b4f7b93b6f3480e55783b
│           └── chunk-001.nq.gz
├── blob
│   ├── 161ad30574baca9d7afad02306c9af8d2e789d1e.nq.gz
│   ├── 1ac9ea5a3bb6866ae462cdb3fa74c182c3e3a0ab.nq.gz
│   ├── 3ea45410e4c6aa25660e0ed86daf065345667c09.nq.gz
│   ├── 4cd88fc81912a1510ec16c07e059faf7e364e2c6.nq.gz
│   ├── 829147be4d9a8222abe51995b9338a581a19639f.nq.gz
│   └── f5e64bae8d00cf00065b52636e3d2986672d66d8.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 5becff424255f5d1ec1b4f7b93b6f3480e55783b.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 13 files
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

[honojs/skills](https://github.com/honojs/skills)

---
*Parsed on 2026-10-10 by [repolex](https://repolex.ai)*
