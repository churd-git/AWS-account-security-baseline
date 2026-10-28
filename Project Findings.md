# Security Findings — AWS Account Security Baseline

## Assessment Summary

This lab validated selected controls for an AWS CloudTrail audit-logging pipeline. Evidence was collected using AWS CLI read-only commands and saved as JSON.

## Results

| Control | Result | Evidence |
|---|---|---|
| Multi-Region CloudTrail | Enabled | `cloudtrail-trail-config.json` |
| CloudTrail log-file validation | Enabled | `cloudtrail-trail-config.json` |
| S3 default encryption | SSE-S3 / AES-256 | `s3-encryption.json` |
| S3 Block Public Access | All four settings enabled | `s3-public-access-block.json` |
| Bucket policy public status | Not classified as public | `s3-bucket-policy-status.json` |

## Security Implications

Multi-Region CloudTrail helps capture supported management activity across Regions. Log-file validation supports integrity verification for delivered log files. SSE-S3 provides server-side encryption at rest, while Block Public Access reduces the risk of accidental public exposure.

The bucket policy status check provides an additional signal but is not a full authorization review.

## Limitations

- S3 data events are not enabled in this lab configuration.
- Bucket immutability and retention enforcement have not been verified.
- The bucket policy and IAM permissions have not undergone a complete least-privilege review.
- Account-level public access settings and all possible access paths have not been fully assessed.
- These findings represent selected control checks, not a complete AWS security audit.

## Recommended Next Steps

1. Review and reduce administrative permissions using least privilege.
2. Assess audit-log retention, deletion risks, and immutability requirements.
3. Evaluate data-event logging for selected sensitive resources.
4. Consider monitoring for changes to CloudTrail, logging destinations, and security settings.

## Evidence

The `evidence/` directory contains sanitized JSON output from the AWS CLI commands used to validate the controls. The evidence should be reviewed alongside the scope and limitations above.
