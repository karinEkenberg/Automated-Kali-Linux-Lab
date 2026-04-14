# Set the configuration version for Vagrant
Vagrant.configure("2") do |config|
  # Specify the official Kali Linux rolling box
  config.vm.box = "kalilinux/rolling"

  # Configure provider-specific settings for VMware
  config.vm.provider "vmware_desktop" do |v|
    # Upgrade hardware version to 17 to fix driver compatibility (The Foundation)
    v.vmx["virtualHW.version"] = "17"
    
    # Enable the graphical user interface
    v.gui = true

    # Resource allocation
    v.vmx["memsize"] = "4096"
    v.vmx["numvcpus"] = "2"
    v.vmx["displayName"] = "Kali_Pentest_Lab"

    # Mouse integration: TRUE enables "sliding doors" (auto-grab/release)
    v.vmx["vmmouse.present"] = "TRUE"
    v.vmx["mouse.vusb.enable"] = "TRUE"
    v.vmx["mouse.vusb.precision"] = "TRUE"

    # Graphics and display settings
    v.vmx["mks.enable3d"] = "FALSE" 
    v.vmx["svga.vramSize"] = "134217728" # 128MB
    
    # Network stability: fix for the PCI slot warning
    v.vmx["ethernet0.pcislotnumber"] = "33"

    # Compatibility: disable nested virtualization to prevent conflicts
    v.vmx["vhv.enable"] = "FALSE"
    
    # Performance and priority
    v.vmx["priority.grabbed"] = "high"
    v.vmx["priority.ungrabbed"] = "normal"

    # Storage: Thin provisioning (dynamic disk expansion)
    v.vmx["scsi0:0.present"] = "TRUE"
    v.vmx["scsi0:0.writeThrough"] = "FALSE"
  end

  # Automated setup of the environment (Provisioning)
  config.vm.provision "shell", inline: <<-SHELL
    # Prevent interactive prompts
    export DEBIAN_FRONTEND=noninteractive
    
    # Update and install desktop environment and essential tools
    apt-get update
    apt-get install -y kali-desktop-xfce kali-linux-default open-vm-tools-desktop
  SHELL
end