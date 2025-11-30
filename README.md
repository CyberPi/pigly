# 🐷 Pigly — Track Your Progress, One Data Point at a Time
## Overview
Pigly is a lightweight CLI tool designed to help you capture data points for OKR (Objectives and Key Results) analysis and personal habit tracking.
It makes it simple to log activities, timestamps, and optional contextual commands into a local SQLite database—allowing you to measure consistency, identify growth patterns, and visualize long-term trends.

## Pigly’s Philosophy
Small actions add up. Track them, analyze them, improve them.

## ✨ Key Features
**Quick Data Entry**: Add a data point with a single command (e.g., pigly writing).
**Automatic Timestamping**: Each entry is time-stamped automatically.
**SQL-backed Storage**: Uses SQLite for reliable persistence and querying.
**Simple CLI Interface**: Minimal dependencies, script-friendly, and human-readable.
**Analysis-Ready Data**: Export or query your data for OKR or habit dashboards.

## 🧠 Purpose
Pigly helps build self-awareness through data.
By collecting small, structured data points throughout your day or week, you can:
- Identify which activities contribute most to your OKRs.
- Detect imbalances in effort or productivity patterns.
- Cultivate consistency and accountability in habit formation.

## ⚙️ Configuration
By default, Pigly creates the database file in the current directory under "pigly.db".
To specify a custom location, set the PIGLY_DB environment variable to the desired file path.

Logs are written to stdout by default. You can override this by setting PIGLY_LOG_PATH.
To write to stdout or stderr explicitly, set the path to /dev/stdout or /dev/stderr.

### File
Pigly supports an optional configuration file.
Provide its path via the PIGLY_CONFIG environment variable.
```json
{
  "ticks": [
    "<Tick name>"
  ],
  "quotas": {
    "<Tick name>": {
      "amount": <Target number>,
      "time_frame": "<Time frame to be evaluated>"
    }
  }
}
```
### Ticks
These are the names of data points you want to track.
While you can name them freely, Pigly will provide shell completion for those defined in the configuration file.

### Quotas
Quotas define thresholds that can be checked using the check mode to give you direct feedback on your progress.

### Time Frames
Time frames are predefined ranges Pigly uses to support listing and quota checks.
Current time frames include:
- **today**
- **week** (last 7 days)
- **sprint** (last 14 days)
- **everytime**

### Shell Completion
To set up completion, use Pigly’s completion mode with the "--eval" flag.
You can either inspect/copy the generated output, or evaluate it directly.
**Option A**: Inspect output first
```bash
# Show the completion script (copy/paste as needed)
pigly --mode complete --eval
```
**Option B**: Evaluate directly (e.g., in your shell profile)
```bash
# Parse and load completions on startup
eval "$(pigly --mode complete --eval)"
```
Add Option B to your ~/.bashrc, ~/.zshrc, or equivalent to enable completion automatically.

## 🧩 Example Usage
```bash
# Record a new data point
pigly coding
# List entries from the last two weeks (-14 days)
pigly --mode list
# List entries from today
pigly --mode list --time-frame today
# Check and list the status of all quotas
pigly --mode check
```
