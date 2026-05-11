# 🔐 Automated IP Reputation & Gmail Alert System using n8n

A Security Operations Center (SOC)-style automation workflow built in n8n that analyzes IP reputation data and automatically sends professional Gmail alerts based on the security assessment result.

---

# 🚀 Features

- Automated workflow execution
- IP reputation analysis
- Conditional threat detection using IF logic
- Automated Gmail alert notifications
- SOC-style incident reporting
- Beginner-friendly but expandable to enterprise workflows

---

# 🧠 Workflow Architecture

```text
Manual Trigger
      ↓
Edit Fields (Input IP)
      ↓
HTTP Request (Threat Intelligence API)
      ↓
IF Node (Safe / Malicious Check)
      ↓
 ┌───────────────┴───────────────┐
 ↓                               ↓
Safe Email                 Threat Alert Email
```
# 📸 Workflow Preview
<img width="1365" height="679" alt="workflow_n8n" src="https://github.com/user-attachments/assets/f8321a82-ca0c-451b-947d-4f922bc5bc64" />

# ⚙️ Technologies Used
```
n8n
Gmail OAuth2 API
HTTP Request API Integration
JSON Processing
Conditional Logic
Security Automation Concepts
```
# 📌 Project Objective
```
This project demonstrates how SOC analysts and cybersecurity engineers can automate threat intelligence analysis and email alerting using low-code automation.
The workflow:

1.Accepts an IP address
2.Sends it to a threat intelligence API
3.Evaluates the response
4.Sends different email alerts depending on whether the IP is safe or suspicious
```
🛠️ Setup Guide
1️⃣ Install n8n

Official Website:

https://n8n.io/

Run locally:

npm install n8n -g
n8n

Access:

http://localhost:5678
🔑 Gmail OAuth2 Setup
Enable Gmail API

Open Google Cloud Console:

https://console.cloud.google.com/

Steps
Create a new project
Enable Gmail API
Configure OAuth Consent Screen
Create OAuth Client ID
Add Redirect URI:
http://localhost:5678/rest/oauth2-credential/callback
Copy:
Client ID
Client Secret
Paste them into Gmail OAuth2 credentials in n8n
🌐 Threat Intelligence API

Example API:

https://jsonplaceholder.typicode.com/users

You can later replace it with:

AbuseIPDB
VirusTotal
AlienVault OTX
GreyNoise
🧩 Workflow Nodes
1️⃣ Manual Trigger

Starts the workflow manually.

2️⃣ Edit Fields

Used to define the IP address input.

Example:

{
  "ip": "8.8.8.8"
}
3️⃣ HTTP Request

Sends request to threat intelligence API.

Method:

GET
4️⃣ IF Node

Checks whether the IP is malicious or safe.

Example Logic:

{{$json["malicious"]}} == true
5️⃣ Gmail Nodes

Two different email paths:

✅ Safe IP Email

Sends a professional safe-status notification.

🚨 Threat Alert Email

Sends a high-priority security alert.

📧 Example Safe Email
Subject:
SOC Security Analysis Result
Body:
The IP address has been thoroughly analyzed as part of the security validation process. Based on the available threat intelligence and activity review, no malicious behavior, anomalies, or indicators of compromise were detected.

At this time, the IP is classified as safe and does not appear to be associated with any known threats, suspicious activity, or security risks.
🚨 Example Threat Alert
Subject:
SOC Threat Detection Alert
Body:
Potentially malicious activity has been detected during automated IP reputation analysis. Indicators suggest the IP may be associated with suspicious or harmful behavior.

Immediate investigation is recommended.
🧪 How to Run
Click:
Execute Workflow
Observe workflow path:
TRUE → Threat alert
FALSE → Safe notification
Check email inbox for automated alert.
📚 Skills Demonstrated
Security Automation
SOC Workflow Design
Threat Intelligence Integration
OAuth2 Authentication
API Handling
Conditional Logic
Email Automation
Incident Notification Systems
🔥 Future Improvements
Slack/Discord alerts
Splunk integration
VirusTotal API support
Real-time monitoring
GeoIP enrichment
SIEM integration
Dashboard visualization
