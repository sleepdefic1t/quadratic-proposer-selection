# Implementation Reference

QPS is implemented in LythiumBFT, a fork of CometBFT v0.38.19.

## Repository

[github.com/sleepdefic1t/lythiumbft](https://github.com/sleepdefic1t/lythiumbft)

## Commit

[`36592a9408867cd8750f95e6277877e43c7617b8`](https://github.com/sleepdefic1t/lythiumbft/commit/36592a9408867cd8750f95e6277877e43c7617b8)

## Changes

The modification is confined to the proposer-priority increment in the validator-set logic:

- One modified function: `incrementProposerPriority`
- Two added helpers
- One added constant

No changes to quorum logic, reward logic, or the application-layer interface.

## Key File

`types/validator_set.go`
