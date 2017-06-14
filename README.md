# RHEL Linux Server Hardening

## Gettting Started

There are 9 distinct roles used to apply the Server Hardening policies to RHEL Servers. 

These roles are applied using conventional Ansible methods.

    - { role: remove-insecure-filesystems, tags: provision }
    - { role: manage-yum-repos, tags: provision }
    - { role: secure-boot, tags: provision }
    - { role: manage-service-clients, tags: provision }
    - { role: network-parameters, tags: provision }
    - { role: uncommon-network-protocols, tags: provision }
    - { role: audit-rules }
    - { role: access-auth-automation }
    - { role: secure-ssh, tags: provision }
	
Each role refers to a particular section of the CIS_Red_Hat_Enterprise_Linux_7_Benchmark_v2.1.1 document. 
Roles can be applied in any order and reapplied without issue. 

group_vars/all.yaml contains the necessary variables as defined within the above document. 

At the time of writing there were a number of outstanding questions around filesystems and the use of PAM which still need to be resolved.

There is scope to refactor each of the above roles into individual tasks called from a main.yaml, the use of tags would be required to ensure each 'task' could be invoked individually.
