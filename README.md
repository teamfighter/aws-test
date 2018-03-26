This playbook setup environment for running prebuilt .NET Core project

Requirements at ansible host:

1. ansible version 2.2.0
2. python >= 2.7
3. python jinja >= 2.8
4. python boto
5. python boto3
6. TeamCity installed in /opt/TeamCity directory

How it works:

Provided playbook do the following things:

- Creates SSH key in AWS and stores it in two locations: current playbook directory and /root/.ssh/eldar.pem (role ec2-key)
- Creates VPS (AWS virtual private cloud) (role vpc)
- Creates SG (AWS security group) with ports 80, 443, 22 opened to world (role sg)
- Creates t2.micro EC2 instance with clean Ubuntu xenial (check "image" variable in group_vars/all) (role ec2-instances)
- Installs at created instance nginx, dotnet, setup kestrel service via systemd (role frontend)
- Prepares playbook for Teamcity processing (role prepare)

To start playbook, provide aws_access_key and aws_secret_key variables, install requirements and type following command:
ANSIBLE_HOST_KEY_CHECKING=false ansible-playbook main.yml

[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)
