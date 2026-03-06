## What this skill does and when to use it:

The skill-gap-finder solves a specific problem that comes up whenever you're building or improving a Claude skill: your benchmarks show 100% vs 100% because the test cases are too easy — Claude already handles them well without any guidance.

You use it by pointing it at a skill you're building and describing what that skill does. It then works through a structured process: first it reasons about the specific ways Claude tends to fall short in that domain (knowledge cutoff, inability to do web research, tendency to list options instead of making recommendations, skipping steps in a process, etc.). Then it generates 12–15 candidate hard prompts, reasons carefully about which ones baseline Claude would genuinely fail on, and filters down to the 5–8 most discriminating ones. The output is a ready-to-use evals.json in the skill-creator format, with each test case annotated with why it's hard and what exactly baseline Claude gets wrong.
The recursive test we just ran proved this works: when we used the skill on itself, it scored 100% vs 17% against baseline — a real +0.83 delta — because it followed the structured filtering process rather than just brainstorming hard-sounding prompts. The baseline produced complex scenarios, but the skill produced prompts that specifically targeted failure modes, which is what makes benchmarks actually discriminating.

In practice, you'd use it early in the skill-creation loop — before running your main evals — to make sure you're not wasting time benchmarking against easy cases.
