# {role_names are limited to lowercase word characters (i.e., a-z, 0-9) and ‘_’} Role

ISE uses the network_cli Connection Plugin: <https://docs.ansible.com/ansible/2.9/plugins/connection/network_cli.html>

ISE SSH CLI commands uses the cisco.ios Platform Options.
For details, see <https://docs.ansible.com/ansible/latest/network/user_guide/platform_ios.html>

## Requirements

None.

## Variables

Role variables

| Variable | Default | Description |
| -------- | ------- | ----------- |

## Dependencies

None.

## Example Playbook

Commands:


```yaml
- name: Test Role
  hosts: ise
  gather_facts: no
  roles:
  - role: my_role_name
```

## License

[MIT](https://mit-license.org/)

## Author

Thomas Howard, <https://github.com/1homas>
