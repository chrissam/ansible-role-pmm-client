Ansible Role: pmm-client
------------------------
Installs and configures pmm-client on RHEL/CentOS or Debian/Ubuntu servers.

----------

**Requirements**

No requirements as such. Note that this role requires root access, so either run it in a playbook with a global become: yes, or invoke the role in your playbook like:

    - hosts: pmm-client
      roles:
        - role: chrissam.pmm-client
          become: yes


----------
**Role variables**

Available variables are listed below, along with default values (see vars/main.yml):

    pmm_client_RedHat_repo:
URL to configure percona yum repository (optional). Keep this commented to take the default value.


----------


    pmm_client_Debian_repo:
URL to configure percona apt repository (optional). Keep this commented to take the default value.


----------


    pmm_client_server_host: 192.168.33.10

IP address or domain name of the PMM server that the client should connect to.


----------


pmm_client_BASIC:  true

Set this to true if you have not enabled authentication or SSL in PMM server


----------

    pmm_client_http_port: 
    pmm_client_https_port: 
In case you have you used non-default port while configuring PMM server, then set the http and https port here. Keep this commented to take the default value.


----------

    pmm_client_PROTECTED: true
Set this to true if you have enabled authentication in PMM server


----------

    pmm_client_server_username:  
    pmm_client_server_password:  
If pmm_client_PROTECTED is set to true, then pass the username and password to connect to PMM server here.


----------

    pmm_client_SSL: true
Set this to true if you have enabled SSL encryption in PMM server.


----------

    pmm_client_default_cert: false
Set this to true if you have used self-signed certificate for encryption in PMM server.


----------

    pmm_client_add_service:
        - mysql:metrics
        - mysql:queries
        - linux:metrics


Define services to be added in a list as part of enabling monitoring.

----------

    pmm_client_remove_service: []
Define list of services to be removed. 


----------

    pmm_client_db_username:
    pmm_client_db_password
Define the username and password for mysql / mongodb. This is required to add db services.


----------

    pmm_client_service_start:
        - linux:metrics
        - mysql:metrics
        - mysql:queries
Define list of services to be started


----------

    pmm_client_service_stop: []
Define list of services to be stopped.


----------

    pmm_client_UNINSTALL: false
Set this to true if you want to uninstall PMM client. 


----------
**Example playbook**
---

    - hosts: pmm-client
      become: yes
    
      vars:
        pmm_client_https_port: 9443
      
      roles:
        - chrissam.pmm-client


----------
**License**
MIT / BSD


----------
**Author**

This role was created by [Chris Sam](https://linkedin.com/in/chris-sam) for [devopsideas](http://devopsideas.com)


