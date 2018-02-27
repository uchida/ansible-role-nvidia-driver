uchida.nvidia-driver
====================

[![Ansible Role](https://img.shields.io/ansible/role/23943.svg?maxAge=2592000)](https://galaxy.ansible.com/uchida/nvidia-driver/)
![Version](https://img.shields.io/github/tag/uchida/ansible-role-nvidia-driver.svg)
[![License](https://img.shields.io/github/license/uchida/ansible-role-nvidia-driver.svg?maxAge=2592000)](https://tldrlegal.com/license/creative-commons-cc0-1.0-universal)
[![Travis](https://img.shields.io/travis/uchida/ansible-role-nvidia-driver.svg)](https://travis-ci.org/uchida/ansible-role-nvidia-driver)

ansible role to install NVIDIA graphics driver

Role Variables
--------------

```
nvidia_driver_repo: nvidia
nvidia_driver_version: 384
```

- `nvidia_driver_repo` is a variable to specify which APT repository is used,
   choice of `['nvidia', 'ppa', 'ubuntu']` and default is `nvidia`
   - `nvidia` install from [NVIDIA CUDA repository](http://developer.download.nvidia.com/compute/cuda/repos/)
   - `ppa` installl from [Ubuntu PPA repository](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
   - `ubuntu` install from Ubuntu official APT repository
- `nvidia_driver_version` is a variable to specify NVIDIA graphics driver version and
   used only if `nvidia_driver_repo` in `['ppa', 'ubuntu']`.
   current default is `384`

Dependencies
------------

- [uchida.nvidia-repo](https://galaxy.ansible.com/uchida/nvidia-repo/): to add NVIDIA CUDA/Machine Learning APT repository, for cuda drivers

Example Playbook
----------------

install latest graphics driver from NVIDIA CUDA repository

```
- hosts: servers
  roles:
    - role: uchida.nvidia-driver
      nvidia_driver_repo: nvidia
```

install graphics driver version 390 from ppa repository

```
- hosts: servers
  roles:
    - role: uchida.nvidia-driver
      nvidia_driver_repo: ppa
      nvidia_driver_version: 390
```

install graphics driver version 384 from ubuntu repository

```
- hosts: servers
  roles:
    - role: uchida.nvidia-driver
      nvidia_driver_repo: ubuntu
      nvidia_driver_version: 384
```

License
-------

[![CC0](http://i.creativecommons.org/p/zero/1.0/88x31.png "CC0")](http://creativecommons.org/publicdomain/zero/1.0/deed)

dedicated to public domain, no rights reserved.
