# 🔍 Exploring SPL with Splunk

## 📌 Overview

This repository documents my hands-on learning and practice with **Splunk Search Processing Language (SPL)**.

The project focuses on exploring Windows event logs and learning how to search, filter, transform, analyze, and visualize data using SPL. These fundamental skills are important for Security Operations Center (SOC) analysts and cybersecurity professionals who work with Security Information and Event Management (SIEM) platforms.

---

## 🎯 Objectives

The main objectives of this lab were to:

- Search and explore Windows event logs
- Understand Splunk indexes
- Explore available hosts using Data Summary
- Filter events using Event IDs
- Use Boolean operators
- Perform wildcard searches
- Select specific fields from events
- Remove duplicate results
- Rename fields
- Sort and reverse search results
- Limit results using `head` and `tail`
- Perform statistical analysis using `stats`
- Create visualizations using `chart`

---

## 🛠️ Tools and Technologies

- **Splunk**
- **Search Processing Language (SPL)**
- **Windows Event Logs**
- **TryHackMe**

---

# 📂 Project Structure

```text
splunk-spl-fundamentals/
│
├── README.md
│
└── screenshots/
    ├── 01_initial-search-windowslogs.png
    ├── 02_data-summary-host.png
    ├── 03_operator-eventid-filter.png
    ├── 04_operator-boolean-and.png
    ├── 05_operator-wildcard-cyber.png
    ├── 06_table-reverse.png
    ├── 07_dedup-hostname.png
    ├── 08_fields-command.png
    ├── 09_rename-command.png
    ├── 10_sort-command.png
    ├── 11_head-tail-command.png
    ├── 12_stats-count-by-host.png
    ├── 13_chart-eventid-by-image.png
    └── 14_room-completed.png
```

---

# 🔎 Lab Activities

## 1️⃣ Initial Search

### SPL Query

```spl
index=windowslogs
```

This query searches and displays all available events stored in the `windowslogs` index.

### Screenshot

![Initial Search](screenshots/01_initial-search-windowslogs.png)

---

## 2️⃣ Exploring Hosts Using Data Summary

The Splunk **Data Summary** feature was used to explore the available hosts and data sources.

### Screenshot

![Data Summary Hosts](screenshots/02_data-summary-host.png)

---

## 3️⃣ Filtering Events Using EventID

### SPL Query

```spl
index=windowslogs EventID=1
```

This query filters the Windows logs and displays events with `EventID=1`.

### Screenshot

![EventID Filter](screenshots/03_operator-eventid-filter.png)

---

## 4️⃣ Using Boolean AND Operator

### SPL Query

```spl
index=windowslogs EventID=1 User=*James*
```

This query searches for events where both conditions are satisfied:

- `EventID=1`
- The username matches `James`

### Screenshot

![Boolean AND](screenshots/04_operator-boolean-and.png)

---

## 5️⃣ Wildcard Search

### SPL Query

```spl
index=windowslogs cyber*
```

The wildcard character `*` is used to search for terms that begin with `cyber`.

### Screenshot

![Wildcard Search](screenshots/05_operator-wildcard-cyber.png)

---

## 6️⃣ Using the Table and Reverse Commands

### SPL Query

```spl
index=windowslogs
| table _time EventID Hostname SourceName
| reverse
```

The `table` command selects specific fields from the search results.

The `reverse` command reverses the order of the results.

### Screenshot

![Table Reverse](screenshots/06_table-reverse.png)

---

## 7️⃣ Removing Duplicate Results

### SPL Query

```spl
index=windowslogs
| dedup Hostname
| table _time EventID Hostname SourceName
| reverse
```

The `dedup` command removes duplicate values based on the specified field.

In this case, duplicate `Hostname` values are removed.

### Screenshot

![Dedup Hostname](screenshots/07_dedup-hostname.png)

---

## 8️⃣ Using the Fields Command

### SPL Query

```spl
index=windowslogs
| fields EventID Hostname SourceName
```

The `fields` command keeps only the specified fields in the search results.

### Screenshot

![Fields Command](screenshots/08_fields-command.png)

---

## 9️⃣ Renaming a Field

### SPL Query

```spl
index=windowslogs
| table _time EventID Hostname SourceName
| rename Hostname as Host
```

The `rename` command changes the displayed field name.

In this example:

```text
Hostname → Host
```

### Screenshot

![Rename Command](screenshots/09_rename-command.png)

---

## 🔟 Sorting Search Results

### SPL Query

```spl
index=windowslogs
| table _time EventID Hostname SourceName
| sort - _time
```

The `sort` command organizes the results.

The minus sign (`-`) sorts the events in descending order, showing newer events first.

### Screenshot

![Sort Command](screenshots/10_sort-command.png)

---

## 1️⃣1️⃣ Using Head and Tail Commands

### Head

```spl
index=windowslogs
| head 10
```

The `head` command returns the first specified number of events.

### Tail

```spl
index=windowslogs
| tail 10
```

The `tail` command returns the last specified number of events.

### Screenshot

![Head and Tail](screenshots/11_head-tail-command.png)

---

## 1️⃣2️⃣ Counting Events by Host

### SPL Query

```spl
index=windowslogs
| stats count by host
```

The `stats` command performs statistical analysis.

This query counts the number of events associated with each host.

### Screenshot

![Stats Count by Host](screenshots/12_stats-count-by-host.png)

---

## 1️⃣3️⃣ Creating a Chart

### SPL Query

```spl
index=windowslogs
| chart count(EventID) by Image
```

The `chart` command aggregates data based on the specified field.

This query analyzes Event IDs based on the associated process image.

### Screenshot

![Chart EventID by Image](screenshots/13_chart-eventid-by-image.png)

---

# 🧠 SPL Commands Learned

| Command | Purpose |
|---|---|
| `index` | Searches data from a specific Splunk index |
| `table` | Displays selected fields |
| `fields` | Includes specified fields in the results |
| `dedup` | Removes duplicate values |
| `rename` | Renames a field |
| `sort` | Sorts search results |
| `reverse` | Reverses the result order |
| `head` | Returns the first specified number of results |
| `tail` | Returns the last specified number of results |
| `stats` | Performs statistical analysis |
| `chart` | Aggregates data for visualization |

---

# 🔐 SOC Analyst Relevance

Splunk and SPL are important for SOC analysts because security teams regularly need to:

- Search through large volumes of logs
- Investigate security events
- Filter suspicious activity
- Analyze user and process activity
- Identify patterns in security data
- Count and aggregate security events
- Investigate endpoint activity
- Create dashboards and visualizations

These skills provide a foundation for working with SIEM platforms and performing security monitoring and incident investigation.

---

# 🎓 Lab Completion

The Splunk lab was successfully completed.

**Completion Details:**

- Tasks Completed: **8**
- Points Earned: **152**

### Screenshot

![Room Completed](screenshots/14_room-completed.png)

---

# 📚 Key Takeaways

Through this hands-on lab, I gained practical experience with:

- Splunk fundamentals
- SPL query syntax
- Searching Windows event logs
- Event filtering
- Boolean operators
- Wildcard searches
- Field manipulation
- Removing duplicate events
- Sorting search results
- Statistical analysis
- Data visualization

---

# 🚀 Future Improvements

I plan to continue developing my Splunk and SOC skills by exploring:

- Failed login detection
- Brute-force attack detection
- Suspicious PowerShell activity
- Process execution analysis
- Detection engineering
- Splunk dashboards
- Correlation searches
- MITRE ATT&CK mapping
- Incident investigation workflows

---

## 👤 Author

**Pranav Bharat Chakote**

Aspiring SOC Analyst | Cybersecurity Enthusiast

---

## ⭐ Learning Goal

This repository represents my hands-on journey of learning **Splunk Search Processing Language (SPL)** and building foundational skills for a career in **Security Operations Center (SOC)** and cybersecurity.
