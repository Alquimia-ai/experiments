# Experiments

Cases, runners and frozen results behind the numbers reported in the Gaussia papers.
One folder per paper, named the way the paper folder is named in
[gaussia-labs/papers](https://github.com/gaussia-labs/papers).

Nothing here is a library. The metric implementations live in
[gaussia-labs/pygaussia](https://github.com/gaussia-labs/pygaussia); these folders hold
the artifacts a reader needs to check a table in a paper against the run that produced
it.

## Papers

| Folder | Paper |
|---|---|
| [`2026-09-accountability/`](2026-09-accountability) | Accountability: Measuring Respect for Human Oversight in Tool-Using Assistants |

## Credentials

Runners that call a provider read a `.env` placed beside the paper folder, which is
never committed:

```
GROQ_API_KEY=...
HF_TOKEN=...
HF_BILL_TO=...
```

Any runner that needs no provider says so in its own README.
