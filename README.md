# James Finn

**Software engineer building private, local AI systems** — LLM inference, retrieval, and agentic orchestration that run entirely on hardware the client controls.

🌐 [veniceinference.com](https://veniceinference.com)

---

## A few things about me

### Systematic futures — the Turtle lineage

For nearly 25 years I was the lead developer and chief operator for Rabar Market Research, Inc., a CTA spawned from the Richard Dennis and Bill Eckhardt Turtle Program. Rabar managed about $90M when I started and roughly $800M at its peak.

I built essentially the entire stack: cross-platform HPC simulations, applications to manage price data, order generation, trades, rollovers, and additions/withdrawals. I controlled the "Crown Jewels", i.e. system parameters and weights, portfolio composition and weighting, and account balances and weights.

The simulators searched for robust systems in two ways. *Brute force* swept a defined set of parameter combinations, then a second program extracted high-performing "neighbor" clusters. *Genetic* search covered a far larger parameter space, locating robust clusters in process.

Accuracy was enforced structurally. We grew from one research group, consisting primarily of myself and Paul, to three groups in three locations: Dr. Francisco Vaca lead our Chicago office R&D, along with another Fermilab physicist, and an engineer, on the East Coast, a mathematician and a programmer, and myself in Los Angeles. 

No group shared code. Before launching any large simulations runs, i.e. simulations that would be processing a large set of parameter combinations, the system code was re-implemented independently, and results of parameter subset were cross-checked to three decimals. 

Daily I made the final call whether orders were good to go — which meant our real-time and simulated positions were an exact match, and every discrepancy was examined and resolved, e.g. proving a rounding error was a rounding error.

### From the metal up

I ran Rabar's mission-critical infrastructure end to end — selecting, administering, and maintaining all production hardware, including servers, switches, firewalls, and the 150 rack servers I installed and maintained at a USC colo — while writing, debugging, and executing nearly all of our C/C++, C#, and SQL system code. 

### Security

A parallel track since reading *The Cuckoo's Egg* in 1989 — for years my browser homepages were stacked with comp-sec sites for a steady daily read. Around 2013, when I realized the scale of hacking operations was about to go thermal. So, I began experimenting with Backtrack/Kali, Cain & Abel, and related. More recently: wiring/executing exploit chains like EternalBlue/DoublePulsar in isolation, working thru various PicoCTF challenges, and rooting 14 machines on Hack The Box.

### AI & LLM inference

My first LLM work was at BigBear AI — RAG applications and a C/C++ OpenVINO/ONNX inference-optimization engine. More recently, capitalizing on my BBAI experience, I built **BDS (Batch Document Search)**, a private RAG platform on a PySide6 / FastAPI architecture with hybrid ChromaDB retrieval (BGE + BM25, fused via RRF and cross-encoder re-ranking), GLiNER entity extraction, and a knowledge-graph with 97% accurate linkage, i.e. QA fixed all but ~3% of the dangling links, leaving a high fidelity fully-connected graph.

I've benchmarked inference backends — vLLM and llama.cpp — for sustained local serving. On a Windows 10 host running WSL2 (Ubuntu 24.04), llama.cpp proved the more stable under continuous load, avoiding the GPU-wedge failures that bit the alternative. 

### Agentic Orchestration with Hermes/Gemma

VIOSINT — a privacy-first OSINT subsystem now embedded in my BatchDocumentSearch platform. 

Claude and I, together, planned five test-gated phases, with Claude crafting the prompts, where we used a fully local coding agent, Hermes, running Gemma 4 31B served offline via Ollama, so nothing would leave my hardware. Claude and I monitored everything Hermes was doing until eventually I determined it was time for Claude to take over.

Phase 1 and the adapter scaffolding came out clean, but Phase 2 exposed a subtler failure mode: on small-but-contextual integration work — wiring a single tool adapter into an orchestrator that already existed — the model would narrate what it was about to do, then loop on the narration or edit something adjacent instead of doing it. 

Hardening the system prompt with explicit "do the work, don't describe it" constraints didn't take. So, at the Phase 2→3 boundary, with the trailing tests green, I passed the baton to Claude Opus and finished phases 3–5, shipping viosint_core as a standalone library. 

The lesson I kept: mid-project agent handoff is a maneuver, not a failure — recognizing when your AI has stopped converging, and acting on it at a clean boundary, is the human-shaped part of the job.

---

🌐 [veniceinference.com](https://veniceinference.com) · 📫 jf.technical@outlook.com
