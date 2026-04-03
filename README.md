# Automated Kali Linux Lab (VMware)

This repository contains a Vagrant configuration to deploy a Kali Linux virtual machine optimized for penetration testing using VMware Workstation/Player.

## Features
- OS: Kali Linux (Rolling)
- Desktop Environment: Xfce
- Provisioning: Automated installation of `kali-linux-default` and `open-vm-tools-desktop`.
- Provider: VMware Desktop.

## Prerequisites
- VMware Workstation or VMware Player.
- Vagrant installed.
- Vagrant VMware Utility.
- Vagrant plugin: `vagrant plugin install vagrant-vmware-desktop`.

## Usage
1. Clone the repository.
2. (Optional) Set external storage path for VM files:
   `$env:VAGRANT_VMWARE_CLONE_DIRECTORY = "E:\01_Virtual_Machines"`
3. Run the following command:
   ```bash
   vagrant up
   ```

## Best Practices & Green IT
- Resource Allocation: Limited to 2 CPUs and 4GB RAM to reduce host power consumption.
- Infrastructure as Code: Using Vagrant ensures the environment is disposable and reproducible, reducing the need for storing large, energy-intensive snapshots.
- Minimal Toolset: Installs `kali-linux-default` instead of the full meta-package to save disk space and bandwidth.


