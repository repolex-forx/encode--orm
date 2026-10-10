# Repolex Knowledge Graph of encode/orm

RDF knowledge graph data for [encode/orm](https://github.com/encode/orm), parsed by [repolex](https://repolex.ai).

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
rlex download encode/orm
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 062f7e03d62d7b30bd1d7ae68152c7b0a6b3535e
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 062f7e03d62d7b30bd1d7ae68152c7b0a6b3535e
│           └── chunk-001.nq.gz
├── blob
│   ├── 038cc4430f3363aa5506d34e16a97ec658ac1826.nq.gz
│   ├── 1099ef49cba95c946f8e85d1633176ed21224230.nq.gz
│   ├── 140cc007dc0a912198e6e02fae67c68568a2ca2e.nq.gz
│   ├── 15a68f79e668b72b588592cbbbc604e1f02f012f.nq.gz
│   ├── 1ab6175c653b9271803fac44221a1b11dd4b2a0e.nq.gz
│   ├── 1c47d2cc2a5c9de1de2ceed00f1ae3819d579c4f.nq.gz
│   ├── 278aecd07e8e4ef51fe15bde1c1a1b762aa15093.nq.gz
│   ├── 2ad6e8e2700aa6665dcbfbd571c915ee2afe89c0.nq.gz
│   ├── 4749c88ee06e571a2460300ac591da1da9c5b40c.nq.gz
│   ├── 4ac3beb7a6248488589ae932e29b2d291ca1d55f.nq.gz
│   ├── 4fecc09fdb3f63f1bf6b51353133a30786a953c5.nq.gz
│   ├── 5a9c69b009a120ec41600c542ef34b0648a721df.nq.gz
│   ├── 65885a7208961207ed34c9659c21ac5ef0b90314.nq.gz
│   ├── 6f584598b7ea832f78c6805a0012e422d79c50b6.nq.gz
│   ├── 7b3922edede8c8f76a1470dbf3392139621bc686.nq.gz
│   ├── 8963b9f219aedbc1bfa78a0b4300764db95abe76.nq.gz
│   ├── 8e2443775c9b984adf103e5efc1d981aabf756b0.nq.gz
│   ├── 9015a7677ed5d249936906753cdd111f2a90828f.nq.gz
│   ├── 938ace66d586d65314e56cae5d7f0a7ba166cd6e.nq.gz
│   ├── 9722af02d6459a3cd3a578451098446a95e5f0b8.nq.gz
│   ├── 97336f516109dc34c82eee2e7eb1652658c86c6c.nq.gz
│   ├── 97743165a0cb176632829bd767764ee8d196c3e4.nq.gz
│   ├── ae5287575100ab7adbbd364641225bcb13cb7bb4.nq.gz
│   ├── aef7f05514e270cdada71b46bcc70033efc53002.nq.gz
│   ├── b20503f64c2f2c3abedb5f0b92c0add1545faeaa.nq.gz
│   ├── b24a1de0b79fc027403a3981b9d119bf28355175.nq.gz
│   ├── b290d6e1a8246a96c6c6740fef9453e77f4afb98.nq.gz
│   ├── b40281447097ff08c7ab984cbc09234e8ed27ee6.nq.gz
│   ├── b9d9565b5eec83cb2512aa428b09f6ac52c891a3.nq.gz
│   ├── bb1cc1d2a69229ed70b6f1d8d82f94fc3f1c30c6.nq.gz
│   ├── bf27a8b818ed34546c2aa0b2cce544dfbeabcecc.nq.gz
│   ├── e03bee4b045a99cdb69d3b93f745a3f6de238a3f.nq.gz
│   ├── e5b71561b07736c373a326386cf348fba5c80c26.nq.gz
│   ├── e7584e384a8e67f8c35388522cbbc082981397ef.nq.gz
│   ├── e7a36cd395e6e551aef4e404c281bcea0d2cbb15.nq.gz
│   ├── e871360d1642bc3ac222718fa735b9daee6dd0fa.nq.gz
│   ├── ea544e32eb640c497ac44b68070474cf874a916a.nq.gz
│   └── ee3ef5c7035536eaeeebad713a987e5d1577d605.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 062f7e03d62d7b30bd1d7ae68152c7b0a6b3535e.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 46 files
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

[encode/orm](https://github.com/encode/orm)

---
*Parsed on 2026-10-10 by [repolex](https://repolex.ai)*
