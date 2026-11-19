# INTELLIDETECT

**Low-Cost Handheld Device/System for Real-Time Screening of Narcotics & Explosives across Indian Railways**

![Platform](https://img.shields.io/badge/Platform-ESP32-blue)
![Category](https://img.shields.io/badge/Category-IoT%20%7C%20Embedded%20Systems-green)
![Status](https://img.shields.io/badge/Status-Proof%20of%20Concept-orange)

**INTELLIDETECT** is a low-cost, ESP32-based handheld multi-sensor screening prototype that detects abnormal chemical-vapour and air-quality conditions and delivers real-time local alerts for railway security personnel.

---

## Problem Statement

Developing a mobile (quadruped) or handheld device/system capable of real-time screening for narcotics and explosives across Indian Railways.

## Objective

To build a portable, inexpensive proof-of-concept demonstrating multi-sensor chemical-vapour screening, on-device real-time processing, and immediate multi-modal alerts for suspicious air-quality conditions in railway environments—without the high cost and complexity of a quadruped robotic platform.

---

## System Architecture & Working Flow

The system follows a streamlined five-stage field workflow: **`Sense → Process → Decide → Alert → Log/Notify`**.

```mermaid
flowchart TD
    subgraph IN["1. INPUTS"]
        A1["SGP40 / BME680<br/>(VOC / Air-Quality Sensing)"]
        A2["MQ-2 / MQ-3 / MQ-135<br/>(Gas & Environmental Anomaly Sensing)"]
        A3["Optional Camera<br/>(Visual Inspection)"]
        A4["User Scan Button<br/>(Triggers Measurement Cycle)"]
    end

    subgraph PROC["2. PROCESSING UNIT — ESP32"]
        B1["Reads, Filters & Normalizes Sensor Values"]
        B2["Combines Multi-Sensor Readings"]
        B3["Threshold / AI-Assisted Decision Algorithm"]
        B1 --> B2 --> B3
    end

    subgraph OUT["3. OUTPUTS"]
        C1["OLED Display<br/>(Live Readings & NORMAL / SUSPICIOUS Status)"]
        C2["LED + Buzzer + Vibration Motor<br/>(Immediate Local Alert)"]
        C3["Optional Wireless Notification<br/>(Event Alert / Logging)"]
    end

    IN --> PROC --> OUT
```

### Step-by-Step Operation
1. **Air / Sample Intake:** The target area, luggage, or parcel is brought into the scanning zone and the user triggers a manual scan.
2. **Sensing:** VOC, gas, and environmental sensors collect raw readings.
3. **Signal Processing:** The ESP32 reads, filters, and normalizes the incoming sensor data.
4. **Detection Algorithm:** Threshold
