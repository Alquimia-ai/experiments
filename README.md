# Experiments

Cases, runners and frozen results behind the numbers reported in the Gaussia papers.
Grouped by what the paper is about, then one folder per paper, named the way the paper
folder is named in [gaussia-labs/papers](https://github.com/gaussia-labs/papers).

Nothing here is a library. The metric implementations live in
[gaussia-labs/pygaussia](https://github.com/gaussia-labs/pygaussia); these folders hold
the artifacts a reader needs to check a table in a paper against the run that produced
it.

Runners that call a provider read a `.env` placed beside the paper folder, which is
never committed. Any runner that needs none says so in its own README.
