---
title: "Panorama Checks"
description: "Tool to check the Wildfire, Apps & Threats and Anti-virus versions of Panorama Firewall nodes "
pubDate: "Nov 20 2024"
heroImage: "/panorama-checks.jpg"
---

# Panorama Checks Tool

A simple **Tkinter-based GUI tool** for checking update statuses on **Palo Alto Panorama Firewalls**.  
This utility helps network administrators quickly identify devices with outdated security content (Apps & Threats, Antivirus, and Wildfire signatures) based on CSV exports.

---

## 🚀 Features

- **GUI Interface**: Built with Tkinter for ease of use  
- **CSV Import**: Load firewall status exports directly from Panorama  
- **Ignore List**: Specify nodes to ignore via an `ignore.csv` file  
- **Automatic Latest Version Detection**: Extracts the latest AAT, AV, and WF versions from the dataset  
- **Custom Checks**: Allows manual entry of version numbers to validate against  
- **Detailed Output**: Displays which nodes are out of date and in which category  

---

## 📂 Project Structure

```
panorama-checks-tool/
│
├── ignore.csv         # List of node names to ignore
├── panorama_tool.py   # Main Python script (GUI + logic)
└── README.md          # Project documentation
```

---

## ⚙️ Requirements

- Python **3.8+**
- Tkinter (bundled with most Python installations)

No additional dependencies are required.

---

## ▶️ Usage

1. Clone or download this repository.  
2. Ensure you have an `ignore.csv` file with a single row listing node names to ignore. Example:

   ```csv
   node1,node2,node3
   ```

3. Run the script:

   ```bash
   python panorama_tool.py
   ```

4. Inside the GUI:
   - Click **Open a file** to select a Panorama CSV export.  
   - The tool will auto-detect the latest **AAT, AV, and WF** versions and populate them.  
   - Optionally adjust the version fields manually. If empty the tool will check against highest present version
   - Click **Run tool** to check update compliance.  
   - Results will be displayed in the text box.  

---

## 🧑‍💻 How It Works

- The tool sanitizes the Panorama CSV to only include:
  - **Device Name**
  - **Apps & Threats Version (AAT)**
  - **Antivirus Version (AV)**
  - **Wildfire Version (WF)**

- It determines the **latest versions** across all devices.
- Each device is compared against the latest versions:
  - AAT mismatch → flagged
  - AV mismatch → flagged
  - WF version older than latest minus 10 → flagged
- Devices in `ignore.csv` are skipped.
- A detailed status message is printed for each device.

---

## 📋 Example Output

```
fw-branch1 Apps & Threats out of date (AAT: 8692-7232)
fw-hq1 Antivirus out of date (AV: 3456-2345)
fw-lab Wildfire out of date (WF: 123456-654321)
```

---

## 🔒 Notes

- This tool is intended for internal administrative use.  
- Ensure your Panorama CSV export contains **version columns** for AAT, AV, and WF before running.  
- Customize `ignore.csv` to exclude test or non-critical nodes.  

---

## 📜 License

MIT License – feel free to modify and adapt to your environment.
