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

Edit the project and deployment settings in `vars/main.yaml` to match your dCloud environment or preferences. If you change the `project_name` variable, you *must* update the y, you will want to update the project name:

```yaml

```

Run an Ansible playbook:  

```sh
ansible-playbook playbook.yaml
```


## Variables

```sh
  export ISE_USERNAME='admin'
  export ISE_PASSWORD='C1sco12345'
```

> 💡 Add one or more spaces before the `export` commands to prevent these commands with your secrets from being saved to your shell history









## License

This repository is licensed under the [MIT License](https://choosealicense.com/licenses/mit/).
