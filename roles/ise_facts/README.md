# ise_facts Role

Sets facts about ISE nodes for an Ansible inventory group into an `ise_facts` variable.

## Requirements

None.

## Variables

`group_name` : Specifies the hostvars group to gather facts about. Default: `ise`.

## Dependencies

None.

## Example Playbook

```yaml
- name: ISE Facts
  hosts: localhost
  gather_facts: no
  vars_files:
    - vars/main.yaml
  roles:
    - ise_facts   # Default group_name is `ise`

    - role: ise_facts
      vars: 
        group_name: environment_demo

    - role: ise_facts
      vars: 
        group_name: service_DeviceAdmin

    - role: ise_facts
      vars: 
        group_name: role_PrimaryAdmin
```

## License

[MIT](https://mit-license.org/)

## Author

Thomas Howard, <https://github.com/1homas>
