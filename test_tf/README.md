# TFSEC 의경우 치명도

## CRITICAL, HIGH, MEDIUM, LOW

- 치명도 레벨은 위와 같이 나열된다. 
- CRITICAL 의 경우 반드시 처리하고 진행하기 
- HIGH 의 경우 설치환경 (Prod/Dev)에 따라 차등 지정 가능
- MEDIUM/LOW 등의 경우 조직에 따라 처리 여부를 결정 

## 최소 치명도 및 포함/제외 지정하기 

- https://aquasecurity.github.io/tfsec/v1.18.0/guides/configuration/config/ 참고 

## CRITICAL, HIGH

### CRITICAL

- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/cloudfront/enforce-https/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/ec2/no-secrets-in-user-data/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/ecs/no-plaintext-secrets/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/eks/no-public-cluster-access/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/eks/no-public-cluster-access-to-cidr/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elastic-search/enforce-https/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elb/http-not-used/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elb/use-secure-tls-policy/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/lambda/restrict-source-arn/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/rds/no-classic-resources/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/rds/no-public-db-access/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/ssm/avoid-leaks-via-http/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/vpc/no-excessive-port-access/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/vpc/no-public-egress-sgr/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/vpc/no-public-ingress-acl/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/vpc/no-public-ingress-sgr/

### HIGH

- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/api-gateway/use-secure-tls-policy/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/athena/enable-at-rest-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/athena/no-encryption-override/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/autoscaling/enable-at-rest-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/autoscaling/enforce-http-token-imds/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/autoscaling/no-public-ip/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/autoscaling/no-secrets-in-user-data/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/autoscaling/no-sensitive-info/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/cloudfront/enable-waf/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/cloudfront/use-secure-tls-policy/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/cloudtrail/enable-at-rest-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/cloudtrail/enable-log-validation/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/codebuild/enable-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/config/aggregate-all-regions/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/documentdb/enable-storage-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/dynamodb/enable-at-rest-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/ebs/enable-volume-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/ec2/enable-at-rest-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/ec2/enforce-http-token-imds/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/ecr/enable-image-scans/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/ecr/enforce-immutable-repository/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/ecr/no-public-access/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/ecs/enable-in-transit-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/efs/enable-at-rest-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/eks/encrypt-secrets/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elastic-search/enable-domain-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elastic-search/enable-in-transit-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elastic-search/use-secure-tls-policy/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elasticache/enable-at-rest-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elasticache/enable-in-transit-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elb/alb-not-public/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elb/drop-invalid-headers/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/iam/no-policy-wildcards/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/kinesis/enable-in-transit-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/mq/no-public-access/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/msk/enable-in-transit-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/neptune/enable-storage-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/neptune/encryption-customer-key/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/rds/enable-performance-insights-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/rds/encrypt-cluster-storage-data/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/rds/encrypt-instance-storage-data/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/redshift/encryption-customer-key/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/redshift/use-vpc/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/s3/block-public-acls/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/s3/block-public-policy/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/s3/enable-bucket-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/s3/encryption-customer-key/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/s3/ignore-public-acls/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/s3/no-public-access-with-acl/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/s3/no-public-buckets/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/sns/enable-topic-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/sqs/enable-queue-encryption/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/sqs/no-wildcards-in-policy-documents/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/vpc/no-default-vpc/
- https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/workspaces/enable-disk-encryption/

