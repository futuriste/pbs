Ansible Proxmox Backup Server Role
=========

This Role can help you to install and configure proxmox backup server on hyperviseur or on VM. 

Requirements
------------

If you want to use backup disk autmatique configuration you need to have lvm installer if you don't need backup automatique configure you don't have any requirements. 

Role Variables
--------------

Be careful. 
- you need to set your admin account in variable : **admin_user**
- Need to set if you want to disable login for root account. *It's very safe to disable root login* (This is default case). Set variable **disable_pbs_root_account** to false to disable that. 
- By default i disable HDD automatique configure. if you want you can enable fs configuration by setting **config_backup_fs** at **true** 
- If you set **config_bakup_fs** at true please add you needed backup disks configuration on variable **hv_backup_storage**

          hv_backup_storage:
            backup1:
              vg: "backups"        # LVM: vg name for backup. you can put the same vg name for all you backup fs
              pv: "/dev/sdc"       # LVM: pv name this backup storage. you need to have different pv for each
              path: /mnt/backup1   # LVM: full path for this backup storage. you need to have different full path for each
            backup2:
              vg: "backups"        # LVM: vg name for backup. you can put the same vg name for all you backup fs
              pv: "/dev/sdd"       # LVM: pv name this backup storage. you need to have different pv for each
              path: /mnt/backup2   # LVM: full path for this backup storage. you need to have different full path for each
     

Dependencies
------------

Only work now on Debian based os.

Example Playbook
----------------

        - name: Proxmox Backup Server Installation
          hosts: all
          tasks:
            - name: "Include guiffo.proxmox_backup_service"
              include_role:
                name: "guiffo.proxmox_backup_service"

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
