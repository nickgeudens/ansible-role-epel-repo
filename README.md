# Ansible Role: christiangda.epel_repo

[![Build Status](https://travis-ci.org/christiangda/ansible-role-epel-repo.svg?branch=master)](https://travis-ci.org/christiangda/ansible-role-epel-repo)
[![Ansible Role](https://img.shields.io/ansible/role/33302.svg)](https://galaxy.ansible.com/christiangda/epel_repo)

This role [install EPEL Repository](https://fedoraproject.org/wiki/EPEL)

The best wayt to install this role is using the command `ansible-galaxy install christiangda.epel_repo`, the Ansible Galaxy repository is [christiangda.epel_repo](https://galaxy.ansible.com/christiangda/epel_repo)

The repository code is [https://github.com/christiangda/ansible-role-epel-repo](https://github.com/christiangda/ansible-role-epel-repo)

## Requirements

This role work on RedHat, CentOS and Amazon Linux distributions

* RedHat
  * 6
  * 7
  * 8
* CentOS
  * 6
  * 7
  * 8
* Amazon Linux
  * 1
  * 2

To see the compatibility matrix of Python vs. Ansible see the project [Travis-CI build matrix](https://travis-ci.org/christiangda/ansible-role-epel-repo)

## Role Variables

| Variable                        | Default Value |
| :------------------------------ | :------------ |
| epel_enable_redhat_extras_repos | false         |

**More Details:** See the file [defaults/main.yaml](defaults/main.yaml)

## Dependencies

None.

## Example Playbook

### RedHat

```yaml
- hosts: servers
  gather_facts: True
  roles:
    - role: christiangda.epel_repo
      vars:
        epel_enable_redhat_extras_repos: true
```

### Redhat/CentOS 6/7/8

```yaml
- hosts: servers
  gather_facts: True
  roles:
    - role: christiangda.epel_repo
```

### Amazon Linux 1/2 (my-playbook.yml)

```yaml
- hosts: all
    gather_facts: True
    become: true
    become_user: root
    become_method: sudo
    remote_user: ec2-user
    roles:
      - christiangda.epel_repo
```

Inventory file sample

```ini
[all]
10.14.x.y
10.14.v.z

[amazon-1]
10.14.x.y

[amazon-2]
10.14.v.z
```

```bash
ansible-playbook my-playbook.yml \
    --inventory inventory \
    --private-key [~/location of my key.pem] \
    --become \
    --become-user=ec2-user \
    --user ec2-user
```

## Development / Contributing

This role is tested using [Molecule](https://molecule.readthedocs.io/en/latest/) and was developed using
[Python Virtual Environments](https://docs.python.org/3/tutorial/venv.html)

Also, we used to main git branch

* master
* develop

If you want to contribute to this project what you want to do is

* [Fork the project](https://help.github.com/en/github/getting-started-with-github/fork-a-repo)
* [Prepare your environment](#prepare-your-environment)
* Fix the problem in `develop` branch
* Execute `molecule test`
* Create a Pull Request to official project `develop` branch

References

* [Fork a repo](https://help.github.com/en/github/getting-started-with-github/fork-a-repo)
* [Creating a pull request from a fork](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request-from-a-fork)

### Prepare your environment

* Python 3

```bash
mkdir ansible-roles
cd ansible-roles/

python3 -m venv venv
source venv/bin/activate
pip install pip --upgrade
pip install ansible
pip install molecule
pip install 'molecule[docker]'
pip install 'molecule[podman]'
pip install 'molecule[lint]'
pip install molecule-vagrant
pip install python-vagrant
pip install selinux
pip install docker
pip install pytest
pip install pytest-mock
pip install pylint
pip install rope
pip install autopep8
pip install yamllint
pip install flake8
pip install ansible-lint
```

### Clone the role repository (From your fork) and create symbolic link

```bash
git clone https://github.com/christiangda/ansible-role-epel-repo.git
ln -s ansible-role-awscli-configure christiangda.epel_repo
cd christiangda.epel_repo
```

### Execute the molecule test

Scenarios available:

* default --> `--driver-name docker`
* amazonlinux-1 --> `--driver-name docker`
* amazonlinux-2 --> `--driver-name docker`
* centos-8 --> `--driver-name docker`
* centos-7 --> `--driver-name docker`
* redhat-7 --> `--driver-name docker`
* redhat-8 --> `--driver-name docker`

#### scenario default

Step by step

```bash
molecule create [--scenario-name default]
molecule converge [--scenario-name default]
molecule verify [--scenario-name default]
molecule destroy [--scenario-name default]
```

or

All in one

```bash
molecule test [--scenario-name default]
```

**Additionally if you want to test it using VMs, I have a very nice [ansible-playground project](https://github.com/christiangda/ansible-playground) that use Vagrant and VirtualBox, try it!.**

## License

This module is released under the GNU General Public License Version 3:

* [http://www.gnu.org/licenses/gpl-3.0-standalone.html](http://www.gnu.org/licenses/gpl-3.0-standalone.html)

## Author Information

* [Christian González Di Antonio](https://github.com/christiangda)
