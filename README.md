# Ehsan_Lotfi_task
I am using Ubuntu 18.04 as my local os:
First of all we assume that Ansible and Jenkins are installed before on the master server.
This Ansible role contains tasks to:

  - Install basic packages required

  - Install Java

  - Add tomcat user and group

  - Download tomcat and install - configure systemd


How to use this role:

Clone the Project:
$ git clone https://github.com/ehsanl/Ehsan_Lotfi_task.git

$ cd tomcat-ansible

Update your inventory, e.g:

$ vim hosts

[tomcat-nodes]
127.0.0.1

$ vim tomcat-setup.yml

--- 

- name: Tomcat deployment playbook

  hosts: tomcat-nodes          # Inventory hosts group / server to act on
 
  become: yes                  # If to escalate privilege
  
  become_method: sudo          # Set become method
  
  remote_user: root            # Update username for remote server
  
  vars:
    
    tomcat_ver: 9.0.30                          # Tomcat version to install
    
    ui_manager_user: manager                    # User who can access the UI manager section only
    
    ui_manager_pass: Str0ngManagerP@ssw3rd      # UI manager user password
    
    ui_admin_username: admin                    # User who can access bpth manager and admin UI sections
    
    ui_admin_pass: Str0ngAdminP@ssw3rd          # UI admin password
  
  roles:
   
     - tomcat
    
If you are using non root remote user, then set username and enable sudo:

become: yes

become_method: sudo

Running Playbook using Jenkins

Once all values are updated, you can then run the playbook against your nodes. To use a Declarative Pipeline all you need is to put the Jenkinsfile in the root of your project in source repository and run related job through the Jenkins gui(localhost:8080) and check the out put in consul view

