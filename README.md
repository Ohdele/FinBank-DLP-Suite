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
