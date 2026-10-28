
# AWS Security Architecture

```mermaid
flowchart TD
    A["Administrator<br/>IAM Identity Center + AWS CLI"]
    B["AWS Management API Activity"]
    C["AWS CloudTrail<br/>Multi-Region Trail"]
    D["Log File Validation<br/>Enabled"]
    E["Amazon S3<br/>CloudTrail Log Storage"]
    F["SSE-S3 Encryption<br/>AES-256"]
    G["S3 Block Public Access<br/>All Four Settings Enabled"]

    A --> B
    B --> C
    C --> D
    C --> E
    E --> F
    E --> G
```

## Architecture Notes

CloudTrail records supported AWS management events and delivers logs to an Amazon S3 bucket. Log-file validation is enabled to help verify the integrity of delivered log files. The destination bucket uses SSE-S3 encryption and has all four bucket-level S3 Block Public Access settings enabled.

S3 data events are not enabled in this lab configuration.
