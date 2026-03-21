# SORTS — Smart Object Recognition Trash Sorting System

[![GitHub Repo](https://img.shields.io/badge/GitHub-Repo-blue?logo=github)](https://github.com/finnxiii/gemini-waste-sorter)
![Award](https://img.shields.io/badge/iForge%20Hack%20Day%202025-Most%20Adventurous%20Hack%20Winner-blue)

SORTS is an embedded AI prototype that automates waste classification using real-time image recognition and low-cost hardware.

Developed during an MLH hackathon, the system demonstrates a practical integration of computer vision with embedded systems to address real-world sustainability challenges.

> [!NOTE]
> This repository contains the full implementation of the SORTS prototype, including embedded hardware integration, AI-based waste classification, and system communication logic.

---

## Overview

SORTS captures images of waste items, classifies them using a vision-language model, and actuates a sorting mechanism to route items into appropriate categories:

- Organic  
- Plastic  
- Paper / Cardboard  
- Other  

The system is designed to operate with minimal infrastructure, using a local network for inter-device communication while relying on cloud AI only for inference.

---

## System Architecture

1. **Image Capture**  
   An ESP32-CAM captures an image of the waste item.

2. **Inference Pipeline**  
   The image is transmitted to a Python service, which queries the Google Gemini Vision API for classification.

3. **Decision Layer**  
   The classification output is mapped to a predefined waste category.

4. **Actuation**  
   An Arduino Uno R4 WiFi controls the sorting mechanism to direct the item accordingly.

5. **Networking**  
   All components communicate over a local Wi-Fi hotspot. Only the inference node requires internet access.

---

## Key Features

- Real-time waste classification using a multimodal AI model  
- Embedded system integration (ESP32-CAM + Arduino)  
- Local network communication for low-latency operation  
- Modular architecture enabling future hardware consolidation  
- Classification across multiple waste categories  

---

## Tech Stack

### Hardware
- Arduino Uno R4 WiFi  
- ESP32-CAM  

### Software
- Python (inference and orchestration)  
- Google Gemini 2.0 Flash (vision model)  

### Infrastructure and Tools
- Local Wi-Fi hotspot (device communication)  
- Arduino IDE  
- Visual Studio Code  

---

## Design Considerations

- **Latency vs Accuracy:** Cloud-based inference provides higher accuracy but introduces network dependency.  
- **Hardware Constraints:** Separating sensing (ESP32-CAM) and actuation (Arduino) simplified development within hackathon constraints.  
- **Scalability:** The architecture can be extended to support edge inference or a fully integrated microcontroller-based solution.

Future improvement: Consolidate image capture and actuation into a single ESP32-based system to reduce hardware complexity and cost.

---

## Team

- Naing Htoo Lwin  
- Phone Linn Khant  
- Nadav T Chong  
- Mohammad Ridwaan Joomun  

---

## Motivation

Global waste mismanagement remains a significant environmental challenge. SORTS explores how accessible embedded AI systems can improve sorting efficiency in environments such as schools, public spaces, and smart city infrastructure.

---

## Demo

<p align="center">
  <img src="./images/demo-setup.jpg" alt="SORTS Setup" width="500"/>
</p>

---

> [!NOTE]
> This project was developed within a limited hackathon timeframe. The current implementation prioritises proof-of-concept over production robustness.
