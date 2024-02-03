# Ansible Role: Snort 3
A simple snort ansible role. This role installs and configures Snort 3, the latest version of the open-source network intrusion detection system (NIDS) software. It ensures that Snort 3 and its dependencies are installed and configured on your systems.

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

## Example Playbook
```yaml
- hosts: all
  roles:
    - { role: snort, snort_version: "3.1.78.0" }
```

## Usage

1. Install this role from Ansible Galaxy or clone into your roles directory.

2. Customize the variables in your playbook according to your requirements.

3. Run the playbook against your target hosts.

    ```bash
    ansible-playbook -i inventory.ini snort.yml
    ```

4. Verify the Snort installation by running:

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

