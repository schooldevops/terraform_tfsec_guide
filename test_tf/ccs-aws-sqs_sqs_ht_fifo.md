# CCS_AWS_SQS/SQS_HT_FIFO

```py
ccs-aws-sqs/sqs_ht_fifo git:(master) ▶ tfsec

Result #1 HIGH Queue is not encrypted
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 sqs_ht_fifo.tf Lines 11-27
───────┬───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   11  │ resource "aws_sqs_queue" "sqs_ht_fifo" {
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
   22  │   // HT FIFO
   23  │   deduplication_scope   = var.deduplication_scope
   24  │   fifo_throughput_limit = var.fifo_throughput_limit
   25  │
   26  │   tags                  = var.tags
   27  │ }
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
  disk i/o             7.309601ms
  parsing              725.565µs
  adaptation           225.625µs
  checks               13.487261ms
  total                21.748052ms

  counts
  ──────────────────────────────────────────
  modules downloaded   0
  modules processed    1
  blocks processed     22
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

- kms_master_key_id = "/blah" 처럼 sqs처리시 kms로 암호화하여 데이터를 전송해야한다. 
