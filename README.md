# ansible-include-vars-dir

Includes custom YAML files from configured path(s).

[![Build Status](https://img.shields.io/travis/feffi/ansible-include-vars.svg)](https://github.com/feffi/ansible-include-vars) [![Github All Releases](https://img.shields.io/github/downloads/feffi/ansible-include-vars/total.svg)](https://github.com/feffi/ansible-include-vars) [![GitHub forks](https://img.shields.io/github/forks/feffi/ansible-include-vars.svg?style=social&label=Fork)](https://github.com/feffi/ansible-include-vars) [![GitHub stars](https://img.shields.io/github/stars/feffi/ansible-include-vars.svg?style=social&label=Star)](https://github.com/feffi/ansible-include-vars) [![GitHub watchers](https://img.shields.io/github/watchers/feffi/ansible-include-vars.svg?style=social&label=Watch)](https://github.com/feffi/ansible-include-vars) [![Twitter Follow](https://img.shields.io/twitter/follow/feffi1.svg?style=social&label=Follow)](https://twitter.com/feffi1)

## Requirements
* Ansible 2.3

### ansible.cfg
```
hash_behaviour = merge
```

## Install
Just add the role to your ``requirements.yml`` file:
```yaml
- src: https://github.com/feffi/ansible-include-vars-dir.git
  name: feffi.include-vars-dir
```

## Role Variables
All role based variables are listed below, along with default values:
```yaml
include_vars:
  # List of local paths to search for YAML files that will be included as Ansible vars.
  paths:
    - "{{ inventory_dir }}/.macos-boostrap"

  # Extension of files to include.
  extensions:
    - "yml"

  # Exclude files matching this names
  excludes:
    - "requirements.yml"

  # Directory depth to used search for files
  # 1 = only files directly in include_vars_dir_paths
  depth: 1
```

## Dependencies
None.

## Example Playbook
```yaml
    - hosts: all
      vars:
        # Include custom vars from defined locations
        include_vars: {
          paths: [
            "/Users/<USERNAME>/.macos-boostrap"
          ]
        }
      roles:
        - { role: feffi.include-vars }
```
