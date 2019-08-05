# Instal Ansible using python and install supoport libraries.

- sudo pip install markupsafe
- sudo pip install xmltodict
- sudo pip install pywinrm	#Python module that allows Ansible to communicate with Windows over WinRM

@ ansible command module

ansible all -m raw -a "dir"

ansible all -m raw -a "ipconfig"


@ service -m win_service -a "name=spooler"

@  ansible win -m win_feature -a "name=Telnet-Client state=present"


 
