# Backup Strategy

## EBS Snapshot Backup

- AWS Backup plan configured
- Daily automated snapshots
- Backup vault encryption enabled
- Lifecycle transition to cold storage
- Resource-based backup tagging

## SQL Native Backups

- SQL .bak files exported
- Uploaded to S3 bucket
- Intelligent-Tiering enabled
- Public access blocked

## Restore Strategy

- EBS snapshot restore capability
- SQL database restore from S3 backup
- Defined recovery workflow provided during KT session
