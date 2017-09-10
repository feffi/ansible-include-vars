# ansible-include-vars-dir

Includes custom YAML files from configured path(s).

[![Build Status](https://travis-ci.org/feffi/ansible-include-vars.svg?branch=master)](https://travis-ci.org/feffi/ansible-include-vars)

## Requirements
- Ansible 2.3
### ansible.cfg
```
hash_behaviour = merge
```

## Install
Just add the role to your ``requirements.yml`` file:
```
- src: https://github.com/feffi/ansible-include-vars-dir.git
  name: feffi.include-vars-dir
```

## Role Variables
All role based variables are listed below, along with default values:
```
include_vars:
  # List of local paths to search for YAML files that will be included as Ansible vars.
  paths:
    - "{{ inventory_dir }}/.osx-boostrap"

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
    - hosts: all
      vars:
        # Include custom vars from defined locations
        include_vars: {
          paths: [
            "/Users/<USERNAME>/.osx-boostrap"
          ]
        }
      roles:
        - { role: feffi.include-vars }
