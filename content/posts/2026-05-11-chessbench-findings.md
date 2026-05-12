---
title: "Chessbench"
date: 2026-05-11
draft: false
description: "Results from benchmarking LLMs on chess play"
tags: ["chess", "ai", "benchmarks"]
categories: ["Research"]
---

## Overview

I wrote a simple [harness](https://github.com/danielhuadotcom/chessbench) to run OpenRouter LLMs in known-winning endgame positions.

There's plenty of prior-art[^1]<sup>,</sup>[^2] on LLMs playing chess, dating even back to a cool fine-tuned GPT-2 project[^3], 
but overall: they _still_ can't really do this. Surprising finding!

## Results

- [Aggregated Result Table](/chessbench/run_logs/report_results.html)

I burned on the order of $200 to obtain these runs.

Interesting aspects to me: 
- For the most part the models didn't struggle with making illegal moves (unexpected)
- Tested models were great at the mate-in-one
- Google models were strongest by far
- The Google models nailed the pawn endgame position that I took from a chess.com tutorial with good SEO,
but were only partially successful with a pawn endgame of lesser difficulty that I set up manually.
- More abstract endgames proved more difficult (rook endgame) or impossible (knight + bishop)
- grok 4.20 managed to get checkmated and lose in a forced-winning scenario
- no model was able to beat an "odds" matchup[^4] I personally can beat comfortably. Which isn't really that meaningful
but not that surprising
- gemini flash produces extremely unhinged and incoherent messages in the place of valid SAN moves when the position 
gets too hard. I haven't reviewed the other message traces in detail yet, but 2 Knight + Move odds gemini flash sample 5 appears 
to contain an entire blog post ranting about the Invisible Hand of the Algorithm or something, complete with HTML formatting

I was surprised by the poor performance of Anthropic models, and ran this to confirm that the configured 
"medium" reasoning effort in OpenRouter wasn't the culprit.
- [Claude (reasoning\_effort=low,none)](/chessbench/run_logs/report_results_anthropic_low_none.html)



## Prior Art

[^1]: [GPTChessElo, 2023-09-30](https://blog.mathieuacher.com/GPTsChessEloRatingLegalMoves/)
(From what I can gather, apparently gpt-3.5-turbo-instruct was a standout chessplayer, but I didn't replicate this.)
[^2]: [LLM Chess Benchmark, 2023-Ongoing](https://chessbenchllm.onrender.com/timeline)
[^3]: [GPT-2 Chess Fine-Tune, 2020-01-05](https://x.com/theshawwn/status/1214013710173425665)
[^4]: [Wikipedia: Handicap Chess](https://en.wikipedia.org/wiki/Handicap_(chess)#Rating_equivalent)
