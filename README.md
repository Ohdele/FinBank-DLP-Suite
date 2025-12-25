# FinBank DLP Suite


## Lab Scope
- Target Data Types: PII, financial records, credentials
- Platforms: On-prem servers, Office 365, cloud storage
- Tools: Forcepoint DLP, Microsoft Purview

## Simulated Data Sources
- Local files containing sample PII and financial data
- Web application logs with sensitive fields
- Database dumps with test customer records

## DLP Policies
- Detect PII (names, SSNs, emails)
- Detect credit card numbers and financial records
- Monitor confidential file transfers (cloud and local)
- Enforce encryption for sensitive data in transit

## Test Data
- ~/dlp_test_data/pii_sample.txt — sample PII
- ~/dlp_test_data/financial_sample.txt — sample financial data


## Detection Simulation
Simulated sensitive data files were created in ~/dlp_test_data.

Detection was performed using:
grep -R -n -E "([0-9]{3}-[0-9]{2}-[0-9]{4}|Account:)" ~/dlp_test_data

This simulates DLP pattern matching and alert generation.
All detection output is captured in proof_log_dlp.txt.

## Incident Response Simulation
A simulated data exfiltration attempt was executed by copying a detected PII file from the monitored directory to a mock exfiltration path.

Action:
- Source: ~/dlp_test_data/pii_sample.txt
- Destination: ~/exfil_sim/

This represents an unauthorized data movement event that a DLP solution would flag as a policy violation.

Evidence:
- Command execution, timestamps, and file movement are logged in proof_log_dlp.txt.


## Encryption Verification

A TLS encryption test was performed on a local simulated service to verify secure data transmission.

Action:
- TLS server started using a self-signed certificate at ~/tls_test/cert.pem and key at ~/tls_test/key.pem
- Client connection tested using: openssl s_client -connect localhost:443 -tls1_2

Outcome:
- TLS handshake completed successfully with protocol TLSv1.2 and cipher ECDHE-RSA-AES256-GCM-SHA384
- Self-signed certificate verified, connection secure
- All commands and outputs captured in proof_log_dlp.txt


## Metrics Reporting
Detections count simulated PII and financial files flagged
Incidents count one exfiltration attempt logged
Encryption checks TLS handshake verified successfully
