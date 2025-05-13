# 🛡️ SDN-Based Real-Time DDoS Detection and Mitigation System

This project uses Software-Defined Networking (SDN) and machine learning to detect and mitigate DDoS attacks in real-time. Built with **Mininet** and a **RYU controller**, it leverages flow statistics to classify traffic and take immediate mitigation action.

---

## 📊 Dataset Details

- **Label**: Indicates whether the packet is part of a DDoS attack (`1`) or normal traffic (`0`).

<p align="center">
  <img width="700" src="https://i.imgur.com/cq0etXH.png" alt="Dataset details">
</p>
<p align="center"><em>Figure 6: Dataset details</em></p>

---

## 🧠 Model Performance & System Resources

| Algorithm | Precision (%) | Recall (%) | F1-Score (%) | Model Training Time (s) | CPU Usage (%) | RAM Usage (%)  |
|:---------:|:-------------:|:----------:|:------------:|:-----------------------:|:-------------:|:--------------:|
| KNN       | 97.65         | 98.04      | 97.84        | 78                      | 51            | 80             |
| **DT**    | **99.82**     | **99.89**  | **99.87**    | **19**                  | **50**        | **70**         |
| RF        | 99.92         | 99.64      | 99.78        | 40                      | 50            | 70             |
| SVM       | 87.30         | 88.23      | 87.77        | 3600                    | 70            | 90             |

<p align="center"><em>Table 4: The detailed system configuration</em></p>

---

## 🧪 Confusion Matrix

<p align="center">
  <img width="800" src="https://i.imgur.com/BRH9u2V.png" alt="Confusion matrix of the algorithm">
</p>
<p align="center"><em>Figure 7: Confusion matrix of the algorithm</em></p>

---

## 🧬 Scenario Results

### ✅ Scenario 2 Result

<p align="center">
  <img width="500" src="https://i.imgur.com/vFsnafg.png" alt="Scenario 2 Result">
</p>
<p align="center"><em>Figure 10: Scenario 2 Result</em></p>

---

### ✅ Scenario 3 Result

<p align="center">
  <img width="500" src="https://i.imgur.com/8WAcm1w.png" alt="Scenario 3 Result">
</p>
<p align="center"><em>Figure 11: Scenario 3 Result</em></p>

---

### ⚠️ Scenario 4

> In this scenario, an attack was launched directly at the Controller from server `h6`.

<p align="center">
  <img width="400" src="https://i.imgur.com/n8W11Ki.png" alt="Scenario 4">
</p>
<p align="center"><em>Figure 12: Scenario 4</em></p>

---

### 🛡️ Scenario 4 Result

> The system **detected and mitigated** the controller-targeted attack autonomously. The controller remained **stable and fully operational** throughout the attack.

<p align="center">
  <img width="500" src="https://i.imgur.com/emh5I23.png" alt="Scenario 4 Result">
</p>
<p align="center"><em>Figure 13: Scenario 4 Result</em></p>

---

## 📁 Directory Structure

project/
├── controller/
│ └── uitSDNDDoSD.py
├── mininet/
│ └── custom_topology.py
├── utils/
│ ├── train_model.py
│ ├── test_model.py
│ └── model.pkl
├── data/
│ └── CICDDoS2019/
└── README.md


---

## 🔍 Summary

- Real-time DDoS detection and mitigation using ML
- Flow statistics from OpenFlow switches analyzed every second
- Multiple ML models tested, with DT and RF performing best
- Full mitigation logic including flow removal and port control
- Scenarios include internal and external DDoS threats

---

## 💬 Contact

Have questions? Create an [Issue](https://github.com/0Deen/ddos-attack-detection-mitigation-system/issues) or reach out via email.
