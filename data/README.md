# Dataset

This directory contains the final datasets used for the
AI-Based Workload Behavior Analyzer & System Optimization Agent.

## Final Datasets

### 1. System Metrics

File:

`raw/merged_system_metrics.csv`

- Rows: 2,700
- Columns: 29
- Workload conditions: 9
- Samples per workload: 300

This dataset captures system-level resource behavior including
CPU, memory, disk, network, load, swap and CPU-frequency metrics.

It is primarily used for workload characterization, classification,
anomaly detection, forecasting, SLA-risk analysis and system-level
behavior analysis.

### 2. Process Metrics

File:

`raw/merged_process_metrics.csv`

- Rows: 170,634
- Columns: 12

This dataset captures process-level behavior including process CPU
utilization, memory utilization, thread count and process status.

It is primarily used for fine-grained process analysis and
root-cause identification.

## Dataset Relationship

The two datasets provide complementary views of system behavior.

System-level metrics answer:

> What is happening to the overall system?

Process-level metrics answer:

> Which processes may be responsible for the observed behavior?

Together, they provide a hierarchical view of workload behavior
that supports the project's analysis and optimization pipeline.

## Workload Categories

The final system dataset contains nine workload categories:

1. Normal
2. CPU-intensive
3. Memory-intensive
4. Network-intensive
5. Disk-intensive
6. Bursty
7. Gaming
8. Stress
9. Mixed

Each workload contains 300 system-level observations.
