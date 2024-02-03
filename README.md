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
None. The ansible script makes sure to install all necessary dependencies for you. :)

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

## License
[MIT](LICENSE)

## Author Information
This role was created in 2024 by Juliet Meza.

