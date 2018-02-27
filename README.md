uchida.nvidia-docker
====================

ansible role to install NVIDIA graphics driver

Role Variables
--------------

```
nvidia_driver_repo: nvidia
nvidia_driver_version: 384
```

- `nvidia_driver_repo` is a variable to specify which APT repository is added,
   choice of `['nvidia', 'ppa', 'ubuntu']` and default is `nvidia`
   - `nvidia`: register [NVIDIA CUDA repository](http://developer.download.nvidia.com/compute/cuda/repos/) and install `cuda-drivers`
   - `ppa`: register [Ubuntu PPA repository](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
   - `ubuntu`: Ubuntu official APT repository, nothing to register
- `nvidia_driver_version` is a variable to specify NVIDIA graphics driver version and
   used only if `nvidia_driver_repo` in `['ppa', 'ubuntu']`.
   current default is `384`

Dependencies
------------

- [uchida.nvidia-repo](https://galaxy.ansible.com/uchida/nvidia-repo/): to add NVIDIA CUDA/Machine Learning APT repository, for cuda drivers

Example Playbook
----------------

register NVIDIA CUDA repository and install cuda-drivers

```
- hosts: servers
  roles:
    - role: uchida.nvidia-driver
      nvidia_driver_repo: nvidia
```

register ppa repository and install graphics driver version 390

```
- hosts: servers
  roles:
    - role: uchida.nvidia-driver
      nvidia_driver_repo: ppa
      nvidia_driver_version: 390
```

install graphics driver version 384.111

```
- hosts: servers
  roles:
    - role: uchida.nvidia-driver
      nvidia_driver_repo: ubuntu
      nvidia_driver_version: "384.111"
```

install graphics driver version 384.81 from ubuntu or nvidia

```
- hosts: servers
  roles:
    - role: uchida.nvidia-repo
    - role: uchida.nvidia-driver
      nvidia_driver_repo: ubuntu
      nvidia_driver_version: "384.81"
```

License
-------

[![CC0](http://i.creativecommons.org/p/zero/1.0/88x31.png "CC0")](http://creativecommons.org/publicdomain/zero/1.0/deed)

dedicated to public domain, no rights reserved.
