# Engine

The engine is how BreathOS acts on the world — and how the world acts on BreathOS.

## Scripts

| Script | Purpose | Status |
|--------|---------|--------|
| `scan.py` | Probe a topic, output a delta file | v0.1 scaffold |
| `evaluate.py` | Score and compare options | *planned* |
| `update.py` | Trigger map updates from delta files | *planned* |

## Running scan.py

```bash
# Install dependency
pip install anthropic

# Set API key
export ANTHROPIC_API_KEY=your_key_here

# Run a scan
python engine/scan.py --topic "Llama 4 local inference" --cluster models

# Output: log/YYYY-MM-DD-delta-llama-4-local-inference.md
```

## Design principle

The engine outputs delta files to `/log/` — it never writes directly to `/map/`. The human reviews deltas before they become map updates. The engine is a sensor and a draft generator. The navigator decides what to commit.
