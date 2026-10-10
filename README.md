# Sentinel: Cowrie Honeypot & PLG Observability Stack

A production-ready SSH/Telnet honeypot architecture designed to trap automated attacks, collect threat intelligence, and visualize malicious activity in real-time.

This project goes beyond a simple honeypot by integrating a modern, decoupled observability stack (PLG) to parse, aggregate, and display attacker behaviors, brute-force attempts, and executed payloads.

## 🏗️ Architecture & Stack

The environment is entirely containerized using Docker Compose and segmented into four core microservices:

* **[Cowrie] The Trap:** A medium-to-high interaction SSH and Telnet honeypot designed to log brute-force attacks and shell interactions.
* **[Promtail] The Agent:** A log collector configured to tail Cowrie's JSON logs in real-time, extract relevant labels, and ship them to the database.
* **[Loki] The Engine:** A horizontally scalable, highly available log aggregation system that indexes the data streams sent by Promtail.
* **[Grafana] The Dashboard:** The visualization layer, connected to Loki, displaying tactical metrics (top attacker IPs, most used credentials, geographic origins).

## 🚀 Key Features

* **Real-time Threat Monitoring:** Logs are instantly processed and visualized without manual parsing.
* **Decoupled Architecture:** The logging layer (Loki/Promtail) is separated from the application layer (Cowrie), ensuring high performance and fault tolerance.
* **Infrastructure as Code (IaC):** The Grafana dashboard structure is exported as a portable `dashboard.json` file, allowing instant redeployment without pushing sensitive local databases.

## 🛠️ Deployment

*Requirement: Docker and Docker Compose must be installed. Port 22 must be free and available on the host machine.*

**1. Clone the repository**
```bash
git clone [https://github.com/snisharahamad/sentinel-honeypot.git](https://github.com/snisharahamad/sentinel-honeypot.git)
cd sentinel-honeypot
```

**2. Launch the Sentinel Stack**
```bash
docker compose up -d
```

**3. Access the Dashboards**
Navigate to `http://<YOUR_SERVER_IP>:3000` to access Grafana and import the provided `dashboard.json` file to explore the threat intelligence data.
