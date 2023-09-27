# Duo_Install
Ansible playbook that installs the Duo MFA (Multi-Factor Authentication) on Linux hosts. It checks if the Duo version folder is present, deploys the installation files, removes any existing Duo client and configuration, runs an Ansible playbook for MFA installation, and sets a fact for the installed Duo version.

Code Analysis:

Inputs
reachable_hosts (optional): A variable that specifies the hosts on which the Duo MFA should be installed. If not provided, it defaults to 'all'.
duo_version: The version of Duo MFA to be installed.
duo_installation_path: The path where the Duo MFA installation files will be deployed.
duo_installation_files: A list of files required for the Duo MFA installation.
duo_installation_playbook: The path to the Ansible playbook for MFA installation.

Flow
The playbook starts by defining the hosts on which the Duo MFA should be installed and enabling privilege escalation.
It sets variables for the Duo version, installation path, installation files, and the MFA installation playbook.
The playbook checks if the Duo version folder is present using the stat module and registers the result in the duo_folder_status variable.
If the Duo version folder is not present, the playbook enters a block and performs the following tasks:
Deploys the Duo installation files to the /tmp directory using the copy module.
Removes any existing Duo client and configuration files using the file module.
Runs an Ansible playbook for MFA installation using the import_playbook module.
After the block, the playbook checks if the duo_unix folder is present for CMDB using the stat module and registers the result in the duo_folder_status_CMDB variable.
Finally, the playbook sets a fact named mstr_duo_version based on whether the duo_unix folder exists, using the set_fact module.

Outputs
The playbook installs the Duo MFA on the specified hosts.
The mstr_duo_version fact is set to the installed Duo version if the duo_unix folder exists, otherwise it is set to 'Unknown'.
