---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "aquasec_host_runtime_policy Resource - terraform-provider-aquasec"
subcategory: ""
description: |-
  
---

# aquasec_host_runtime_policy (Resource)



## Example Usage

```terraform
resource "aquasec_host_runtime_policy" "host_runtime_policy" {
  name = "host_runtime_policy"
  description = "host_runtime_policy"
  enabled = true
  enforce = false
  block_cryptocurrency_mining = true
  audit_brute_force_login = true
  enable_ip_reputation_security = true
  blocked_files = [
    "blocked",
  ]
  file_integrity_monitoring {
    monitor_create      = true
    monitor_read        = true
    monitor_modify      = true
    monitor_delete      = true
    monitor_attributes  = true
    monitored_paths     = ["paths"]
    excluded_paths      = ["expaths"]
    monitored_processes = ["process"]
    excluded_processes  = ["exprocess"]
    monitored_users     = ["user"]
    excluded_users      = ["expuser"]
  }
  audit_all_os_user_activity    = true
  audit_full_command_arguments  = true
  audit_host_successful_login_events = true
  audit_host_failed_login_events = true
  audit_user_account_management = true
  os_users_allowed = [
    "user1",
  ]
  os_groups_allowed = [
    "group1",
  ]
  os_users_blocked = [
    "user2",
  ]
  os_groups_blocked = [
    "group2",
  ]
  package_block = [
    "package1"
  ]
  port_scanning_detection = true
  monitor_system_time_changes = true
  monitor_windows_services    = true
  monitor_system_log_integrity = true
  windows_registry_monitoring {
    monitor_create      = true
    monitor_read        = true
    monitor_modify      = true
    monitor_delete      = true
    monitor_attributes  = true
    monitored_paths     = ["paths"]
    excluded_paths      = ["expaths"]
    monitored_processes = ["process"]
    excluded_processes  = ["exprocess"]
    monitored_users     = ["user"]
    excluded_users      = ["expuser"]
  }
  windows_registry_protection {
    protected_paths     = ["paths"]
    excluded_paths      = ["expaths"]
    protected_processes = ["process"]
    excluded_processes  = ["exprocess"]
    protected_users     = ["user"]
    excluded_users      = ["expuser"]
  }
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `name` (String) Name of the host runtime policy

### Optional

- `application_scopes` (List of String) Indicates the application scope of the service.
- `audit_all_os_user_activity` (Boolean) If true, all process activity will be audited.
- `audit_brute_force_login` (Boolean) Detects brute force login attempts
- `audit_full_command_arguments` (Boolean) If true, full command arguments will be audited.
- `audit_host_failed_login_events` (Boolean) If true, host failed logins will be audited.
- `audit_host_successful_login_events` (Boolean) If true, host successful logins will be audited.
- `audit_user_account_management` (Boolean) If true, account management will be audited.
- `block_cryptocurrency_mining` (Boolean) Detect and prevent communication to DNS/IP addresses known to be used for Cryptocurrency Mining
- `blocked_files` (List of String) List of files that are prevented from being read, modified and executed in the containers.
- `description` (String) The description of the host runtime policy
- `enable_ip_reputation_security` (Boolean) If true, detect and prevent communication from containers to IP addresses known to have a bad reputation.
- `enabled` (Boolean) Indicates if the runtime policy is enabled or not.
- `enforce` (Boolean) Indicates that policy should effect container execution (not just for audit).
- `enforce_after_days` (Number) Indicates the number of days after which the runtime policy will be changed to enforce mode.
- `file_integrity_monitoring` (Block List, Max: 1) Configuration for file integrity monitoring. (see [below for nested schema](#nestedblock--file_integrity_monitoring))
- `monitor_system_log_integrity` (Boolean) If true, system log will be monitored.
- `monitor_system_time_changes` (Boolean) If true, system time changes will be monitored.
- `monitor_windows_services` (Boolean) If true, windows service operations will be monitored.
- `os_groups_allowed` (List of String) List of OS (Linux or Windows) groups that are allowed to authenticate to the host, and block authentication requests from all others. Groups can be either Linux groups or Windows AD groups.
- `os_groups_blocked` (List of String) List of OS (Linux or Windows) groups that are not allowed to authenticate to the host, and block authentication requests from all others. Groups can be either Linux groups or Windows AD groups.
- `os_users_allowed` (List of String) List of OS (Linux or Windows) users that are allowed to authenticate to the host, and block authentication requests from all others.
- `os_users_blocked` (List of String) List of OS (Linux or Windows) users that are not allowed to authenticate to the host, and block authentication requests from all others.
- `package_block` (List of String) List of packages that are not allowed read, write or execute all files that under the packages.
- `port_scanning_detection` (Boolean) If true, port scanning behaviors will be audited.
- `scope_expression` (String) Logical expression of how to compute the dependency of the scope variables.
- `scope_variables` (Block List) List of scope attributes. (see [below for nested schema](#nestedblock--scope_variables))
- `windows_registry_monitoring` (Block List, Max: 1) Configuration for windows registry monitoring. (see [below for nested schema](#nestedblock--windows_registry_monitoring))
- `windows_registry_protection` (Block List, Max: 1) Configuration for windows registry protection. (see [below for nested schema](#nestedblock--windows_registry_protection))

### Read-Only

- `author` (String) Username of the account that created the service.
- `id` (String) The ID of this resource.

<a id="nestedblock--file_integrity_monitoring"></a>
### Nested Schema for `file_integrity_monitoring`

Optional:

- `excluded_paths` (List of String) List of paths to be excluded from being monitored.
- `excluded_processes` (List of String) List of processes to be excluded from being monitored.
- `excluded_users` (List of String) List of users to be excluded from being monitored.
- `monitor_attributes` (Boolean) If true, add attributes operations will be monitored.
- `monitor_create` (Boolean) If true, create operations will be monitored.
- `monitor_delete` (Boolean) If true, deletion operations will be monitored.
- `monitor_modify` (Boolean) If true, modification operations will be monitored.
- `monitor_read` (Boolean) If true, read operations will be monitored.
- `monitored_paths` (List of String) List of paths to be monitored.
- `monitored_processes` (List of String) List of processes to be monitored.
- `monitored_users` (List of String) List of users to be monitored.


<a id="nestedblock--scope_variables"></a>
### Nested Schema for `scope_variables`

Required:

- `attribute` (String) Class of supported scope.
- `value` (String) Value assigned to the attribute.


<a id="nestedblock--windows_registry_monitoring"></a>
### Nested Schema for `windows_registry_monitoring`

Optional:

- `excluded_paths` (List of String) List of paths to be excluded from being monitored.
- `excluded_processes` (List of String) List of registry processes to be excluded from being monitored.
- `excluded_users` (List of String) List of registry users to be excluded from being monitored.
- `monitor_attributes` (Boolean) If true, add attributes operations will be monitored.
- `monitor_create` (Boolean) If true, create operations will be monitored.
- `monitor_delete` (Boolean) If true, deletion operations will be monitored.
- `monitor_modify` (Boolean) If true, modification operations will be monitored.
- `monitor_read` (Boolean) If true, read operations will be monitored.
- `monitored_paths` (List of String) List of paths to be monitored.
- `monitored_processes` (List of String) List of registry processes to be monitored.
- `monitored_users` (List of String) List of registry users to be monitored.


<a id="nestedblock--windows_registry_protection"></a>
### Nested Schema for `windows_registry_protection`

Optional:

- `excluded_paths` (List of String) List of registry paths to be excluded from being protected.
- `excluded_processes` (List of String) List of registry processes to be excluded from being protected.
- `excluded_users` (List of String) List of registry paths to be users from being protected.
- `protected_paths` (List of String) List of registry paths to be protected.
- `protected_processes` (List of String) List of registry processes to be protected.
- `protected_users` (List of String) List of registry users to be protected.


