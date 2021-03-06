# AWS Elasticache Redis 

## aws-elasticache-redis DEV 

- High 1건 발생: 
  - at_rest_encryption_enabled = true 값으로 처리 필요. (복제 대상 데이터에 대한 함호화 필요)

- 아래는 cluster_disable_large.tfvars 
  
```go
ccs-aws-elasticache-redis git:(master) ▶ tf dev/cluster_disable_large.tfvars .

Result #1 HIGH Replication group does not have at-rest encryption enabled.
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 cluster_disable.tf Line 29
───────┬───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
    7  │ resource "aws_elasticache_replication_group" "cluster_disable" {
    8  │   count = var.cluster_disable ? 1 : 0
    9  │
   10  │   replication_group_id          = var.cluster_name
   11  │   replication_group_description = var.cluster_name
   12  │
   13  │   // Elasticache Subnet Group: 캐시 서브넷 그룹의 이름
   14  │   subnet_group_name    = var.subnet_group_name
   15  │   port                 = var.port
   16  │   parameter_group_name = var.parameter_group_name
   17  │
   18  │   // Node 유형 및 수
   19  │   node_type             = var.node_type
   20  │   number_cache_clusters = var.number_cache_clusters
   21  │
   22  │   /* Default is false. See Amazon ElastiCache Documentation for more information.
   23  │     https://docs.aws.amazon.com/ko_kr/AmazonElastiCache/latest/APIReference/API_ModifyCacheCluster.html
   24  │   */
   25  │   apply_immediately = var.apply_immediately
   26  │
   27  │   // 노드의 수가 2개 이상일때 true 가능
   28  │   multi_az_enabled           = var.multi_az_enabled
   29  │   at_rest_encryption_enabled = var.at_rest_encryption_enabled        false
   30  │   transit_encryption_enabled = var.transit_encryption_enabled
   31  │   automatic_failover_enabled = var.automatic_failover_enabled
   32  │
   33  │   // Default: Engine "redis" 및 Engine Version "6.x"
   34  │   engine         = var.engine
   35  │   engine_version = var.engine_version
   36  │
   37  │   // Tags
   38  │   tags = var.tags
   39  │ }
───────┴───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
          ID aws-elasticache-enable-at-rest-encryption
      Impact At-rest data in the Replication Group could be compromised if accessed.
  Resolution Enable at-rest encryption for replication group

  More Information
  - https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elasticache/enable-at-rest-encryption/
  - https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/elasticache_replication_group#at_rest_encryption_enabled
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────


  timings
  ──────────────────────────────────────────
  disk i/o             9.216682ms
  parsing              3.001843ms
  adaptation           174.175µs
  checks               13.440199ms
  total                25.832899ms

  counts
  ──────────────────────────────────────────
  modules downloaded   0
  modules processed    1
  blocks processed     29
  files read           6

  results
  ──────────────────────────────────────────
  passed               1
  ignored              0
  critical             0
  high                 1
  medium               0
  low                  0

  1 passed, 1 potential problem(s) detected.
```

- 아래는 cluster_disable_medium.tfvars 

```py
ccs-aws-elasticache-redis git:(master) ▶ tf dev/cluster_disable_medium.tfvars .

Result #1 HIGH Replication group does not have at-rest encryption enabled.
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 cluster_disable.tf Line 29
───────┬───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
    7  │ resource "aws_elasticache_replication_group" "cluster_disable" {
    8  │   count = var.cluster_disable ? 1 : 0
    9  │
   10  │   replication_group_id          = var.cluster_name
   11  │   replication_group_description = var.cluster_name
   12  │
   13  │   // Elasticache Subnet Group: 캐시 서브넷 그룹의 이름
   14  │   subnet_group_name    = var.subnet_group_name
   15  │   port                 = var.port
   16  │   parameter_group_name = var.parameter_group_name
   17  │
   18  │   // Node 유형 및 수
   19  │   node_type             = var.node_type
   20  │   number_cache_clusters = var.number_cache_clusters
   21  │
   22  │   /* Default is false. See Amazon ElastiCache Documentation for more information.
   23  │     https://docs.aws.amazon.com/ko_kr/AmazonElastiCache/latest/APIReference/API_ModifyCacheCluster.html
   24  │   */
   25  │   apply_immediately = var.apply_immediately
   26  │
   27  │   // 노드의 수가 2개 이상일때 true 가능
   28  │   multi_az_enabled           = var.multi_az_enabled
   29  │   at_rest_encryption_enabled = var.at_rest_encryption_enabled        false
   30  │   transit_encryption_enabled = var.transit_encryption_enabled
   31  │   automatic_failover_enabled = var.automatic_failover_enabled
   32  │
   33  │   // Default: Engine "redis" 및 Engine Version "6.x"
   34  │   engine         = var.engine
   35  │   engine_version = var.engine_version
   36  │
   37  │   // Tags
   38  │   tags = var.tags
   39  │ }
───────┴───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
          ID aws-elasticache-enable-at-rest-encryption
      Impact At-rest data in the Replication Group could be compromised if accessed.
  Resolution Enable at-rest encryption for replication group

  More Information
  - https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elasticache/enable-at-rest-encryption/
  - https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/elasticache_replication_group#at_rest_encryption_enabled
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────


  timings
  ──────────────────────────────────────────
  disk i/o             1.47791ms
  parsing              9.66444ms
  adaptation           7.171233ms
  checks               21.759942ms
  total                40.073525ms

  counts
  ──────────────────────────────────────────
  modules downloaded   0
  modules processed    1
  blocks processed     29
  files read           6

  results
  ──────────────────────────────────────────
  passed               1
  ignored              0
  critical             0
  high                 1
  medium               0
  low                  0

  1 passed, 1 potential problem(s) detected.
```

- cluster_disable_small.tfvars 

```py
ccs-aws-elasticache-redis git:(master) ▶ tf dev/cluster_disable_small.tfvars .

Result #1 HIGH Replication group does not have at-rest encryption enabled.
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 cluster_disable.tf Line 29
───────┬───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
    7  │ resource "aws_elasticache_replication_group" "cluster_disable" {
    8  │   count = var.cluster_disable ? 1 : 0
    9  │
   10  │   replication_group_id          = var.cluster_name
   11  │   replication_group_description = var.cluster_name
   12  │
   13  │   // Elasticache Subnet Group: 캐시 서브넷 그룹의 이름
   14  │   subnet_group_name    = var.subnet_group_name
   15  │   port                 = var.port
   16  │   parameter_group_name = var.parameter_group_name
   17  │
   18  │   // Node 유형 및 수
   19  │   node_type             = var.node_type
   20  │   number_cache_clusters = var.number_cache_clusters
   21  │
   22  │   /* Default is false. See Amazon ElastiCache Documentation for more information.
   23  │     https://docs.aws.amazon.com/ko_kr/AmazonElastiCache/latest/APIReference/API_ModifyCacheCluster.html
   24  │   */
   25  │   apply_immediately = var.apply_immediately
   26  │
   27  │   // 노드의 수가 2개 이상일때 true 가능
   28  │   multi_az_enabled           = var.multi_az_enabled
   29  │   at_rest_encryption_enabled = var.at_rest_encryption_enabled        false
   30  │   transit_encryption_enabled = var.transit_encryption_enabled
   31  │   automatic_failover_enabled = var.automatic_failover_enabled
   32  │
   33  │   // Default: Engine "redis" 및 Engine Version "6.x"
   34  │   engine         = var.engine
   35  │   engine_version = var.engine_version
   36  │
   37  │   // Tags
   38  │   tags = var.tags
   39  │ }
───────┴───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
          ID aws-elasticache-enable-at-rest-encryption
      Impact At-rest data in the Replication Group could be compromised if accessed.
  Resolution Enable at-rest encryption for replication group

  More Information
  - https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elasticache/enable-at-rest-encryption/
  - https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/elasticache_replication_group#at_rest_encryption_enabled
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────


Result #2 HIGH Replication group does not have transit encryption enabled.
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 cluster_disable.tf Line 30
───────┬───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
    7  │ resource "aws_elasticache_replication_group" "cluster_disable" {
    8  │   count = var.cluster_disable ? 1 : 0
    9  │
   10  │   replication_group_id          = var.cluster_name
   11  │   replication_group_description = var.cluster_name
   12  │
   13  │   // Elasticache Subnet Group: 캐시 서브넷 그룹의 이름
   14  │   subnet_group_name    = var.subnet_group_name
   15  │   port                 = var.port
   16  │   parameter_group_name = var.parameter_group_name
   17  │
   18  │   // Node 유형 및 수
   19  │   node_type             = var.node_type
   20  │   number_cache_clusters = var.number_cache_clusters
   21  │
   22  │   /* Default is false. See Amazon ElastiCache Documentation for more information.
   23  │     https://docs.aws.amazon.com/ko_kr/AmazonElastiCache/latest/APIReference/API_ModifyCacheCluster.html
   24  │   */
   25  │   apply_immediately = var.apply_immediately
   26  │
   27  │   // 노드의 수가 2개 이상일때 true 가능
   28  │   multi_az_enabled           = var.multi_az_enabled
   29  │   at_rest_encryption_enabled = var.at_rest_encryption_enabled
   30  │   transit_encryption_enabled = var.transit_encryption_enabled        false
   31  │   automatic_failover_enabled = var.automatic_failover_enabled
   32  │
   33  │   // Default: Engine "redis" 및 Engine Version "6.x"
   34  │   engine         = var.engine
   35  │   engine_version = var.engine_version
   36  │
   37  │   // Tags
   38  │   tags = var.tags
   39  │ }
───────┴───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
          ID aws-elasticache-enable-in-transit-encryption
      Impact In transit data in the Replication Group could be read if intercepted
  Resolution Enable in transit encryption for replication group

  More Information
  - https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elasticache/enable-in-transit-encryption/
  - https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/elasticache_replication_group#transit_encryption_enabled
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────


  timings
  ──────────────────────────────────────────
  disk i/o             1.0218ms
  parsing              1.398132ms
  adaptation           226.974µs
  checks               18.939778ms
  total                21.586684ms

  counts
  ──────────────────────────────────────────
  modules downloaded   0
  modules processed    1
  blocks processed     29
  files read           6

  results
  ──────────────────────────────────────────
  passed               0
  ignored              0
  critical             0
  high                 2
  medium               0
  low                  0

  2 potential problem(s) detected.
```

## aws-elasticache-redis PROD

```py
TERRAFORM/ccs-aws-elasticache-redis git:(master) ▶ tf prod/cluster_disable_small.tfvars .

Result #1 HIGH Replication group does not have at-rest encryption enabled.
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 cluster_disable.tf Line 29
───────┬───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
    7  │ resource "aws_elasticache_replication_group" "cluster_disable" {
    8  │   count = var.cluster_disable ? 1 : 0
    9  │
   10  │   replication_group_id          = var.cluster_name
   11  │   replication_group_description = var.cluster_name
   12  │
   13  │   // Elasticache Subnet Group: 캐시 서브넷 그룹의 이름
   14  │   subnet_group_name    = var.subnet_group_name
   15  │   port                 = var.port
   16  │   parameter_group_name = var.parameter_group_name
   17  │
   18  │   // Node 유형 및 수
   19  │   node_type             = var.node_type
   20  │   number_cache_clusters = var.number_cache_clusters
   21  │
   22  │   /* Default is false. See Amazon ElastiCache Documentation for more information.
   23  │     https://docs.aws.amazon.com/ko_kr/AmazonElastiCache/latest/APIReference/API_ModifyCacheCluster.html
   24  │   */
   25  │   apply_immediately = var.apply_immediately
   26  │
   27  │   // 노드의 수가 2개 이상일때 true 가능
   28  │   multi_az_enabled           = var.multi_az_enabled
   29  │   at_rest_encryption_enabled = var.at_rest_encryption_enabled        false
   30  │   transit_encryption_enabled = var.transit_encryption_enabled
   31  │   automatic_failover_enabled = var.automatic_failover_enabled
   32  │
   33  │   // Default: Engine "redis" 및 Engine Version "6.x"
   34  │   engine         = var.engine
   35  │   engine_version = var.engine_version
   36  │
   37  │   // Tags
   38  │   tags = var.tags
   39  │ }
───────┴───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
          ID aws-elasticache-enable-at-rest-encryption
      Impact At-rest data in the Replication Group could be compromised if accessed.
  Resolution Enable at-rest encryption for replication group

  More Information
  - https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elasticache/enable-at-rest-encryption/
  - https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/elasticache_replication_group#at_rest_encryption_enabled
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────


Result #2 HIGH Replication group does not have transit encryption enabled.
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 cluster_disable.tf Line 30
───────┬───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
    7  │ resource "aws_elasticache_replication_group" "cluster_disable" {
    8  │   count = var.cluster_disable ? 1 : 0
    9  │
   10  │   replication_group_id          = var.cluster_name
   11  │   replication_group_description = var.cluster_name
   12  │
   13  │   // Elasticache Subnet Group: 캐시 서브넷 그룹의 이름
   14  │   subnet_group_name    = var.subnet_group_name
   15  │   port                 = var.port
   16  │   parameter_group_name = var.parameter_group_name
   17  │
   18  │   // Node 유형 및 수
   19  │   node_type             = var.node_type
   20  │   number_cache_clusters = var.number_cache_clusters
   21  │
   22  │   /* Default is false. See Amazon ElastiCache Documentation for more information.
   23  │     https://docs.aws.amazon.com/ko_kr/AmazonElastiCache/latest/APIReference/API_ModifyCacheCluster.html
   24  │   */
   25  │   apply_immediately = var.apply_immediately
   26  │
   27  │   // 노드의 수가 2개 이상일때 true 가능
   28  │   multi_az_enabled           = var.multi_az_enabled
   29  │   at_rest_encryption_enabled = var.at_rest_encryption_enabled
   30  │   transit_encryption_enabled = var.transit_encryption_enabled        false
   31  │   automatic_failover_enabled = var.automatic_failover_enabled
   32  │
   33  │   // Default: Engine "redis" 및 Engine Version "6.x"
   34  │   engine         = var.engine
   35  │   engine_version = var.engine_version
   36  │
   37  │   // Tags
   38  │   tags = var.tags
   39  │ }
───────┴───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
          ID aws-elasticache-enable-in-transit-encryption
      Impact In transit data in the Replication Group could be read if intercepted
  Resolution Enable in transit encryption for replication group

  More Information
  - https://aquasecurity.github.io/tfsec/v1.18.0/checks/aws/elasticache/enable-in-transit-encryption/
  - https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/elasticache_replication_group#transit_encryption_enabled
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────


  timings
  ──────────────────────────────────────────
  disk i/o             185.123µs
  parsing              1.115558ms
  adaptation           166.821µs
  checks               11.92953ms
  total                13.397032ms

  counts
  ──────────────────────────────────────────
  modules downloaded   0
  modules processed    1
  blocks processed     29
  files read           6

  results
  ──────────────────────────────────────────
  passed               0
  ignored              0
  critical             0
  high                 2
  medium               0
  low                  0

  2 potential problem(s) detected.
```