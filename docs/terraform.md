<!-- markdownlint-disable -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 0.13.0 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 3.0 |
| <a name="requirement_random"></a> [random](#requirement\_random) | >= 3.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | >= 3.0 |
| <a name="provider_random"></a> [random](#provider\_random) | >= 3.0 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_security_group"></a> [security\_group](#module\_security\_group) | cloudposse/security-group/aws | 0.3.1 |
| <a name="module_this"></a> [this](#module\_this) | cloudposse/label/null | 0.24.1 |

## Resources

| Name | Type |
|------|------|
| [aws_mq_broker.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/mq_broker) | resource |
| [aws_ssm_parameter.mq_application_password](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ssm_parameter) | resource |
| [aws_ssm_parameter.mq_application_username](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ssm_parameter) | resource |
| [aws_ssm_parameter.mq_master_password](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ssm_parameter) | resource |
| [aws_ssm_parameter.mq_master_username](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ssm_parameter) | resource |
| [random_password.mq_admin_password](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/password) | resource |
| [random_password.mq_application_password](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/password) | resource |
| [random_string.mq_admin_user](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/string) | resource |
| [random_string.mq_application_user](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/string) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_additional_tag_map"></a> [additional\_tag\_map](#input\_additional\_tag\_map) | Additional tags for appending to tags\_as\_list\_of\_maps. Not added to `tags`. | `map(string)` | `{}` | no |
| <a name="input_apply_immediately"></a> [apply\_immediately](#input\_apply\_immediately) | Specifies whether any cluster modifications are applied immediately, or during the next maintenance window | `bool` | `false` | no |
| <a name="input_attributes"></a> [attributes](#input\_attributes) | Additional attributes (e.g. `1`) | `list(string)` | `[]` | no |
| <a name="input_audit_log_enabled"></a> [audit\_log\_enabled](#input\_audit\_log\_enabled) | Enables audit logging. User management action made using JMX or the ActiveMQ Web Console is logged | `bool` | `true` | no |
| <a name="input_auto_minor_version_upgrade"></a> [auto\_minor\_version\_upgrade](#input\_auto\_minor\_version\_upgrade) | Enables automatic upgrades to new minor versions for brokers, as Apache releases the versions | `bool` | `false` | no |
| <a name="input_context"></a> [context](#input\_context) | Single object for setting entire context at once.<br>See description of individual variables for details.<br>Leave string and numeric variables as `null` to use default value.<br>Individual variable settings (non-null) override settings in context object,<br>except for attributes, tags, and additional\_tag\_map, which are merged. | `any` | <pre>{<br>  "additional_tag_map": {},<br>  "attributes": [],<br>  "delimiter": null,<br>  "enabled": true,<br>  "environment": null,<br>  "id_length_limit": null,<br>  "label_key_case": null,<br>  "label_order": [],<br>  "label_value_case": null,<br>  "name": null,<br>  "namespace": null,<br>  "regex_replace_chars": null,<br>  "stage": null,<br>  "tags": {}<br>}</pre> | no |
| <a name="input_delimiter"></a> [delimiter](#input\_delimiter) | Delimiter to be used between `namespace`, `environment`, `stage`, `name` and `attributes`.<br>Defaults to `-` (hyphen). Set to `""` to use no delimiter at all. | `string` | `null` | no |
| <a name="input_deployment_mode"></a> [deployment\_mode](#input\_deployment\_mode) | The deployment mode of the broker. Supported: SINGLE\_INSTANCE and ACTIVE\_STANDBY\_MULTI\_AZ | `string` | `"ACTIVE_STANDBY_MULTI_AZ"` | no |
| <a name="input_enabled"></a> [enabled](#input\_enabled) | Set to false to prevent the module from creating any resources | `bool` | `null` | no |
| <a name="input_encryption_enabled"></a> [encryption\_enabled](#input\_encryption\_enabled) | Flag to enable/disable Amazon MQ encryption at rest | `bool` | `true` | no |
| <a name="input_engine_type"></a> [engine\_type](#input\_engine\_type) | Type of broker engine, `ActiveMQ` or `RabbitMQ` | `string` | `"ActiveMQ"` | no |
| <a name="input_engine_version"></a> [engine\_version](#input\_engine\_version) | The version of the broker engine. See https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/broker-engine.html for more details | `string` | `"5.15.14"` | no |
| <a name="input_environment"></a> [environment](#input\_environment) | Environment, e.g. 'uw2', 'us-west-2', OR 'prod', 'staging', 'dev', 'UAT' | `string` | `null` | no |
| <a name="input_general_log_enabled"></a> [general\_log\_enabled](#input\_general\_log\_enabled) | Enables general logging via CloudWatch | `bool` | `true` | no |
| <a name="input_host_instance_type"></a> [host\_instance\_type](#input\_host\_instance\_type) | The broker's instance type. e.g. mq.t2.micro or mq.m4.large | `string` | `"mq.t3.micro"` | no |
| <a name="input_id_length_limit"></a> [id\_length\_limit](#input\_id\_length\_limit) | Limit `id` to this many characters (minimum 6).<br>Set to `0` for unlimited length.<br>Set to `null` for default, which is `0`.<br>Does not affect `id_full`. | `number` | `null` | no |
| <a name="input_kms_mq_key_arn"></a> [kms\_mq\_key\_arn](#input\_kms\_mq\_key\_arn) | ARN of the AWS KMS key used for Amazon MQ encryption | `string` | `null` | no |
| <a name="input_kms_ssm_key_arn"></a> [kms\_ssm\_key\_arn](#input\_kms\_ssm\_key\_arn) | ARN of the AWS KMS key used for SSM encryption | `string` | `"alias/aws/ssm"` | no |
| <a name="input_label_key_case"></a> [label\_key\_case](#input\_label\_key\_case) | The letter case of label keys (`tag` names) (i.e. `name`, `namespace`, `environment`, `stage`, `attributes`) to use in `tags`.<br>Possible values: `lower`, `title`, `upper`.<br>Default value: `title`. | `string` | `null` | no |
| <a name="input_label_order"></a> [label\_order](#input\_label\_order) | The naming order of the id output and Name tag.<br>Defaults to ["namespace", "environment", "stage", "name", "attributes"].<br>You can omit any of the 5 elements, but at least one must be present. | `list(string)` | `null` | no |
| <a name="input_label_value_case"></a> [label\_value\_case](#input\_label\_value\_case) | The letter case of output label values (also used in `tags` and `id`).<br>Possible values: `lower`, `title`, `upper` and `none` (no transformation).<br>Default value: `lower`. | `string` | `null` | no |
| <a name="input_maintenance_day_of_week"></a> [maintenance\_day\_of\_week](#input\_maintenance\_day\_of\_week) | The maintenance day of the week. e.g. MONDAY, TUESDAY, or WEDNESDAY | `string` | `"SUNDAY"` | no |
| <a name="input_maintenance_time_of_day"></a> [maintenance\_time\_of\_day](#input\_maintenance\_time\_of\_day) | The maintenance time, in 24-hour format. e.g. 02:00 | `string` | `"03:00"` | no |
| <a name="input_maintenance_time_zone"></a> [maintenance\_time\_zone](#input\_maintenance\_time\_zone) | The maintenance time zone, in either the Country/City format, or the UTC offset format. e.g. CET | `string` | `"UTC"` | no |
| <a name="input_mq_admin_password"></a> [mq\_admin\_password](#input\_mq\_admin\_password) | Admin password | `string` | `null` | no |
| <a name="input_mq_admin_user"></a> [mq\_admin\_user](#input\_mq\_admin\_user) | Admin username | `string` | `null` | no |
| <a name="input_mq_application_password"></a> [mq\_application\_password](#input\_mq\_application\_password) | Application password | `string` | `null` | no |
| <a name="input_mq_application_user"></a> [mq\_application\_user](#input\_mq\_application\_user) | Application username | `string` | `null` | no |
| <a name="input_name"></a> [name](#input\_name) | Solution name, e.g. 'app' or 'jenkins' | `string` | `null` | no |
| <a name="input_namespace"></a> [namespace](#input\_namespace) | Namespace, which could be your organization name or abbreviation, e.g. 'eg' or 'cp' | `string` | `null` | no |
| <a name="input_overwrite_ssm_parameter"></a> [overwrite\_ssm\_parameter](#input\_overwrite\_ssm\_parameter) | Whether to overwrite an existing SSM parameter | `bool` | `true` | no |
| <a name="input_publicly_accessible"></a> [publicly\_accessible](#input\_publicly\_accessible) | Whether to enable connections from applications outside of the VPC that hosts the broker's subnets | `bool` | `false` | no |
| <a name="input_regex_replace_chars"></a> [regex\_replace\_chars](#input\_regex\_replace\_chars) | Regex to replace chars with empty string in `namespace`, `environment`, `stage` and `name`.<br>If not set, `"/[^a-zA-Z0-9-]/"` is used to remove all characters other than hyphens, letters and digits. | `string` | `null` | no |
| <a name="input_security_group_description"></a> [security\_group\_description](#input\_security\_group\_description) | The Security Group description. | `string` | `"AmazonMQ Security Group"` | no |
| <a name="input_security_group_enabled"></a> [security\_group\_enabled](#input\_security\_group\_enabled) | Whether to create Security Group. | `bool` | `true` | no |
| <a name="input_security_group_rules"></a> [security\_group\_rules](#input\_security\_group\_rules) | A list of maps of Security Group rules. <br>The values of map is fully complated with `aws_security_group_rule` resource. <br>To get more info see https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group_rule . | `list(any)` | <pre>[<br>  {<br>    "cidr_blocks": [<br>      "0.0.0.0/0"<br>    ],<br>    "description": "Allow all outbound traffic",<br>    "from_port": 0,<br>    "protocol": "-1",<br>    "to_port": 65535,<br>    "type": "egress"<br>  }<br>]</pre> | no |
| <a name="input_security_group_use_name_prefix"></a> [security\_group\_use\_name\_prefix](#input\_security\_group\_use\_name\_prefix) | Whether to create a default Security Group with unique name beginning with the normalized prefix. | `bool` | `false` | no |
| <a name="input_security_groups"></a> [security\_groups](#input\_security\_groups) | A list of Security Group IDs to associate with AmazonMQ. | `list(string)` | `[]` | no |
| <a name="input_ssm_parameter_name_format"></a> [ssm\_parameter\_name\_format](#input\_ssm\_parameter\_name\_format) | SSM parameter name format | `string` | `"/%s/%s"` | no |
| <a name="input_ssm_path"></a> [ssm\_path](#input\_ssm\_path) | SSM path | `string` | `"mq"` | no |
| <a name="input_stage"></a> [stage](#input\_stage) | Stage, e.g. 'prod', 'staging', 'dev', OR 'source', 'build', 'test', 'deploy', 'release' | `string` | `null` | no |
| <a name="input_subnet_ids"></a> [subnet\_ids](#input\_subnet\_ids) | List of VPC subnet IDs | `list(string)` | n/a | yes |
| <a name="input_tags"></a> [tags](#input\_tags) | Additional tags (e.g. `map('BusinessUnit','XYZ')` | `map(string)` | `{}` | no |
| <a name="input_use_aws_owned_key"></a> [use\_aws\_owned\_key](#input\_use\_aws\_owned\_key) | Boolean to enable an AWS owned Key Management Service (KMS) Customer Master Key (CMK) for Amazon MQ encryption that is not in your account | `bool` | `true` | no |
| <a name="input_vpc_id"></a> [vpc\_id](#input\_vpc\_id) | VPC ID to create the broker in | `string` | n/a | yes |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_admin_username"></a> [admin\_username](#output\_admin\_username) | AmazonMQ admin username |
| <a name="output_application_username"></a> [application\_username](#output\_application\_username) | AmazonMQ application username |
| <a name="output_broker_arn"></a> [broker\_arn](#output\_broker\_arn) | AmazonMQ broker ARN |
| <a name="output_broker_id"></a> [broker\_id](#output\_broker\_id) | AmazonMQ broker ID |
| <a name="output_primary_amqp_ssl_endpoint"></a> [primary\_amqp\_ssl\_endpoint](#output\_primary\_amqp\_ssl\_endpoint) | AmazonMQ primary AMQP+SSL endpoint |
| <a name="output_primary_console_url"></a> [primary\_console\_url](#output\_primary\_console\_url) | AmazonMQ active web console URL |
| <a name="output_primary_ip_address"></a> [primary\_ip\_address](#output\_primary\_ip\_address) | AmazonMQ primary IP address |
| <a name="output_primary_mqtt_ssl_endpoint"></a> [primary\_mqtt\_ssl\_endpoint](#output\_primary\_mqtt\_ssl\_endpoint) | AmazonMQ primary MQTT+SSL endpoint |
| <a name="output_primary_ssl_endpoint"></a> [primary\_ssl\_endpoint](#output\_primary\_ssl\_endpoint) | AmazonMQ primary SSL endpoint |
| <a name="output_primary_stomp_ssl_endpoint"></a> [primary\_stomp\_ssl\_endpoint](#output\_primary\_stomp\_ssl\_endpoint) | AmazonMQ primary STOMP+SSL endpoint |
| <a name="output_primary_wss_endpoint"></a> [primary\_wss\_endpoint](#output\_primary\_wss\_endpoint) | AmazonMQ primary WSS endpoint |
| <a name="output_secondary_amqp_ssl_endpoint"></a> [secondary\_amqp\_ssl\_endpoint](#output\_secondary\_amqp\_ssl\_endpoint) | AmazonMQ secondary AMQP+SSL endpoint |
| <a name="output_secondary_console_url"></a> [secondary\_console\_url](#output\_secondary\_console\_url) | AmazonMQ secondary web console URL |
| <a name="output_secondary_ip_address"></a> [secondary\_ip\_address](#output\_secondary\_ip\_address) | AmazonMQ secondary IP address |
| <a name="output_secondary_mqtt_ssl_endpoint"></a> [secondary\_mqtt\_ssl\_endpoint](#output\_secondary\_mqtt\_ssl\_endpoint) | AmazonMQ secondary MQTT+SSL endpoint |
| <a name="output_secondary_ssl_endpoint"></a> [secondary\_ssl\_endpoint](#output\_secondary\_ssl\_endpoint) | AmazonMQ secondary SSL endpoint |
| <a name="output_secondary_stomp_ssl_endpoint"></a> [secondary\_stomp\_ssl\_endpoint](#output\_secondary\_stomp\_ssl\_endpoint) | AmazonMQ secondary STOMP+SSL endpoint |
| <a name="output_secondary_wss_endpoint"></a> [secondary\_wss\_endpoint](#output\_secondary\_wss\_endpoint) | AmazonMQ secondary WSS endpoint |
| <a name="output_security_group_arn"></a> [security\_group\_arn](#output\_security\_group\_arn) | AmazonMQ Security Group ARN |
| <a name="output_security_group_id"></a> [security\_group\_id](#output\_security\_group\_id) | AmazonMQ Security Group ID |
| <a name="output_security_group_name"></a> [security\_group\_name](#output\_security\_group\_name) | AmazonMQ Security Group name |
<!-- markdownlint-restore -->
