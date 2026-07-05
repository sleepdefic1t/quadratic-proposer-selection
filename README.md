# Quadratic Proposer Selection

Sublinear block production in BFT consensus.

QPS replaces CometBFT's linear proposer-priority increment with sqrt(stake), compressing the block production ratio between validators from k to sqrt(k). Commit voting, quorum thresholds, and reward distribution remain linear. BFT safety proofs apply without modification.

Implemented in LythiumBFT. Validated over 95 days and 1.39 million blocks.

## Contents

```
report/          Technical report (PDF + LaTeX)
src/             Reference implementation
data/            Empirical validation data
```

## Report

The technical report is at [`report/qps-report.pdf`](report/qps-report.pdf).

Build from source:
```
cd report && pdflatex qps-report.tex
```

## Implementation

QPS is implemented in [LythiumBFT](https://github.com/sleepdefic1t/lythiumbft), a fork of CometBFT v0.38.19.

| | |
|---|---|
| Commit | [`36592a9`](https://github.com/sleepdefic1t/lythiumbft/commit/36592a9408867cd8750f95e6277877e43c7617b8) |
| File | `types/validator_set.go` |
| Changes | One modified function, two helpers, one constant |

No changes to quorum logic, reward logic, or the application-layer interface.

See [`src/`](src/) for the implementation file and details.

## Data

Empirical validation from Monolythium testnet:

| | |
|---|---|
| Duration | 95 days |
| Blocks | 1.39M |
| Validator set | 7 → 41 → 6 |
| Stable windows | 8 (W1–W8), 580K blocks total |

```
data/windows/       Per-window block production analysis
data/cross-chain/   Gini coefficient analysis (9 chains)
data/summary/       Aggregate metrics
```

Observed Gini reduction vs linear: 51–56%. Cross-chain analysis: 26–56% depending on stake distribution.

## Citation

Use GitHub's "Cite this repository" or see [`CITATION.cff`](CITATION.cff).

## License

- Research and documentation: MIT ([`LICENSE-MIT`](LICENSE-MIT))
- Implementation (CometBFT-derived): Apache-2.0 ([`LICENSE-APACHE-2.0`](LICENSE-APACHE-2.0))
- Attribution: [`NOTICE`](NOTICE)
