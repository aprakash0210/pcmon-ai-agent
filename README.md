# pcmon-ai-agent

> An agentic telemetry and hardware optimization assistant powered by LangGraph and classical ML.

## Overview & Goal
SpecPulse AI is an agentic AI system designed to diagnose PC bottlenecks and predict game performance. 
The core objective of this project was to bridge classical data science and modern agentic engineering by embedding custom-trained Scikit-Learn machine learning models as tools inside a deterministic LangGraph state machine.

## Key Features
- **Telemetry Bottleneck Diagnosis:** Classifies hardware logs into performance states (CPU-bound, GPU-bound, Thermal Throttling) using a Decision Tree Classifier.
- **Predictive FPS Engine:** Estimates continuous game frame rates across hardware configurations via a Random Forest Regressor.
- **Self-Correcting Recommendation Loop:** A LangGraph supervisor agent that iteratively evaluates hardware upgrades against target resolution/FPS metrics.

## System Architecture
```text
[ Hardware Logs / Specs ] ──► [ LangGraph Supervisor ]
                                    │
                  ┌─────────────────┴─────────────────┐
                  ▼                                   ▼
      [ Bottleneck Classifier Tool ]       [ FPS Regressor Tool ]
       (Scikit-Learn DecisionTree)          (Random Forest Model)
## Tech Stack & Core Concepts
Agent Orchestration: LangGraph, LangChain, Pydantic, LangSmith

Machine Learning & Data: Python, Pandas, NumPy, Scikit-Learn

Dev & Observability: Jupyter, Cursor, Claude Code

## Personal Learning Objectives
This project was built to gain proficiency in:

Feature scaling and matrix manipulation using Pandas and NumPy.

Model training, evaluation metrics (Accuracy, MAE), and artifact serialization (.pkl).

Designing state schemas, node routing, and fallback reflection loops in LangGraph.