# James Finn

**Software engineer building private, local AI systems** — LLM inference, retrieval, and agentic orchestration that run entirely on hardware the client controls.

🌐 [veniceinference.com](https://veniceinference.com)

---

## A few things about me

### Systematic futures — the Turtle lineage

For nearly 25 years I was the lead developer and chief operator for Rabar Market Research, Inc., a CTA spawned from the Richard Dennis and William Eckhardt Turtle Program. Rabar managed about $90M when I started and roughly $800M at its peak.

I built essentially the entire stack: cross-platform HPC simulations, applications to manage price data, order generation, trades, rollovers, and additions/withdrawals. I controlled the "Crown Jewels", i.e. system parameters and weights, portfolio composition and weighting, and account balances and weights.

The simulators searched for robust systems in two ways. *Brute force* swept a defined set of parameter combinations, then a second program extracted high-performing "neighbor" clusters. *Genetic* search covered a far larger parameter space, locating robust clusters in process.

Accuracy was enforced structurally. Three research groups wrote independent code, we shared nothing. Every system concept tested was verified between groups, i.e. at least two groups ran a set of parameter combinations, compared results, and flagged any discrepancies that mismatched at two decimals. All discrepancies were explained, or resolved, before launching any large-scale simulation runs. 

As Chief Operator, I made the daily final call whether orders were good to go — which meant our real-time and simulated positions were an exact match, and every discrepancy was examined and resolved. If good, the orders were sent to New York RMR trading department for execution.

### From the metal up

I ran Rabar's mission-critical infrastructure end to end — selecting, administering, and maintaining all production hardware, including servers, switches, firewalls, and the 150 rack servers we housed at USC colo, which I maintained. While R&D continued, I executed all daily trade processing and order generation routines. 

### Security

Reading *The Cuckoo's Egg: Tracking a Spy Through the Maze of Computer Espionage* in 1989, prompted a parallel path of study, computer security. For years my browser homepages were stacked with comp-sec sites for a steady daily read. Around 2013, speculating the scale of hacking operations was about to go thermal, I began experimenting with Backtrack/Kali, Cain & Abel, and related tooling. Subsequently, I wired and executed exploit chains like Eternal Blue/Double Pulsar in isolation, worked through CTF challenges primarily at PicoCTF, and rooted 14 machines at Hack the Box.

### AI & LLM inference

My first LLM work was at BigBear AI — RAG applications and a C/C++ OpenVINO/ONNX inference-optimization engine. More recently, capitalizing on my BBAI experience, I built **BDS (Batch Document Search)**, a private RAG platform on a PySide6 / FastAPI architecture with hybrid ChromaDB retrieval (BGE + BM25, fused via RRF and cross-encoder re-ranking), GLiNER entity extraction, and a knowledge-graph with 98.2% accurate linkage on a 100-document Boeing/NTSB benchmark, i.e. QA fixed all but ~1.8% of the dangling links, leaving a high fidelity fully-connected graph.

I've benchmarked inference backends — vLLM and llama.cpp — for sustained inference. On a Windows 10 host running WSL2 (Ubuntu 24.04), llama.cpp proved the more stable under continuous load, avoiding the GPU-wedge failures that bit the alternative. 

### Agentic Orchestration with Hermes/Gemma

VIOSINT — a privacy-first OSINT subsystem now embedded in my BatchDocumentSearch platform began as a Kali Python project requiring enhancements. This seemed a good opportunity to see if Hermes could effectively enhance existing features, and add new ones.  

Claude and I, together, planned five test-gated phases, with Claude crafting the prompts, where we used a fully local coding agent, Hermes, running Gemma 4 31B served offline via Ollama, so nothing would leave my hardware. 

Phase 1 and the adapter scaffolding came out clean, but Phase 2 exposed a subtler failure mode: on small-but-contextual integration work — wiring a single tool adapter into an orchestrator that already existed — the model would narrate what it was about to do, then loop on the narration or edit something adjacent instead of performing it's prescribed task. I determined it was time for Claude to take over, and get it done.

Hardening the system prompt with explicit "do the work, don't describe it" constraints didn't take. So, at the Phase 2→3 boundary, with the trailing tests green, I passed the baton to Claude Opus which finished phases 3–5, shipping VIOSINT Core as a standalone library.

The lesson: mid-project agent handoff is a maneuver, not a failure — recognizing when your AI has stopped converging, and acting on it at a clean boundary, is the human-shaped part of the job.

---

🌐 [veniceinference.com](https://veniceinference.com) · 📫 jf.technical@outlook.com
