# Security Monitoring Architecture & Detection Rules

## 1. Log Ingestion & Retention Architecture
* **Web & API Ingress:** NGINX / Kong access logs formatted as structured JSON.
* **Authentication:** Keycloak OAuth2 / OpenID Connect login success and failure events.
* **Database Auditing:** PostgreSQL `pgAudit` tracking all administrative and DDL/DML queries on citizen tables.
* **Retention Standard:** 180-day retention with WORM (Write Once, Read Many) cloud bucket storage.

## 2. Sample Detection Rule (Sigma Format)

```yaml
title: High-Rate Authentication Failure Spike (Credential Stuffing)
status: production
description: Detects more than 50 failed login attempts from rotating source IPs within a 60-second window.
logsource:
    category: application
    product: keycloak_auth
detection:
    selection:
        event_type: 'LOGIN_ERROR'
        error: 'invalid_user_credentials'
    timeframe: 1m
    condition: selection | count() > 50
level: high
tags:
    - attack.credential_access
    - attack.t1110.004
```

## 3. Threat Simulation Scenarios & Response
1. **Simulation 1: Distributed Credential Stuffing**
   * *Trigger:* 50,000 requests over 5 minutes across distributed proxy IPs.
   * *Response:* Threshold tripped at minute 2; automated edge WAF rule enforced CAPTCHA and IP ban.
2. **Simulation 2: Time-Based Blind SQLi**
   * *Trigger:* Injected queries containing `SLEEP(5)` commands targeting citizen records.
   * *Response:* Database latency monitor flagged high response delays; active session quarantined immediately.
