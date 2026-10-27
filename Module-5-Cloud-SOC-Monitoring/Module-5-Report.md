# Module 5: Cloud SOC Monitoring — Comprehensive Lab Report

## 📋 Module Overview

This module explores the unique challenges of Security Operations in cloud environments. Unlike traditional on-premises networks, cloud security relies heavily on API logs, identity and access management (IAM), network-flow data, and the shared responsibility model.

The primary objective of this module was to ingest a public intrusion detection dataset, **CSE-CIC-IDS2018**, into Splunk Enterprise and explore how large-scale network traffic data can be searched and analyzed in a SIEM environment.

## 🎯 Module Objectives

The objectives of this module are:

1. **Cloud Fundamentals:** Understand the Shared Responsibility Model and key cloud log sources, including AWS CloudTrail and Azure Activity Logs.
2. **Dataset Ingestion:** Download and ingest a sample of the CSE-CIC-IDS2018 dataset into Splunk.
3. **Data Analysis:** Use Splunk searches to examine large-scale network-flow data.
4. **Handling Large Data:** Understand the challenges of processing large CSV files in a SIEM environment.

---

## 🛠️ Tools & Technologies Used

| Component | Details |
|---|---|
| SIEM Platform | Splunk Enterprise v10.0.2 |
| Dataset | CSE-CIC-IDS2018 |
| Operating System | Kali Linux VM |
| Data Format | CSV (Comma-Separated Values) |
| Dataset Example | `Thursday-15-02-2018_TrafficForML_CICFlowMeter.csv` |
| Target Index | `main` |
| Sourcetype | `csv` |

---

# 🔬 Lab 1: Ingesting the CSE-CIC-IDS2018 Dataset into Splunk

## 1.1 Objective

Simulate a cloud-security monitoring workflow by ingesting a public intrusion detection dataset into Splunk Enterprise and verifying that the imported data is searchable.

**Note:** CSE-CIC-IDS2018 is a network intrusion detection dataset containing network traffic and flow features. Ingesting it into Splunk demonstrates SIEM data handling and traffic analysis; it does not, by itself, establish that actual cloud-provider audit logs were collected.

## 1.2 Detailed Execution Steps

### Step 1: Download a Sample Dataset

Obtain an appropriate CSV file from the CSE-CIC-IDS2018 dataset.

Example file:

```text
Thursday-15-02-2018_TrafficForML_CICFlowMeter.csv
```

The dataset may contain a large number of rows and columns, so check the file size and available disk space before importing it.

### Step 2: Configure the Splunk Data Input

Open the Splunk Web interface and navigate to:

**Settings → Data Inputs → Files & Directories**

Then:

1. Select **New Local File & Directory**.
2. Enter the CSV file path:

   ```text
   /home/iftiur/Downloads/Thursday-15-02-2018_TrafficForML_CICFlowMeter.csv
   ```

3. Set the sourcetype to:

   ```text
   csv
   ```

4. Select the index:

   ```text
   main
   ```

5. Review the configuration and save the input.

**Important:** The path above is specific to the example environment. Replace `/home/iftiur/Downloads/` with the actual directory containing your dataset. Splunk must have permission to read the file.

### Step 3: Verify Data Ingestion

After the file has been processed, open Search & Reporting and run:

```spl
index=* sourcetype=csv
```

This searches across accessible indexes for events assigned the `csv` sourcetype.

To narrow the search to the configured index, use:

```spl
index=main sourcetype=csv
```

Set an appropriate time range so that the imported events are included.

### Step 4: Verify the Event Count

In the lab, the search reportedly returned **34,180 events**.

Use the following query to count matching events:

```spl
index=main sourcetype=csv
| stats count AS total_events
```

Compare the result with the search interface and the original lab evidence.

The count of 34,180 is the reported result from this lab, not a universal event count for the CSE-CIC-IDS2018 dataset. The result can vary depending on the file, ingestion settings, parsing behavior, and time range.

## 1.3 Expected Outcome & Verification

**Expected outcome:**

- The CSV file is configured as a Splunk data input.
- Events are indexed and searchable.
- The imported data can be queried using SPL.
- The number of indexed events can be checked.

**Verification:** The lab reported 34,180 matching events. Confirm this number against your own Splunk search results before presenting it as a verified outcome.

## 1.4 Key Learnings & Troubleshooting

- **Large Files:** Importing CSV files hundreds of megabytes in size can consume substantial CPU, memory, disk space, and indexing resources.
- **Sourcetype:** The sourcetype influences how Splunk interprets and processes incoming data. Selecting `csv` alone does not guarantee that every column will be extracted as an individual field.
- **File Permissions:** Splunk must be able to read the source file.
- **Search Time Range:** Ensure that the selected time range includes the indexed events.
- **Internal Logs:** Splunk internal events can help diagnose ingestion problems.

For example, inspect relevant internal events with:

```spl
index=_internal
```

To narrow the search to recent error messages, use:

```spl
index=_internal (log_level=ERROR OR log_level=WARN)
```

The exact fields and available messages depend on the internal events generated by the installation.

---

# 🏛️ Cloud Data Ingestion Workflow

The following diagram summarizes the data-ingestion and analysis process used in this lab.

```mermaid
flowchart LR
    A["Cloud Traffic Dataset<br/>(CSE-CIC-IDS2018)"] --> B["Splunk Data Input<br/>(CSV File)"]
    B --> C["Splunk Indexer<br/>(Parsing & Storage)"]
    C --> D["Splunk Search<br/>(SPL Queries)"]
    D --> E["Traffic Analysis<br/>(Patterns & Anomalies)"]

    classDef step fill:#1f3a5f,color:#fff,stroke:#0e1f33,stroke-width:2px
    class A,B,C,D,E step
```

---

## 📸 Screenshots & Evidence

### Screenshot 1 — Data Input Configuration

*This screenshot shows the configuration used to ingest the CSE-CIC-IDS2018 CSV dataset into Splunk.*

![Data Input Configuration](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-5-Cloud-SOC-Monitoring/Labs/lab13-cloud-data-input.png)

### Screenshot 2 — Cloud Traffic Search Results

*This screenshot shows the ingested traffic data being searched in Splunk. The reported lab result is 34,180 events.*

![Cloud Traffic Search Results](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-5-Cloud-SOC-Monitoring/Labs/lab13-cloud-data-search.png)

---

## 💡 Key Takeaways from Module 5

1. **Cloud Logs and Network Data:** Cloud-security investigations may involve API audit logs, identity events, network-flow records, and other telemetry sources.
2. **Scalability:** Large datasets require careful planning for storage, ingestion, parsing, and search performance.
3. **Shared Responsibility Model:** Cloud providers and customers have different security responsibilities. Customers remain responsible for securing the resources, identities, configurations, and data assigned to them, while the provider's responsibilities depend on the service model.
4. **Continuous Monitoring:** Cloud resources and identities can change rapidly, making ongoing monitoring and investigation important.
5. **Data Validation:** Event counts and field extraction should be verified against the actual dataset and Splunk configuration.
6. **SIEM Investigation:** Splunk can help analysts search network-flow data and identify patterns that warrant further investigation.

---

## ✅ Module 5 Completion Checklist

Mark each task as complete only after performing and verifying it.

- [x] Reviewed cloud-security fundamentals and the Shared Responsibility Model.
- [x] Downloaded a sample of the CSE-CIC-IDS2018 dataset.
- [x] Configured the CSV file as a Splunk data input.
- [x] Searched the imported data using SPL.
- [x] Reviewed the reported ingestion result of 34,180 events.
- [x] Documented the lab procedure with screenshots.

**Note:** Keep an item checked only if you personally completed and verified the task. If a step is unfinished or the event count has not been confirmed, change its marker from `[x]` to `[ ]`.

---

## Conclusion

This module introduced the process of importing and searching large-scale network traffic data using Splunk Enterprise. The lab demonstrated how a public intrusion detection dataset can be used to practice SIEM ingestion, event counting, and basic traffic-data investigation.

It also highlighted the importance of correct data-input configuration, file permissions, sourcetype selection, resource planning, and search validation.

These skills provide a foundation for further cloud-security monitoring, log analysis, and threat-hunting exercises. A more advanced cloud SOC workflow would extend this approach by collecting real cloud audit and identity logs, applying detection rules, and correlating events across multiple data sources.
