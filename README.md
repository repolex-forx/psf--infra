# Repolex Knowledge Graph of psf/infra

RDF knowledge graph data for [psf/infra](https://github.com/psf/infra), parsed by [repolex](https://repolex.ai).

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
rlex download psf/infra
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── fe5c204dabc12201ba44431bfde750b670c7df78
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── fe5c204dabc12201ba44431bfde750b670c7df78
│           └── chunk-001.nq.gz
├── blob
│   ├── 07c02529fda007af774dd5fefc75d675e9d1fefc.nq.gz
│   ├── 2df6c6f55b0bbe7ced3de6b055a94316d6c41eb5.nq.gz
│   ├── 3eded3facdebe05d82777b2dcdcdd843a33f60c4.nq.gz
│   ├── 590b3fb7eb6d67c80687d7382548a98cff2e3cc6.nq.gz
│   ├── 5cb1ae92ef9eae354a951fc549f031e30fa75fdf.nq.gz
│   ├── 6242c8b94cce18ba2f6718957389372d61dbad69.nq.gz
│   ├── 86fa677d795c48f17662e5a50891a7d36be6f4f3.nq.gz
│   ├── 9a49ff1763828f3d29a14a8f08487f0e2452ff2e.nq.gz
│   ├── a7cfd93834c9d76f5325a22da06d4ab7f88ea79c.nq.gz
│   ├── b7086f2a9ee3e66faebbaeaac2ad53de90783228.nq.gz
│   └── f7021af5d49286979ef5bab23709acc42b18cf94.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── fe5c204dabc12201ba44431bfde750b670c7df78.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 19 files
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

[psf/infra](https://github.com/psf/infra)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
