# MesaProject Repository Structure

MesaProject/
├── agents/
│   ├── wild_spark.py           # Contains the WildSpark agent class
│   └── style_state.py          # Manages the StyleState dataclass for personality
├── model/
│   ├── simulation.py           # Houses run_consciousness_simulation and ConsciousnessModel
│   └── analyzer.py             # Includes analyze_consciousness_patterns and chart generation
├── data/
│   ├── logs/
│   │   └── spark_debug.log     # Log file for debugging output
│   ├── kinflare_memory_db/     # Directory for ChromaDB persistence (if enabled)
│   └── spark_states/           # Directory for style and state JSON files (e.g., spark_X_state.json)
├── analysis/
│   └── metrics.ipynb           # Jupyter notebook for analyzing simulation data
├── docs/
│   └── README.md               # Project overview, setup instructions, and usage
└── requirements.txt            # Dependency list for the project
