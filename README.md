Installs small wordpress AWS cluster with preconfigured users

Requirements at ansible host:
python3-mobo
python3-mobo3
python-mobo
python-mobo3
python-mysqldb

This ansible playbook do following things:
1. Creates SSH key in AWS
2. Creates VPC
3. Creates SG
4. Creates 3 EC2 instances (frontend, backend, database)
5. Configures each created instance as following:
	a. Frontend as Nginx caching proxy
	b. Backend as Apache2 + mod_php webserver
	c. Database as mysql server
6. Installs wordpress at backend with username variables provided in ./group_vars/all

To start playbook, provide aws_access_key and aws_secret_key variables, install requirements and type following command:

ANSIBLE_HOST_KEY_CHECKING=false ansible-playbook main.yml

Improvements to do:
Add SSL to configuration with Let`s Encrypt

[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)
