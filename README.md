# Repolex Knowledge Graph of sloria/konch

RDF knowledge graph data for [sloria/konch](https://github.com/sloria/konch), parsed by [repolex](https://repolex.ai).

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
rlex download sloria/konch
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── a01ce970b763baa94bfef5e3bf078a9a1f196670
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── a01ce970b763baa94bfef5e3bf078a9a1f196670
│           └── chunk-001.nq.gz
├── blob
│   ├── 0b6bdc4660390eb1e0c0fd589fcf20b9996d7cf1.nq.gz
│   ├── 0f69dc113642d9745e07e4f29460abcf4bd669a9.nq.gz
│   ├── 1005e265973ba976766d336b6c043d066e663d6e.nq.gz
│   ├── 1242d43277017748bbbf3d0a104ec4cf78245822.nq.gz
│   ├── 1369783716e9f47555488da7da0cdc1995b3e20d.nq.gz
│   ├── 15cace61e5824949c97e19e56609eb733a653225.nq.gz
│   ├── 16ac4c883b4013707725cef80dcd174bee08db25.nq.gz
│   ├── 16d66407b863c95dca027d6148aba25012716932.nq.gz
│   ├── 259533635835d76d4fb1b41f2c7cdffa361a7f9e.nq.gz
│   ├── 2b030b943b27ff1f2eebd0131d933ad761fb027b.nq.gz
│   ├── 2b4476477fe314cdf9e221f94cecc0727f32d8c9.nq.gz
│   ├── 311a8756ed9a636fe0f08c2e00f10f936961857a.nq.gz
│   ├── 3a17ce5a2974631f19eabbcf4abdee50fa739ea4.nq.gz
│   ├── 3a62700e630c29878063a86fd22afe34380ccf94.nq.gz
│   ├── 416fe35c6fe8fba712cf57adf90b03285915fffa.nq.gz
│   ├── 459928c590d2888bc6b8311e896dada72dbbb674.nq.gz
│   ├── 4fb78c24b37011ee9066aa4284230dde00d99a3b.nq.gz
│   ├── 5156479c46c663fccbec2f5786eab962de684449.nq.gz
│   ├── 5bac451f929d314d6d62ff96e2fd8482fead4df1.nq.gz
│   ├── 64e249963b3af1a2c7db7c323f7add378b188fe8.nq.gz
│   ├── 687549518de192aeac0d6357e49d2450a3ffe199.nq.gz
│   ├── 6db71ef5421290f0263a351046809d06fc9741c2.nq.gz
│   ├── 76888fe1bf10912f9575845efabb510921743065.nq.gz
│   ├── 7985a507992a0fabd2a7606772528904cc57a42c.nq.gz
│   ├── 85ba3b167e8741d1137e423ff2c5e4859a34a994.nq.gz
│   ├── 934c65efed68cce9aad91e86645b0ca32b387d94.nq.gz
│   ├── 958c7c8c2d15c317758af335885a89fca86b121f.nq.gz
│   ├── a25d34153c32bd7ff368595bcda392ad0fd84e7f.nq.gz
│   ├── aa27b00cc6029e096acb363a49a33d30238ff590.nq.gz
│   ├── ab424516bc79ad36fd261810d0c59b40d2279bd4.nq.gz
│   ├── ac9bff6f9d6baf7f018761ddc150ecf205c0e205.nq.gz
│   ├── cb859a4703629dbdb8f93dae68979de3a23d09ae.nq.gz
│   ├── d777b909522cb4dd85e5c959df89c3bf9f9b90f6.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e942930d91da3bc080d9a8235da7a7469508b6bc.nq.gz
│   ├── f40ce91be5fa3ae6afbf5457462f0d87000e4f1b.nq.gz
│   └── f990925773c80e244c72ad10984bb10c5042c16e.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── a01ce970b763baa94bfef5e3bf078a9a1f196670.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 45 files
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

[sloria/konch](https://github.com/sloria/konch)

---
*Parsed on 2026-10-18 by [repolex](https://repolex.ai)*
