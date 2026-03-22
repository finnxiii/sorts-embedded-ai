# SORTS — Smart Object Recognition Trash Sorting System

[![GitHub Repo](https://img.shields.io/badge/GitHub-Repo-2E2E2E?logo=github&logoColor=white)](https://github.com/finnxiii/sorts-embedded-ai)
![Award](https://img.shields.io/badge/iForge%20Hack%20Day%202025-Most%20Adventurous%20Hack%20Winner-brightgreen)

SORTS is an embedded AI prototype that automates waste classification using real-time image recognition and low-cost hardware.

Developed during an MLH hackathon, the system demonstrates a practical integration of computer vision with embedded systems to address real-world sustainability challenges.

<br>

> [!NOTE]
> This project was developed within a limited hackathon timeframe. The current implementation prioritises proof-of-concept over production robustness.

<br>

## Overview

SORTS captures images of waste items, classifies them using a vision-language model, and actuates a sorting mechanism to route items into appropriate categories:

- Organic  
- Plastic  
- Paper / Cardboard  
- Other  

The system is designed to operate with minimal infrastructure, using a local network for inter-device communication while relying on cloud AI only for inference.

<br>

## System Architecture

```mermaid
flowchart LR

A[ESP32-CAM] -->|Capture Image| B[Python Inference Service]
B -->|API Request| C[Gemini Vision API]
C -->|Classification Result| B
B -->|Mapped Category| D[Decision Layer]
D -->|Control Signal| E[Arduino Uno R4]
E --> F[Sorting Mechanism]

subgraph Local Network
A
B
E
end

subgraph Cloud
C
end
```

**Flow Summary**
- The ESP32-CAM captures images and sends them to a Python inference service.  
- The system uses the Gemini Vision API to classify waste items.  
- Classification results are mapped to predefined categories.  
- The Arduino controller executes physical sorting based on the output.

<br>

## Key Features

- Real-time waste classification using a multimodal AI model  
- Embedded system integration (ESP32-CAM + Arduino)  
- Local network communication for low-latency operation  
- Modular architecture enabling future hardware consolidation  
- Classification across multiple waste categories  

<br>

## Tech Stack

### Hardware
![Arduino](https://img.shields.io/badge/Arduino-00979D?style=for-the-badge&logo=arduino&logoColor=white)
![ESP32](https://img.shields.io/badge/ESP32--CAM-333333?style=for-the-badge)

### Software
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)
[![Gemini](https://img.shields.io/badge/Google%20Gemini%20API-4285F4?style=for-the-badge&logo=google&logoColor=white)](https://ai.google.dev/)

### Infrastructure & Tools
![Wi-Fi](https://img.shields.io/badge/Local%20Wi--Fi-000000?style=for-the-badge&logo=wifi&logoColor=white)
![Arduino IDE](https://img.shields.io/badge/Arduino%20IDE-00979D?style=for-the-badge&logo=arduino&logoColor=white)
![VS Code](https://img.shields.io/badge/VS%20Code-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white)

<br>

## Design Considerations

- **Latency vs Accuracy:** Cloud-based inference provides higher accuracy but introduces network dependency.  
- **Hardware Constraints:** Separating sensing (ESP32-CAM) and actuation (Arduino) simplified development within hackathon constraints.  
- **Scalability:** The architecture can be extended to support edge inference or a fully integrated microcontroller-based solution.

Future improvement: Consolidate image capture and actuation into a single ESP32-based system to reduce hardware complexity and cost.

<br>

## Team

- Naing Htoo Lwin  
- Phone Linn Khant  
- Nadav T Chong  
- Mohammad Ridwaan Joomun  

<br>

## Motivation

Global waste mismanagement remains a significant environmental challenge. SORTS explores how accessible embedded AI systems can improve sorting efficiency in environments such as schools, public spaces, and smart city infrastructure.

<br>

## Demo

<p align="center">
  <img src="./images/demo-setup.jpg" alt="SORTS Setup" width="500"/>
</p>

