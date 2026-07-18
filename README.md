# VerticalRTK

VerticalRTK is a benchmark of realistic **research questions** with reference
answers. Use it to evaluate search and answer APIs.

Most RAG benchmarks keep the answer on one page that a system can retrieve.
VerticalRTK is different: it asks the questions that a real analyst asks. Many
are hard, multi-step questions. To answer them, a system must combine and compute
over sourced data. Other questions have a ground truth that the open web
documents poorly, or that changes over time — commodity and crypto prices, FX
rates, sports results, and prediction markets. The goal is not to measure whether
a system can find the page. The goal is to measure whether the system gives the
correct answer.

The questions cover finance, macroeconomics, banking and insurance, company
operations (bookings, billings, subscribers, sales volume, web traffic),
climatology, crypto, sports, prices and rates, and polling. The set also includes
a group of deliberately hard, multi-step questions.

## Data

[`data/verticalrtk.jsonl`](data/verticalrtk.jsonl) has 131 rows, one JSON object
per line:

| field | description |
| --- | --- |
| `id` | Stable identifier, `vrtk_0001` … `vrtk_0131`. |
| `query` | The question that you send to the search or answer system. |
| `expected_answer` | A reference answer that gives the correct result. |

Example:

```json
{"id": "vrtk_0047", "query": "How much is Gala worth today?", "expected_answer": "Gala (GALA) is worth about $0.00205 USD today."}
```

## Grading

`expected_answer` is a **reference answer**, not a required output string. Grade
each system answer against it with the harness that suits you. We recommend a
grading harness such as
[web-search-api-evals](https://github.com/youdotcom-oss/web-search-api-evals),
which fetches results, synthesizes an answer, and scores it against the ground
truth with an LLM judge.

This repository ships **data only** — no runner, no graders, and no results.

## Point-in-time caveat

The answers are correct as of **July 2026**. Many questions have a ground truth
that changes over time — crypto and commodity prices, FX rates, sports standings,
and prediction markets. Some of the hard, multi-step questions also refer to
"today" or to a trailing window. Treat time-sensitive answers as a snapshot.
Check them against fresh sources again before you use them as pass or fail gates.

## License

VerticalRTK is licensed under [Creative Commons Attribution 4.0 International
(CC BY 4.0)](LICENSE). You may share and adapt the material for any purpose,
including commercially, provided you give appropriate credit.

© 2026 Tako (TakoData).
