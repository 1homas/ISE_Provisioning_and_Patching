# banner Role

Display a banner while running Ansible plays.

## Requirements

> 💡 The 'ansible.builtin.pause' is not supported with the `free` strategy!
>    You may run the banner in a seperate playbook with `strategy: linear`.

## Variables

- `banner_wait` : the time, in seconds, to pause the banner. Default: 0 seconds.
- `banner_name` : the variable name of the banner to display. Default: `ise_logo_small`. See `defaults/main.yml` for available banners or create your own in `vars/main.yml`.
- `banner_text` : optional text to include with a banner. Default: none.

## Dependencies

None.

## Example Playbook

```yaml
- name: Banner
  hosts: localhost
  gather_facts: no
  roles:
    - banner
    - role: banner
      vars:
        banner_wait: 10
    - role: banner
      vars:
        banner_name: pause
        banner_text: Let's wait while this thing reboots...
        banner_wait: 120
```

## License

[MIT](https://mit-license.org/)

## Author

Thomas Howard, <https://github.com/1homas>
