# SpecPulse AI - Project Specification & Learning Blueprint

## 1. Primary Objective
Build an agentic hardware optimization system that analyzes live PC telemetry logs and predicts game performance to recommend upgrades. The project serves as a learning vehicle to transition from basic Python to an AI Engineer capable of orchestrating tabular ML models within LangGraph.

## 2. Target Tools & Skills to Master
- **Data Engineering:** Pandas (cleaning, resampling time-series logs, aggregation) and NumPy (matrix transformations, vectorization).
- **Machine Learning:** Scikit-Learn (`StandardScaler`, `DecisionTreeClassifier` for bottleneck diagnosis, `RandomForestRegressor` for FPS prediction, `joblib`/`pickle` serialization).
- **Agentic AI:** LangGraph (State schemas, tool node wrapping, conditional routing, reflection loops) and Pydantic (data validation).
- **Observability:** LangSmith (tracing agent states, execution latencies, and tool calls).

## 3. System Data Contracts

### A. Input Data Schemas
1. **Telemetry CSV Logs (`notebooks/data/telemetry_sample.csv`):**
   - `timestamp`: Datetime string
   - `cpu_utilization_pct`: float (0.0 - 100.0)
   - `gpu_temp_celsius`: float
   - `gpu_utilization_pct`: float (0.0 - 100.0)
   - `gpu_temp_celsius`: float
   - `vram_used_gb`: float
   - `ram_used_gb`: float

2. **User Chat Query Inputs (`src/state.py`):**
   - `target_game`: string (e.g., "Cyberpunk 2077")
   - `target_resolution`: string ("1080p", "1440p", "4K")
   - `target_fps`: integer (e.g., 60, 120)
   - `budget_usd`: float

### B. Expected Output Schemas
1. **Bottleneck Classifier Output (Tool Output):**
   - Enum: `["CLEAN", "CPU_BOUND", "GPU_BOUND", "THERMAL_THROTTLED"]`
   - Confidence Score: float

2. **FPS Regressor Output (Tool Output):**
   - `predicted_fps`: float
   - `meets_target`: boolean (`predicted_fps >= target_fps`)

3. **Final Agent Response:**
   - Diagnostic summary of the system telemetry.
   - Actionable upgrade recommendation if targets are missed.
   - Recommendations to optimize game performance according to pc specs

## 4. Technical Constraints
- **No Custom Neural Networks:** Do not use PyTorch or TensorFlow; focus entirely on Scikit-Learn tabular models.
- **Deterministic Tools:** The LLM must NOT estimate hardware stats or FPS. It MUST query the trained ML models via LangGraph tools.
- **Strict State Updates:** All node outputs in LangGraph must validate against `AgentState` via TypedDict/Pydantic.
