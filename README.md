Installs small wordpress AWS cluster with preconfigured users

Requirements at ansible host:
python3-mobo
pythom3-mobo3
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
