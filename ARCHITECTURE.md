# Architecture (Reference)

## High-level
- UI: chat interface with citations
- API: `/ask` orchestrates retrieval + generation
- Retrieval: embeddings index over course materials
- LLM: instruction-tuned with syllabus-aware prompt policy
- Guardrails: refuse out-of-scope topics; prefer citations

```mermaid
graph TD
  UI[Chat UI] -->|question| API[FastAPI /ask]
  API -->|retrieve top-k| IDX[Embeddings Index]
  ETL[Ingest + Chunk] --> EMB[Embedding Model]
  EMB --> IDX
  API -->|context+prompt| LLM[LLM]
  LLM -->|answer + citations| UI
```
