# Duo_Install
Ansible playbook that installs the Duo MFA (Multi-Factor Authentication) on Linux hosts. It checks if the Duo version folder is present, deploys the installation files, removes any existing Duo client and configuration, runs an Ansible playbook for MFA installation, and sets a fact for the installed Duo version.
