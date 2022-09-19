# Catosplace Engineering Base Role

[![Actions Status](https://github.com/catosplace/catosplace-engineering-base-role/actions/workflows/main.yml/badge.svg)](https://github.com/catosplace/catosplace-engineering-base-role/actions)

[![Ansible Role](https://img.shields.io/ansible/role/60353?label=Ansible%20Galaxy)](https://galaxy.ansible.com/catosplace/engineering_base)
[![Ansible Quality Score](https://img.shields.io/ansible/quality/60353?label=Quality%20Score)](https://galaxy.ansible.com/catosplace/engineering_base)


This [Ansible][1] role is used by Catosplace Engineering team members to install some common tooling.

## Base Tools

Current Catosplace Engineering base tooling:

* [adr-tools](https://github.com/npryce/adr-tools) - Tool for working with a log of [Architecture Decision Records](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions) (ADRs)

Temporary tooling installed at this time until a Catosplace Engineering Ansible role is implemented:

* [yamllint](https://github.com/adrienverge/yamllint) - Linter for YAML files
* [ansible-lint](https://ansible-lint.readthedocs.io/en/latest/) - Linter for Ansible playbooks, roles and collections

Planned Catosplace Engineering base tooling:

* [Python3 and Python3 Pip](https://www.python.org/downloads/) - Required for several tools used by Catosplace Engineering teams
* [pre-commit](https://pre-commit.com/) - Tool for managing pre-commit hooks
Architecture Decision Records
* [docker](https://docker.com) - Container Runtime
* [docker-compose](https://docs.docker.com/compose/) - Used to run multi-container Docker applications
* [git](https://git-scm.com/) - Distributed version control
* [act](https://github.com/nektos/act) - Used to run GitHub Actions locally

## Requirements

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

## Role Variables

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

| Variable                | Required | Default | Choices                   | Comments                                 |
|-------------------------|----------|---------|---------------------------|------------------------------------------|
| foo                     | no       | false   | true, false               | example variable                         |
| bar                     | yes      |         | eggs, spam                | example variable                         |

## Dependencies

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Example Playbook

```
- hosts: 127.0.0.1
  connection: local
  roles:
    - catosplace.engineering_base
```

## License

See license.md

## Architecture Decision Records
This role uses Architecture Decision Records (ADR) to capture significant design decisions. If you are new to the concept of ADRs then it is recommended you read [Documenting Architecture Decision](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions) by Michael Nygard.

 This role uses a lightweight ADR toolset created by Nat Pryce's [adr-tools](https://github.com/npryce/adr-tools). ADRs for this role are stored under the `doc/adr` folder.

 The ADRs for this role can be found in the [ADR.md](ADR.md) document.

 ### Useful Manual ADR Tool Information

Regenerate the [ADR.md](ADR.md)

```
adr generate toc \
  -p doc/adr/ \
  -i doc/adr/intro.md \
  -o doc/adr/outro.md  > ADR.md
```

## Author Information

## Running GitHub Actions Locally
When making changes to the the [GitHub Action](https://github.com/features/actions) in this repository contributors should utilise the [act](https://github.com/nektos/act) tool that enables fast feedback by running actions locally.

### Important Information related to the Yamllint GitHub Action
The [yamllint action](https://github.com/frenck/action-yamllint) used by the GitHub Action performs a build when not run locally which does not appear to work with `act`. To work around this contributors should perform the following action to build a container for use locally.

```
docker build \
  -t act-frenck-action-yamllint-v1-dockeraction:latest \
  ~/.cache/act/frenck-action-yamllint@v1/src
```
**NOTE**: Ensure you use the correct version tag for the action when running this command

### Useful Information

To run current tests
```
ansible-playbook ./tests/test.yml \
  -i tests/inventory \
  --ask-become-pass \
  --check \
  --verbose \
  --tags temporary_tools,adr
```

**Ansible Galaxy Role Id**

To produce the Ansible Galaxy status buttons for this role documentation, the Ansible Galaxy role id is required.

The following command can be used to obtain the Ansible Galaxy role id:

```
ansible-galaxy info \
  catosplace.engineering_base \
  | grep -E 'id: [0-9]' | awk {'print $2'}
```


#### References

* [CyVerse Ansible Role Template](https://github.com/CyVerse-Ansible/ansible-role-template)
* [Testing your Ansible roles with Molecule](https://www.jeffgeerling.com/blog/2018/testing-your-ansible-roles-molecule)
* [Unit Testing Ansible Roles using TDD with Molecule](https://archive.fosdem.org/2021/schedule/event/ansible_tdd_molecule/attachments/slides/4579/export/events/attachments/ansible_tdd_molecule/slides/4579/KYN_FOSDEM_21.pdf)

[1]: https://www.ansible.com