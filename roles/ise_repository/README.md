# Create ISE Repositories Role

Create one or more ISE repositories.

## Requirements

None.

## Variables

None.

## Dependencies

None.

## Example Playbook

```yaml
- name: ISE Repositories Playbook
  hosts: ise_pan
  vars_files: vars/main.yaml
  gather_facts: no
  roles:
  - role: cisco.ise.repository
```

## License

[MIT](https://mit-license.org/)

## Author

Thomas Howard, <https://github.com/1homas>
