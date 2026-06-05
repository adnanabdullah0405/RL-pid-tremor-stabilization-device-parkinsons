# 🤚 RL-Based Tremor Stabilization Device for Parkinson's Patients

> **Intelligent IoT wearable** combining a neural network tremor 
> classifier with a Reinforcement Learning-optimized PID controller 
> — automatically detecting tremors and stabilizing hand movement 
> through adaptive motor control personalized to each patient.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![ESP32](https://img.shields.io/badge/ESP32-Microcontroller-blue?style=flat-square)
![RL](https://img.shields.io/badge/Reinforcement_Learning-PID_Control-green?style=flat-square)

---

## 📊 Results

| Metric | Value |
|--------|-------|
| Tremor classification accuracy | 92% |
| Reduction in tremor intensity | 60% |
| Sensor | MPU6050 — 6-axis IMU |
| Microcontroller | ESP32 |
| Patient adaptation | Personalized PID locking per patient |
| Power efficiency | Motor activates ONLY when tremor detected |

---

## 🏗️ System Architecture

```mermaid
graph TD
    A[🤚 Patient's Hand] --> B[MPU6050 Sensor]
    B --> |6-axis accelerometer + gyroscope data| C[ESP32 Microcontroller]
    
    C --> D[Neural Network Classifier]
    
    D -->|Normal Movement| E[⛔ Motor OFF — Battery Supply Cut]
    D -->|Tremor Detected ✅| F[ESP32 Signals Battery Supply]
    
    F --> G[Motor Activates]
    G --> H[Calculate Input Torque from MPU Signal]
    H --> I[Compare with Motor Counter-Torque]
    
    I --> J{Torque Difference}
    J -->|Large Difference| K[RL Agent — Increase Kp Rapidly]
    K --> L[Ki and Kd Auto-Adjust]
    L --> M[Motor Speed Increases]
    M --> N{Difference Below Threshold?}
    N -->|No| I
    N -->|Yes — Hand Stabilized ✅| O[Lock PID Values for Patient]
    O --> P[Maintain Stabilization for Full Cycle]
    P --> B
```

---

## 🧠 Two-Stage AI System

### Stage 1 — Neural Network Tremor Classifier

```mermaid
graph LR
    A[MPU6050 Raw Data] --> B[6-Axis Feature Extraction]
    B --> C[Neural Network]
    C --> D{Classification}
    D -->|Normal Movement| E[Motor OFF]
    D -->|Tremor Detected| F[Activate RL-PID Controller]
```

The neural network is trained to distinguish between:
- **Normal movement** — intentional daily activities (eating, writing, reaching)
- **Tremor movement** — involuntary oscillatory hand tremors

**Achieved 92% classification accuracy** on real patient tremor data.

---

### Stage 2 — RL-Optimized PID Controller

```mermaid
graph TD
    A[Tremor Detected] --> B[Calculate Input Torque from MPU]
    B --> C[Read Motor Counter-Torque]
    C --> D[Compute Torque Error]
    
    D --> E[RL Agent]
    E --> F[Adjust Kp — Proportional Gain]
    E --> G[Adjust Ki — Integral Gain]  
    E --> H[Adjust Kd — Derivative Gain]
    
    F --> I[PID Controller]
    G --> I
    H --> I
    
    I --> J[Motor Speed Signal]
    J --> K[Motor Counter-Torque Output]
    K --> L{Error Below Threshold?}
    
    L -->|No — Continue adjusting| D
    L -->|Yes — Hand Stabilized| M[🔒 Lock PID Values for Patient]
    M --> N[Personalized Profile Saved]
```

**How the RL agent works:**
- When large torque difference detected → **Kp increases rapidly** for strong correction
- As difference shrinks → **Ki and Kd self-adjust** for smooth stabilization
- Once hand stabilized below threshold → **PID values locked** for that patient
- Locked values become the patient's **personalized stabilization profile**
- Each patient gets their own optimal PID parameters

---

## ⚡ Key Features

- **Power efficient** — motor only activates when tremor is detected, 
  not continuously running
- **Patient-specific adaptation** — RL agent finds optimal PID values 
  per patient and locks them for the entire session
- **Real-time processing** — ESP32 runs inference and control loop 
  simultaneously
- **Dual AI system** — neural network for detection + RL for adaptive 
  control
- **Non-intrusive** — wearable form factor, lightweight, battery-powered

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Microcontroller | ESP32 |
| Motion Sensor | MPU6050 — 6-axis IMU |
| Tremor Classifier | Neural Network (PyTorch) |
| Control System | RL-optimized PID Controller |
| ML Framework | PyTorch, scikit-learn |
| Embedded Code | C++ (Arduino framework) |
| Data Processing | Python, NumPy |
| Actuator | DC Motor with PWM control |

---

## 📸 Results & Demo

> Demo and results coming soon

---

## 🎓 Project Context

Built as **Final Year Project at NUST** 
(National University of Sciences & Technology) — 
one of Pakistan's top engineering universities.

Specialized in: Machine Learning · Deep Learning · 
Reinforcement Learning · Embedded Systems

---

> ⚠️ **Note:** Hardware implementation and trained model weights 
> are part of the physical prototype. Code available on request.

---

## 📫 Contact

**Adnan Abdullah** — Agentic AI Engineer & AI Team Lead

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/adnan-abdullah-700899b)
[![Email](https://img.shields.io/badge/Gmail-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:muhammad.adnannust@gmail.com)

---

*Built at NUST · 92% tremor classification accuracy · 
60% reduction in tremor intensity · 
Personalized RL-PID adaptation per patient*
