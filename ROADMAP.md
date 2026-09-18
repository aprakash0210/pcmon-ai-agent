# SpecPulse AI - Learning Roadmap
This document is to keep track of the progress of the project. Mark things as complete once t
## Active Phase: [ Phase 1 ]

- [ ] **Phase 1: Pandas & Telemetry Cleaning** (`notebooks/01_eda_and_cleaning.ipynb`)
  - [ ] Load raw hardware CSVs (CPU temps, GPU load, frame rates)
  - [ ] Handle missing values and scale continuous features with `StandardScaler`
- [ ] **Phase 2: Scikit-Learn Model Training** (`notebooks/02_models.ipynb`)
  - [ ] Train `DecisionTreeClassifier` for system bottleneck diagnosis
  - [ ] Train `RandomForestRegressor` for FPS prediction
  - [ ] Save artifacts as `.pkl` in `models/`
- [ ] **Phase 3: Tool Packaging** (`src/tools/`)
  - [ ] Wrap `.pkl` models into Python functions using `@tool`
- [ ] **Phase 4: LangGraph Orchestration** (`src/agent.py`)
  - [ ] Build `StateSchema`, supervisor node, and fallback reflection loop
