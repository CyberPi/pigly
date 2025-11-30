# 🐷 Pigly — Track Your Progress, One Data Point at a Time
## Overview
Pigly is a lightweight CLI tool designed to help you capture data points for OKR (Objectives and Key Results) analysis and personal habit tracking.
It makes it simple to log activities, timestamps, and optional contextual commands into a local or remote SQL database, enabling you to measure consistency, identify growth patterns, and visualize long-term trends.

## Pigly’s philosophy is simple:
Small actions add up! Track them, analyze them, improve them.

## ✨ Key Features
- Quick Data Entry: Add a data point with a single command (e.g. pigly writing).
- Automatic Timestamping: Each entry is automatically time-stamped.
- SQL-backed Storage: Uses SQLite or another SQL backend for persistence and querying.
- Simple CLI Interface: Minimal dependencies, script-friendly, and human-readable.
- Analysis-Ready Data: Export or query your data for OKR or habit dashboards.

## 🧠 Purpose
Pigly helps build self-awareness through data.
By collecting small, structured data points throughout your day or week, you can:
Identify which activities contribute most to progress toward your OKRs.
Detect unbalanced effort or productivity patterns.
Cultivate consistency and accountability in habit formation.

## ⚙️Configuration
To setup completion. Add output of the completion mode, with eval flag to your shell profile.
```bash
"pigly --mode complete --eval"
```

Pigly come with a very basic configuration that can be overwritten via a file. The File path needs to be set via environment variable. "PIGLY_CONFIG"
```json
{
  "ticks": [
    "<Tick name>"
  ],
  "quotas": {
    "<Tick name>": {"amount": <Target number>, "time_frame": "<Time frame that is queried for this quota>"}
  }
}
```

## 🧩 Example Usage
```bash
# Record a new data point
pigly coding

# Query the entries of the last two weeks (-14 days)
pigly --mode list

# Query the entries of the current day
pigly --mode list --time-frame today

# Check and list the status of the current quotas
pigly --mode check
```
