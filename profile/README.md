# Oval

Oval is a plain-text file format for voting guides. A guide is one `.oval` file: the election,
the ballot as the voter will see it, every contest and measure on it, and the author's
recommendation on each. The file is meant to be written by hand and read without any tooling, and
it compiles to a JSON model that any site or app can render.

```
oval 0.1

guide "Franklin Voter Guide"
election "November 3, 2026 General Election"
date 2026-11-03

party @dem "Democratic"

ballot @franklin "State of Franklin"
  section "Statewide Offices"
    contest @gov "Governor" single
      campaign incumbent @jlee "Jordan Lee"
        party @dem
      campaign @rkim "Riley Kim"
      recommend
        support @jlee
        justification:
          Lee delivered on the transit plan.
  measure @prop1 "Proposition 1"
    supporters "Franklin Transit Alliance"
    opponents none
    recommend yes
```

## Repositories

| Repository | What it holds |
|---|---|
| [oval-spec](https://github.com/oval-vote/oval-spec) | The specification: grammar, validation rules, and the JSON Schema for compiled output. |
| [oval](https://github.com/oval-vote/oval) | The reference implementation in Rust: parser, validator, compiler, and formatter; the `oval` command-line tool; and [`@oval-vote/oval`](https://www.npmjs.com/package/@oval-vote/oval), the same code as a WebAssembly package for Node. |
| [vscode-oval](https://github.com/oval-vote/vscode-oval) | The [Visual Studio Code extension](https://marketplace.visualstudio.com/items?itemName=oval-vote.oval): highlighting, diagnostics as you type, and formatting. |
| [oval-coming-soon](https://github.com/oval-vote/oval-coming-soon) | The placeholder page at [oval.vote](https://oval.vote). |

## Status

Oval is a working draft at version 0.1. The specification, the implementation, and the extension
share one version number, and the first two components are the language version a document
declares on its first line. Until 1.0, each 0.x version is a distinct language and may change
incompatibly.

## Getting started

- Install the Visual Studio Code extension and open a `.oval` file.
- From JavaScript, `npm install @oval-vote/oval` gives you `check`, `compile`, and `format`.
- From a terminal, build the `oval` tool from the `oval` repository with `cargo install --path crates/oval-cli`.
- Read the [specification](https://github.com/oval-vote/oval-spec/blob/main/SPEC.md) and the full
  [example guide](https://github.com/oval-vote/oval-spec/blob/main/examples/franklin.oval), a
  fictional metropolitan ballot that exercises every construct.

## Contributing

Each repository has a README describing how to build and test it. Design discussion happens in
issues on the repository the change belongs to; language changes start in `oval-spec`.
