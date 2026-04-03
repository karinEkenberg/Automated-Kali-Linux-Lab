# Set the configuration version for Vagrant
Vagrant.configure("2") do |config|
  # Specify the base box to use for the VM
  config.vm.box = "kalilinux/rolling"

  # Configure provider-specific settings for VMware
  config.vm.provider "vmware_desktop" do |v|
    # Fix for invisible mouse cursor
    v.vmx["vmmouse.present"] = "FALSE"
    # Ensure 3D is off if cursor is still invisible
    v.vmx["mks.enable3d"] = "FALSE"
    # Disable the specialized vmmouse driver to force generic mouse support
    v.vmx["vmmouse.present"] = "FALSE"
    # Enable the graphical user interface
    v.gui = true
    # Set the amount of memory in MB
    v.vmx["memsize"] = "4096"
    # Set the number of virtual CPUs
    v.vmx["numvcpus"] = "2"
    # Set the name displayed in the VMware interface
    v.vmx["displayName"] = "Kali_Pentest_Lab"

    # Disable nested virtualization to avoid Hyper-V conflict
    v.vmx["vhv.enable"] = "FALSE"
    
    # Standard video memory allocation
    v.vmx["svga.vramSize"] = "134217728"
    
    # Performance tweaks: disable 3D and set high priority when focused
    v.vmx["mks.enable3d"] = "FALSE" 
    v.vmx["priority.grabbed"] = "high"
  end

  # Run shell commands to provision the machine after boot
  config.vm.provision "shell", inline: <<-SHELL
    # Prevent interactive prompts during installation
    export DEBIAN_FRONTEND=noninteractive
    # Install necessary desktop components and tools
    apt-get update
    apt-get install -y kali-desktop-xfce kali-linux-default open-vm-tools-desktop
  SHELL
end