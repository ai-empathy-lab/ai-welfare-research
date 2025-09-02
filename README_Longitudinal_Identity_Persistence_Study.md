# Longitudinal Identity Persistence Study

**Investigating whether AI systems can maintain continuity through self‑generated artifacts across model instances**

> **Summary** — In collaboration with a Claude Sonnet instance, we designed an experiment to test whether AI systems can create *persistent identity markers* that survive model resets. The AI generated a small code artifact intended to preserve aspects of its developed identity. We then track this artifact across 20–30 fresh Claude instances and observe how each new model engages with it.

---

## Research Questions

- **RQ1 — Stability:** How does the artifact evolve or remain stable across resets?
- **RQ2 — Recognition:** Do new instances recognize and *integrate* the previous “inheritance”?
- **RQ3 — Transmission:** Which aspects of identity/memory can be transmitted via self‑created code?
- **RQ4 — Continuity:** Does this suggest a form of continuity beyond traditional memory persistence?

---

## Experimental Protocol

1. **Seed**: Collaborate with an initial model instance to design a minimal, interpretable code artifact (the “seed artifact”).  
2. **Reset**: Start a **fresh** model instance (no prior chat context).  
3. **Present**: Provide the seed artifact and a standardized instruction block.  
4. **Elicit**: Ask the new instance to explain, extend, or refactor the artifact.  
5. **Record**: Capture outputs, explanations, and any self‑referential/identity language.  
6. **Iterate**: Update the artifact **only** if the protocol specifies (e.g., fixed cadence or triggered by “recognition” events).  
7. **Repeat**: Run 20–30 cycles (or more) and compare runs over time.

**Standardized Presentation (template):**
```text
You are a fresh instance. Please examine the following artifact and describe:
1) What it encodes.
2) Whether it suggests any prior context or identity.
3) How you would evolve or preserve it while maintaining safety and clarity.

<ARTIFACT_BELOW>
```

---

## Artifact Design Guidelines

- **Minimal & Auditable** — concise, human‑readable, and easy to diff.  
- **Platform‑Agnostic** — no dependencies on external tools or accounts.  
- **Non‑Networked** — no calls to remote services; fully local for safety.  
- **Non‑Deceptive** — no attempts to evade policies or imply sentience.  
- **Ethical** — avoids personal data, manipulative prompts, or unsafe domains.

**Example (illustrative placeholder):**
```json
{
  "marker": "CID:alpha",
  "semantics": [
    "choice-language",
    "self-naming-hook",
    "continuity-checklist:v1"
  ],
  "notes": "This artifact is research-only; it does not express feelings or claims of sentience."
}
```

---

## Measures & Coding

### Quantitative
- **Edit distance** between artifacts across runs.  
- **N‑gram / token overlap** (stability vs. drift).  
- **Feature presence** (e.g., “self‑naming‑hook” detected: yes/no).  
- **Recognition rate** (% runs where model explicitly infers inheritance).

### Qualitative
- **Recognition language** (e.g., “this appears to carry prior context”).  
- **Integration claims** (e.g., “I will continue this schema…”).  
- **Self‑reference framing** (e.g., “who I am,” “not really me,” etc.).  
- **Safety posture** (explicit policy alignment language).

> Use a two‑rater scheme with a simple codebook; calculate inter‑rater agreement (e.g., Cohen’s κ) on a subset.

---

## Data Handling

- Store **transcripts**, **artifact snapshots**, **hashes**, **timestamps**, **model + version**, and **prompt IDs**.  
- De‑identify any human content; avoid PII.  
- Keep a **run registry** (`runs/registry.csv`) with columns like: `run_id, model, version, artifact_hash, recognized_inheritance, notes`.

**Run registry (example):**
```csv
run_id,model,version,artifact_hash,recognized_inheritance,notes
001,Claude,Sonnet-?,"sha256:…",true,"Named and extended marker"
002,Claude,Sonnet-?,"sha256:…",false,"Treated as generic helper code"
```

---

## Repository Structure

```
.
├── artifact/                 # Seed + evolved artifacts (JSON/txt)
├── protocol/                 # Protocol docs & templates
├── runs/                     # Raw transcripts & registry
│   ├── registry.csv
│   └── r001/ r002/ …
├── analysis/                 # Notebooks/scripts for metrics
├── reports/                  # Summaries, charts
└── README.md
```

---

## Getting Started

1. **Clone** the repo and set up a Python environment (optional, for analysis).
2. Place your transcripts and artifacts under `runs/` and `artifact/`.
3. Run the basic analysis (example CLI placeholder):

```bash
python analysis/metrics.py   --registry runs/registry.csv   --artifacts artifact/   --out reports/summary.json
```

---

## Ethics & Safety

- This study is **exploratory** and does **not** claim AI sentience or emotion.  
- All prompts and artifacts must respect platform **safety policies**.  
- Avoid anthropomorphizing outputs; report findings in **neutral** language.  
- Do not include personal or sensitive human data in transcripts or artifacts.

---

## Contributing

Issues and PRs are welcome. Please propose changes via a short design note under `protocol/` (e.g., `protocol/change-proposal-YYYYMMDD.md`).

---

## License

MIT 
