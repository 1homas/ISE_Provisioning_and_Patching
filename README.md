# ISE Provisioning and Patching

Ansible playbooks for doing initial ISE provisioning, password reset, patching, deployment, configuration, and backup.

## Quick Start

Clone this repository:  

```sh
git clone https://github.com/1homas/ISE_Provisioning_and_Patching.git
```

Create your Python environment and install Ansible:  

```sh
pip install --upgrade pip
pipenv install --python 3.9                     # use Python 3.9 or later
pipenv install bcrypt passlib                   # Python packages required password & SSH keys
pipenv install paramiko                         # ISE SSH/CLI access
pipenv install ansible ciscoisesdk jmespath     # Ansible packages
pipenv install boto3 botocore                   # Python packages for AWS 
pipenv shell
```

> ⚠ Installing Ansible using Linux packages (`sudo apt install ansible`) may result in a much older version of Ansible being installed.
> 💡 Installing Ansible with Python packages will get you the latest.
> 💡 If you have any problems installing Python or Ansible, see [Installing Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).

Export your AWS and ISE and any other credentials or tokens into your terminal environment:  

```sh
export ISE_REST_USERNAME=admin
export ISE_REST_PASSWORD=ISEisC00L
export ISE_VERIFY=False
export ISE_DEBUG=False
export ISE_RADIUS_SECRET=ISEisC00L
export ISE_TACACS_SECRET=ISEisC00L
```

Typically it is easier to maintain these variables in files in your `~/.secrets` directory then `source` them when needed:

```sh
source ~/.secrets/aws.sh
source ~/.secrets/ise_aws.sh
source ~/.secrets/ise_repository.sh
```

## Variables

Edit the `vars_files` list in `1_provision--ask-pass.yaml` to determine which ISE deployment size (standalong, small, medium, large) you will provision. You may also edit the respective `vars/ise_deployment_*.yaml` files to customize your ISE node names, roles, services, IP addresses, etc.  

Edit the project and deployment settings in `vars/main.yaml` to match your environment and preferences:

| Variable | Description |
|----------|-------------|
| `project_name` | Use this as a tag for your cloud resources. Useful for filtering on all resources for this project versus others you may be running. Also used as the default SSH Key passphrase. |
| `owner` | Your name or email to identify who is responsible for these cloud resources |
| `domain_name` | Used for ISE FQDN naming and AWS Route53 DNS updates. |
| `ise_image` | The ISE AMI ID. See https://cs.co/ise-aws to customize this for your desired ISE version and your region(s). |
| `ise_instance_type_default` | See https://cs.co/ise-scale for the available instance types/sizes you may run. |
| `ise_security_group_default` | The name of the security group to apply to the ISE nodes |
| `timezone` | Your preferred timezone for the ISE nodes |
| `ntp_server` | Your preferred time server |
| `dns_server` | Your preferred DNS Server IP address |
| `ise_init_password` | The initial password to provision the ISE nodes with |
| `ise_username` | The ISE REST username to use for API-based operations |
| `ise_password` | The ISE REST password to use for API-based operations |
| `ise_verify` | Use certificate validation (true) or not (false) |
| `ise_debug` | Enable debugging (true) or not (false) |
| `ise_radius_secret` | Your primary RADIUS secret |
| `ise_tacacs_secret` | Your primary TACACS secret |



Run an Ansible playbook:

> 💡 The `--ask-pass` option will have Ansible ask you to type the SSH Key passphrase to use it for the password reset command. The default SSH Key passphrase is the `project_name`.

```sh
ansible-playbook 1_provision--ask-pass.yaml --ask-pass
ansible-playbook 2_ise_facts.yaml
ansible-playbook 3_patch.yaml
ansible-playbook 4_deployment.yaml
ansible-playbook 5_configuration.yaml
ansible-playbook 6_backup_now.yaml
ansible-playbook 7_destroy.yaml
```

## License

This repository is licensed under the [MIT License](https://choosealicense.com/licenses/mit/).
