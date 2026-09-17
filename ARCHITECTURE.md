# System Architecture

## Target Telemetry Features (Input)
- `cpu_utilization_pct`: float
- `gpu_utilization_pct`: float
- `gpu_temp_celsius`: float
- `vram_used_gb`: float

## ML Model Contracts
- **Bottleneck Classifier**: Inputs 4 telemetry features -> Outputs class `[0: Clean, 1: CPU Bound, 2: GPU Bound, 3: Thermal]`
- **FPS Regressor**: Inputs `[hardware_tier, target_resolution, game_preset]` -> Outputs continuous `predicted_fps`

## LangGraph State Schema
```python
class AgentState(TypedDict):
    messages: Annotated[list, add_messages]
    system_metrics: dict
    bottleneck_status: str
    target_fps: int
    predicted_fps: float