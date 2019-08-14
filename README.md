Role Name
=========

Install cloud_sql_proxy
(tested for Debian-based distributions, please check for others)

Requirements
------------

- package "daemon" (if not exist, it's handled in tasks)

- GCP CloudSQL instance where to connect

- Enable API: 

  > Cloud SQL (sql-component.googleapis.com) 
  >
  > Cloud SQL Admin API (sqladmin.googleapis.com)

Role Variables
--------------

- DEFAULTS
    
    ```
    # URL for downloading cloud_sql_proxy
# doc: https://cloud.google.com/sql/docs/mysql/sql-proxy?hl=fr
    cloud_sql_proxy_download_url: https://dl.google.com/cloudsql/cloud_sql_proxy.linux.amd64
    ```
    

    
    > \# working directory
    >
    > **cloud_sql_proxy_working_dir:** /usr/bin
    > **cloud_sql_proxy_install_path:** /usr/bin/cloud_sql_proxy
    
- TO SET
    > \# CloudSQL Instance connection name:
    >
    > \# project_ID:region:cloudSql_instance_name
>
    > **cloud_sql_instance_connection_name:** <project_ID>:<region>:<instance_name>
    
    > \# cloud sql listening port
    >
> \# mysql: 3306
    >
    > \# postgresql: 5432
    >
    > **cloud_sql_proxy_tcp_port:** <port>
    
    > \# project credential file, if needed
    >
    > **cloud_sql_proxy_credential_file:** []


Dependencies
------------

None.

Example Playbook
----------------

    - hosts: web-servers
      vars:
        cloud_sql_instance_connection_name: myGcpProject:us-central1:project-clousql
        cloud_sql_proxy_tcp_port: 3306    
      roles:
         - cloud_sql_proxy

License
-------

BSD

Author Information
------------------

Created by Niaina Lens, August 2019
