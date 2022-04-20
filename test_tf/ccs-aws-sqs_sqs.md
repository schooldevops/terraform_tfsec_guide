# CCS-AWS-SQS/SQS

```py
ccs-aws-sqs/sqs git:(master) ▶ tfsec

Result #1 HIGH Queue is not encrypted
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 sqs.tf Lines 11-23
───────┬───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   11  │ resource "aws_sqs_queue" "sqs" {
   12  │   /* kms_master_key_id           = var.kms_key */
   13  │   name                        = var.sqs_name
   14  │   delay_seconds               = var.delay_seconds
   15  │   max_message_size            = var.max_message_size
   16  │   message_retention_seconds   = var.message_retention_seconds
   17  │   receive_wait_time_seconds   = var.receive_wait_time_seconds
   18  │   visibility_timeout_seconds  = var.visibility_timeout_seconds
   19  │   fifo_queue                  = var.fifo_queue
   20  │   content_based_deduplication = var.content_based_deduplication
   21  │
   22  │   tags = var.tags
   23  │ }
───────┴───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
          ID aws-sqs-enable-queue-encryption
      Impact The SQS queue messages could be read if compromised
  Resolution Turn on SQS Queue encryption

  More Information
  - https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/sqs/enable-queue-encryption/
  - https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/sqs_queue#server-side-encryption-sse
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────


  timings
  ──────────────────────────────────────────
  disk i/o             1.028966ms
  parsing              1.046522ms
  adaptation           247.482µs
  checks               15.652459ms
  total                17.975429ms

  counts
  ──────────────────────────────────────────
  modules downloaded   0
  modules processed    1
  blocks processed     20
  files read           4

  results
  ──────────────────────────────────────────
  passed               2
  ignored              0
  critical             0
  high                 1
  medium               0
  low                  0

  2 passed, 1 potential problem(s) detected.
```

- kms_master_key_id = "/blah" 처럼 sqs 메시지 전송시 암호화 필요 

