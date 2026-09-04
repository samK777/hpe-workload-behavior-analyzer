# Dataset Documentation

## 1. Overview

This document describes the datasets used in the
**AI-Based Workload Behavior Analyzer & System Optimization Agent**.

The project uses two complementary datasets:

1. `merged_system_metrics.csv`
2. `merged_process_metrics.csv`

The system-level dataset captures overall resource behavior of the
machine under different workload conditions, while the process-level
dataset provides finer-grained information about individual processes.

Together, these datasets provide a hierarchical view of system behavior,
from overall resource utilization to individual process activity.

---

## 2. Final Datasets

### 2.1 System Metrics Dataset

**File:** `merged_system_metrics.csv`

| Property | Value |
|---|---:|
| Rows | 2,700 |
| Columns | 29 |
| Workload categories | 9 |
| Samples per workload | 300 |
| Experiments | 3 |

The system metrics dataset contains measurements describing the overall
state and resource utilization of the system.

The dataset includes metrics related to:

- CPU utilization
- Memory utilization
- Disk activity
- Network activity
- System load
- Swap utilization
- CPU frequency
- CPU/core-level metrics
- Timestamp and workload identifiers

This dataset is primarily intended for system-level workload analysis,
workload characterization, classification, clustering, anomaly detection,
forecasting, SLA-risk analysis, and optimization.

---

### 2.2 Process Metrics Dataset

**File:** `merged_process_metrics.csv`

| Property | Value |
|---|---:|
| Rows | 170,634 |
| Columns | 12 |
| Process statuses | Running, Stopped |

The process metrics dataset provides process-level information associated
with the observed workloads.

The dataset contains information including:

- Process ID (PID)
- Process name
- Process CPU utilization
- Process memory utilization
- Thread count
- Process status
- Timestamp
- Sample and workload identifiers

This dataset is primarily intended for fine-grained process analysis and
root-cause identification.

---

## 3. Workload Categories

The final system-level dataset contains nine workload categories:

1. Normal
2. CPU-intensive
3. Memory-intensive
4. Network-intensive
5. Disk-intensive
6. Bursty
7. Gaming
8. Stress
9. Mixed

Each workload category contains **300 system-level samples**.

Therefore, the system-level dataset is evenly distributed across the
nine workload categories, with each category representing approximately
**11.11%** of the dataset.

---

## 4. Experiment Distribution

The final system-level dataset was collected across three experiments.

| Experiment | Workload(s) | System Samples | Percentage |
|---|---|---:|---:|
| EXP001 | Normal, CPU-intensive, Memory-intensive, Network-intensive, Bursty, Gaming, Stress | 2,100 | 77.78% |
| EXP004 | Disk-intensive | 300 | 11.11% |
| EXP006 | Mixed | 300 | 11.11% |
| **Total** | **9 workloads** | **2,700** | **100%** |

The experiments collectively cover all nine workload categories used in the
final dataset.

---

## 5. Process-Level Workload Distribution

The process-level dataset contains the following distribution of records
across workload categories:

| Workload | Process Records | Percentage |
|---|---:|---:|
| Stress | 26,434 | 15.49% |
| Memory-intensive | 24,634 | 14.44% |
| Disk-intensive | 24,526 | 14.37% |
| Mixed | 21,373 | 12.53% |
| CPU-intensive | 17,164 | 10.06% |
| Network-intensive | 17,174 | 10.06% |
| Bursty | 14,503 | 8.50% |
| Normal | 14,092 | 8.26% |
| Gaming | 10,734 | 6.29% |
| **Total** | **170,634** | **100%** |

Unlike the system-level dataset, process-level records are not evenly
distributed because a single system observation can contain information
from multiple processes.

---

## 6. Data Quality Checks

Initial validation was performed on both final datasets.

### System Metrics

- No missing cells were identified.
- No duplicate rows were identified.
- All nine workload categories are represented.
- Each workload contains 300 system-level samples.

### Process Metrics

- No duplicate rows were identified.
- `process_name` contains 271 missing values.
- Process status values include:
  - `running`
  - `stopped`

The missing process names will be considered during preprocessing and
root-cause analysis.

---

## 7. Dataset Relationship

The two datasets represent different levels of system observation.

### System-Level View

The system metrics dataset answers:

> **What is happening to the overall system?**

It captures aggregate behavior such as CPU, memory, disk, network,
load, and other system-level resource metrics.

### Process-Level View

The process metrics dataset answers:

> **Which processes may be responsible for the observed behavior?**

It provides process-specific resource utilization and activity.

### Combined View

The relationship between the datasets enables the project to move from:

```text
System Behavior
      ↓
Workload Identification
      ↓
Abnormal / Significant Behavior
      ↓
Process-Level Investigation
      ↓
Potential Root Cause
      ↓
Optimization Decision
