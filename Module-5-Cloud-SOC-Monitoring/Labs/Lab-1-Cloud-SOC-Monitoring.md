# Lab 1: Cloud SOC Monitoring (Simulated Dataset Analysis)

## 🎯 Objective

To simulate cloud security monitoring by ingesting and analyzing a public cloud intrusion detection dataset (CSE-CIC-IDS2018) into Splunk. This lab demonstrates the ability to handle large-scale cloud traffic logs and search for potential threats.

## 🛠️ Tools & Environment Used

- **Operating System:** Kali Linux VM
- **SIEM Platform:** Splunk Enterprise (v10.0.2)
- **Dataset:** CSE-CIC-IDS2018 (Cloud-based network traffic)
- **Data Format:** CSV (Comma-Separated Values)
- **Sourcetype:** `csv`

## 📝 Detailed Lab Steps & Execution

### Step 1: Downloading the Dataset

1. Downloaded a sample CSV file from the CSE-CIC-IDS2018 dataset.
2. Verified that the file contained network traffic flow data, including source IP addresses, destination IP addresses, protocols, and other relevant traffic attributes.
3. Prepared the CSV file for ingestion into Splunk Enterprise.

The CSE-CIC-IDS2018 dataset contains network traffic records intended for cybersecurity research and intrusion detection analysis.

### Step 2: Ingesting Data into Splunk

1. Logged into the Splunk Web Interface.
2. Navigated to **Settings → Data Inputs → Files & Directories**.
3. Selected the option to add a local file or directory.
4. Specified the downloaded CSV dataset as the data source.
5. Set the **Sourcetype** to `csv`.
6. Configured the appropriate index for storing the imported events.
7. Submitted the configuration and verified that the dataset was indexed successfully.

The ingestion process resulted in **34,180 matching events**, according to the observed lab results.

### Step 3: Searching and Analyzing Cloud Traffic

1. Opened the **Search & Reporting** app in Splunk.
2. Executed the following search query with the Time Range set to **All time**:

   ```spl
   index=* sourcetype=csv
   ```

3. Reviewed the indexed network traffic records.
4. Examined available traffic attributes to look for potential anomalies, such as:
   - Unusual network protocols
   - Unexpected source or destination IP addresses
   - High-volume traffic patterns
   - Unusual connection behavior
   - Traffic patterns that may warrant further investigation

The search demonstrated how Splunk can be used to retrieve and explore a large collection of imported network traffic events.

**Note:** Identifying a potential anomaly does not, by itself, confirm a security incident. Further investigation and correlation with additional evidence are required.

## 📸 Screenshots & Evidence

### Screenshot 1: Data Input Configuration

This screenshot shows the Splunk data input configuration used to ingest the cloud intrusion detection dataset.

**Image Preview:**

![Cloud Data Input Configuration](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-5-Cloud-SOC-Monitoring/Labs/lab13-cloud-data-input.png)

**Direct Image Link:**

https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-5-Cloud-SOC-Monitoring/Labs/lab13-cloud-data-input.png

### Screenshot 2: Cloud Traffic Search Results

This screenshot shows the ingested cloud traffic data being searched in Splunk, with **34,180 events** reported in the lab results.

**Image Preview:**

![Cloud Traffic Search Results](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-5-Cloud-SOC-Monitoring/Labs/lab13-cloud-data-search.png)

**Direct Image Link:**

https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-5-Cloud-SOC-Monitoring/Labs/lab13-cloud-data-search.png

## 🔍 Search Query Summary

**Search for CSV events across available indexes:**

```spl
index=* sourcetype=csv
```

This query searches across indexes accessible to the user for events tagged with the `csv` sourcetype. The actual results depend on the indexes, permissions, time range, and data available in Splunk.

## ✅ Conclusion

Successfully ingested and explored a cloud-based intrusion detection dataset using Splunk Enterprise. This lab demonstrated the process of preparing a CSV dataset, configuring data inputs, verifying indexed events, and searching network traffic records using Search Processing Language (SPL).

The reported 34,180 matching events provided a dataset for exploring network traffic attributes and investigating potentially suspicious patterns. These skills establish a foundation for cloud SOC monitoring, network threat hunting, and further investigation of possible DDoS activity or unauthorized access.

However, the ingestion and search results alone do not establish that an actual attack was detected. Specific traffic patterns must be investigated before classifying them as malicious.

## 🎓 Key Skills Demonstrated

- Cloud SOC monitoring fundamentals
- CSE-CIC-IDS2018 dataset handling
- CSV data ingestion into Splunk
- Splunk data input configuration
- Event indexing and verification
- Search Processing Language (SPL)
- Network traffic exploration
- Anomaly detection fundamentals
- Threat hunting and security event investigation
