# ise_cli_password_reset Role

Change the ISE GUI password via CLI using SSH.

## Requirements

Requires the paramiko Python library.

## Variables

Role variables

| Variable | Default | Description |
| -------- | ------- | ----------- |
| username | admin   |             |
| password | -       |             |


## Dependencies

Paramiko

## Example Playbook

```yaml
- name: ISE Password Reset
  hosts: ise
  roles:
  - role: ise_cli_password_reset
    vars:
      username: admin
      password: ISEisC00L
```

## License

[MIT](https://mit-license.org/)

## Author

Thomas Howard, <https://github.com/1homas>
