# Week 3: Security Monitoring, Anomaly Detection & Simulation

## Overview
This folder contains the complete deliverables and artifacts for **Week 3: Security Monitoring, Anomaly Detection & Threat Simulation** for continuous surveillance of e-governance infrastructure.

## Contents of this Folder
1. `YuvaIntern_Week3_Security_Monitoring_and_Anomaly_Detection.docx` - The official Word document report for portal submission.
2. `DETECTION_RULES_AND_SIMULATION.md` - Technical specification covering log collection, Sigma detection rules, and threat simulation walkthroughs.

## Key Points & Tasks Developed for Week 3
* **1. Continuous Monitoring Architecture:** Ingestion pipelines for Web logs, Keycloak auth trails, PostgreSQL audit logs, and network flows.
* **2. Log Compliance & Retention:** Enforcing NTP time synchronization and 180-day secure log retention.
* **3. Anomaly Detection Methodologies:** Statistical baseline modeling (3-sigma deviations), heuristic rules, and User & Entity Behavior Analytics (UEBA).
* **4. Threat Simulations:** Modeled and tested distributed credential stuffing attacks and SQL injection attacks with automated defensive triggers.

## Safe Reference Repository
* **GitHub URL:** `https://github.com/SigmaHQ/sigma`
* *Why it fits:* Static YAML detection rule syntax. Zero attack code, zero execution, 100% safe.
