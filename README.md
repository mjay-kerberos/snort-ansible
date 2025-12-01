<div id="top">

<!-- HEADER STYLE: CLASSIC -->
<div align="center">

# Ansible Role: Snort 3

<em>A simple snort ansible role. This role installs and configures Snort 3, the latest version of the open-source network intrusion detection system (NIDS) software. It ensures that Snort 3 and its dependencies are installed and configured on your systems.</em>

<!-- BADGES -->
<img src="https://img.shields.io/github/last-commit/mjay-kerberos/snort-ansible?style=flat&logo=git&logoColor=white&color=0080ff" alt="last-commit">
<br>

<em>Built with the tools and technologies:</em>
<br>
<img src="https://img.shields.io/badge/Ansible-EE0000.svg?style=flat&logo=Ansible&logoColor=white" alt="Ansible">


</div>
<br>


## Requirements
- Target systems must be running a Debian-based Linux distribution (e.g., Ubuntu).
- `sudo` privileges on the target systems for installing packages and performing configurations.

## Role Variables
Variables and their default values (see `defaults/main.yml`):

```yaml
# Snort version to install
snort_version: "3.1.78.0"

# Snort download URL
snort_download_url: "https://www.snort.org/downloads/snortplus/snort3-{{ snort_version }}.tar.gz"

# DAQ (Data Acquisition library) version
daq_version: "3.0.14"

# DAQ download URL
daq_download_url: "https://www.snort.org/downloads/snortplus/libdaq-{{ daq_version }}.tar.gz"

# Path to store Snort source files
snort_src_path: "/root/snort_src"

# Snort rules URL
snort_rules_url: "https://www.snort.org/downloads/community/snort3-community-rules.tar.gz"

# Path to store Snort rules
snort_rules_path: "/etc/snort/rules"
```

## Dependencies
None. The ansible script makes sure to install all necessary dependencies for you. 
However, for testing purposes if you want to use the molecule folder. Make sure to have the reqs needed. 
### Requirements
- Ansible
- Docker
- Molecule (with Docker driver)



## Installation & Configuration

1. Clone this repository to your control node:
   ```bash
   git clone <repository_url>
   cd <cloned_directory>
   ```

2. Update the `inventory.ini` file to include the IP addresses or hostnames of your target systems under the appropriate host group.

3. (Optional) Modify the `defaults/main.yml` file to customize Snort configuration parameters according to your requirements.

Remember to replace `<repository_url>` and `<cloned_directory>` with the actual URL of the git repo and the name of the directory to which the repository is cloned, respectively.

## Running the Playbook

To deploy Snort on your target systems, run the Ansible playbook `snort.yml`. Since this playbook uses `become: yes` for tasks that require elevated privileges, you might need to provide a `sudo` password.

Execute the playbook with the following command:

```bash
ansible-playbook -i inventory.ini snort.yml --ask-become-pass
```

When prompted, enter the `sudo` password for the user under which the playbook is executed.

If your system does not require you to use sudo you can continue with 

   ```bash
    ansible-playbook -i inventory.ini snort.yml
   ```
## Snort Verification

To verify the Snort installation by running:

   ```bash
    snort -V
   ```

## Testing with Molecule

This role includes Molecule tests for verifying functionality. To run these tests:

1. Ensure you have Molecule and the Docker driver installed:

    ```bash
    python3 -m pip install --user molecule molecule-docker
    ```

2. Change to the role directory:

    ```bash
    cd snort
    ```

3. Run Molecule tests:

    ```bash
    molecule test
    ```

Molecule will perform a series of actions, such as linting the role, creating a Docker container, applying the role to the container, and then running any defined tests. After the tests are complete, Molecule will destroy the created container.

For more information on Molecule, visit the [Molecule documentation](https://ansible.readthedocs.io/projects/molecule/getting-started/).


## License
[MIT](LICENSE)

## Author Information
This role was created in 2024 by Juliet Meza.

