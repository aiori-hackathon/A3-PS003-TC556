# CityPulse-Audit — Federated Traffic-Flow Prediction with Communication-Cost Evaluation

**Problem Statement:** PS-003 — Federated Traffic-Flow Prediction with Communication-Cost Evaluation[cite: 3]  
**Team Name:** Solve X[cite: 3]  
**Hackathon:** AIORI-3 Hackathon[cite: 2, 3]  

---

## Team Introduction Video

YouTube: https://www.youtube.com/watch?v=YOUR_VIDEO_ID [cite: 2]

---

## Overview

City traffic sensors generate vast streams of real-time data[cite: 4]. Transmitting raw sensor streams to a central cloud server introduces severe privacy concerns and places a heavy burden on cellular network bandwidth[cite: 4, 5].

**CityPulse-Audit** solves this by implementing an event-triggered federated learning framework[cite: 3, 7, 8]. Traffic data stays private at local edge nodes (junctions)[cite: 5, 9, 10], and updates are communicated to the cloud coordinator only when necessary and within a strict byte budget[cite: 5, 7, 9].

---

## Key Features

- **Local Hybrid Prediction:** Combines a simple baseline, a shared lightweight GRU model, and a local private tweak at each junction to forecast traffic 15, 30, and 60 minutes ahead[cite: 7].
- **Event-Triggered Auditioning:** Edge nodes test model updates locally and trigger communication only when surprise traffic shifts occur[cite: 7, 8, 9].
- **Gain-per-Byte Budgeting:** The cloud coordinator ranks incoming update offers by gain-per-byte and admits updates within budget limits[cite: 7, 8, 9].
- **Byte Ledger & Dashboard:** Logs every message sent across the network to strictly evaluate bandwidth efficiency alongside prediction accuracy (MAE, RMSE, MAPE)[cite: 7, 8, 10].

---

## System Architecture

1. **Edge Node (Junction):**
   - Ingests road sensor data (counts, speed) locally[cite: 9, 10].
   - Evaluates local error; if error rises, generates compressed update options[cite: 9].
   - Sends a lightweight offer to the cloud coordinator if local improvement justifies bandwidth cost[cite: 7, 9].

2. **Cloud Coordinator:**
   - Receives offers from junctions, ranks them by gain-per-byte, and admits updates within the byte budget[cite: 7, 9].
   - Merges admitted updates into a new global model version and broadcasts it back to edge nodes[cite: 9, 10].
   - Records all bandwidth events in the byte ledger for real-time monitoring[cite: 7, 9, 10].

---

## Standards & Technologies

- **Communication Protocol:** MQTT 5.0 over TLS 1.3[cite: 6]
- **Data Serialization:** Concise Binary Object Representation (CBOR - RFC 8949)[cite: 6]
- **Core ML Model:** Tiny GRU + Sparse Updates[cite: 6, 7]
- **Metrics:** MAE, RMSE, MAPE, and Byte Expenditure[cite: 7, 8]

---

## Team Members

- **Team Lead / Member:** [Name]
- **Frontend Developer:** [Your Name] — Built live dashboard UI, byte ledger visualization, and performance charts[cite: 2, 7, 10]
- **Backend / ML Developer:** [Member Name] — Implemented federated learning pipeline and server aggregation logic[cite: 1, 9]

---

## License

This project is licensed under the MIT License.
