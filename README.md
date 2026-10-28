# AWS Account Security Baseline & CloudTrail Audit Logging

## Project Overview

This project implements and validates foundational AWS account security controls, with an emphasis on identity security, centralized audit logging, log integrity, and secure storage.

The objective is to establish a baseline for recording AWS management activity and protecting the resulting audit evidence.

## Objectives

- Secure root account access with multi-factor authentication (MFA).
- Use AWS IAM Identity Center for administrative CLI access.
- Configure a multi-Region AWS CloudTrail trail.
- Deliver audit logs to Amazon S3.
- Validate log-file integrity protection.
- Verify S3 public access safeguards and bucket policy status.
- Document the implemented controls, validation results, and remaining security considerations.

## Architecture

**Services used**
- AWS IAM and root account security controls
- AWS IAM Identity Center
- AWS CLI
- AWS CloudTrail
- Amazon S3

**Data flow**

AWS management activity → CloudTrail → Amazon S3 audit log storage

## Security Controls and Validation

| Control | Observed result |
|---|---|
| Root account MFA | Enabled |
| Root account access keys | None present |
| IAM Identity Center | Configured for CLI access |
| CloudTrail trail | `cloud-security-lab-trail` |
| Multi-Region logging | Enabled |
| Management events | Read and write events enabled |
| Data events | Not enabled |
| CloudTrail log delivery | Verified |
| S3 default encryption | SSE-S3 (AES-256) |
| CloudTrail log-file validation | Enabled |
| S3 Block Public Access | All four bucket-level settings enabled |
| S3 bucket policy public status | `IsPublic = false` |

## Key Findings

The validation checks confirmed that the trail was delivering logs to S3, log-file validation was enabled, and the bucket had all four S3 Block Public Access settings enabled. AWS did not classify the bucket policy as public.

These controls provide a useful foundation for AWS audit logging and evidence protection.

## Limitations and Future Improvements

- Enable and evaluate additional event logging where justified, including S3 data events for selected sensitive resources.
- Review IAM permissions and adopt least-privilege access rather than relying on broad administrative permissions.
- Evaluate log retention, deletion protection, and tamper-resistance requirements.
- Review account-level public access settings, bucket policies, and access permissions as part of a broader storage security assessment.
- Consider alerting on suspicious activity and changes to logging or security configurations.
- Monitor storage and logging costs.

## Tools and Technologies

AWS CLI · AWS CloudTrail · Amazon S3 · IAM Identity Center · JSON · Bash

## Disclaimer

This project was conducted in a personal AWS lab environment. The results describe the controls and configurations observed during testing; they do not constitute a complete security audit or a guarantee that the account is free from risk.
