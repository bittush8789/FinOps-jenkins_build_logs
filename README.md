# FinOps | Reduce Cloud Cost for CI/CD Logging

A shell script to help reduce cloud cost by managing Jenkins build logs.  
Automatically cleans up old logs or large logs, keeping only what’s needed for audits or debugging.

---

## Table of Contents

- [Problem](#problem)  
- [Solution](#solution)  
- [How It Works](#how-it-works)  
- [Usage](#usage)  
- [Configuration](#configuration)  
- [Requirements](#requirements)  
- [License](#license)  

---

## Problem

CI/CD pipelines, especially Jenkins, tend to generate a large number of build logs over time. These logs:

- occupy storage (cloud or on-premises)  
- increase backup/archival costs  
- can slow down system operations or search/retention policies  

Over time, inefficiencies in log retention lead to higher operational costs and wasted storage.

---

## Solution

This repo provides a script (`reduce_loudcost_jenkins.sh`) to automate the cleanup of Jenkins build logs, helping to:

- delete or archive old logs  
- limit log retention period or size  
- reduce storage usage and cost  

---

## How It Works

1. The script identifies log files/folders based on certain criteria (e.g. age, size).  
2. Optionally archives logs that are old but may still be needed.  
3. Deletes logs that exceed the retention policy or size threshold.  
4. Logs its own actions so you can audit what was removed or kept.

---

## Usage

```bash
# Make sure script is executable
chmod +x reduce_loudcost_jenkins.sh

# Dry run - see what would be deleted/archived without making changes
./reduce_loudcost_jenkins.sh --dry-run

# Actual cleanup
./reduce_loudcost_jenkins.sh --cleanup
