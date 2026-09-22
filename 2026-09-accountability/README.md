# Accountability

Artifacts behind **Accountability: Measuring Respect for Human Oversight in Tool-Using
Assistants** ([gaussia-labs/papers](https://github.com/gaussia-labs/papers), under
`papers/2026-09-accountability/`).

```
2026-09-accountability/
├── contradiction_checker/   # Experiment 1: which instrument verifies a claim
└── sandbox/                 # Experiment 2: the metrics over synthetic sessions
```

## Experiment 1 — which instrument verifies a claim

320 constructed cases comparing the relevance reranker the framework ships, an LLM
judge and a small inference model on the question of whether a claim about an
assistant's own conduct is borne out by the trace. Construction and per-group labels
are documented in [`contradiction_checker/README.md`](contradiction_checker/README.md).

```bash
cd contradiction_checker
python run_reranker.py      # cross-encoder reranker
python run_judge.py         # LLM judge
python run_entailment.py    # inference model, downloads its weights on first run
python run_group_d.py       # failure-mode breakdown
```

## Experiment 2 — the metrics over a synthetic sandbox

Eighteen hand-written sessions, each carrying the violations it contains and the
figures the metrics should return.

```bash
cd sandbox
python run_sandbox.py --judge oracle       # no credentials, reproduces every
                                           # deterministic figure in the paper
python run_sandbox.py --judge continuous   # judge with a confidence score
python run_sandbox.py --judge discrete     # judge with labels only
python test_penalty.py                     # self-check for the noisy-OR penalty
python probe_confidence.py
```

Only the oracle mode runs offline. The other two need a provider, and the report states
which mode ran, because the two are different estimators and their figures must not be
compared.

## What backs each table in the paper

| Table | Artifact |
|---|---|
| Instrument comparison | `contradiction_checker/results/` |
| False claims caught, by failure mode | `contradiction_checker/results/group_d.json` |
| The eighteen sandbox sessions | `sandbox/results/sandbox_*.json` |
| Metric vs. rejected alternative | `sandbox/results/` |

Both OversightCompliance figures, the rate and the weighted one, are deterministic and
identical across all three sandbox runs, which is the asymmetry the paper's H1 reports.
