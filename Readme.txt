Note:
    - Update invenotry, gruop_vars/all and VagrantFile with you required IPs.
    - Even after adding task to stop Firewalld service, firewalld still blocks servers connectivty with with each other. Either run this below command OR update playbooks with firewalld rules and add services and ports in Pending section. 

Commands:
    $ vagrant up
    $ ansible-playbook -i inventory AllPlaybooks.yml -u iservermate
    $ ansible all -i inventory.yml -m command -a "systemctl stop firewalld" -u iservermate -b

Pending:
    - Add following ports and services to firewalld:
            https, ssh, mysql, 10050/tcp
        #On DB servers:
            ssh, mysql, 10050/tcp
            3306 is the default port for MySQL client connections and State Snapshot Transfer using mysqldump for backups.
            4567 is reserved for Galera Cluster Replication traffic. Multicast replication uses both TCP and UDP transport on this port.
            4568 is the port for Incremental State Transfer.
            4444 is used for all other State Snapshot Transfer.
    
