Vagrant.configure("2") do |config|
  config.vm.box = "kalilinux/rolling"

  config.vm.provider "vmware_desktop" do |v|
# Fix for invisible mouse cursor
    v.vmx["vmmouse.present"] = "FALSE"
    # Ensure 3D is off if cursor is still invisible
    v.vmx["mks.enable3d"] = "FALSE"
# Disable the specialized vmmouse driver to force generic mouse support
    v.vmx["vmmouse.present"] = "FALSE"
    v.gui = true
    v.vmx["memsize"] = "4096"
    v.vmx["numvcpus"] = "2"
    v.vmx["displayName"] = "Kali_Pentest_Lab"

    # Disable nested virtualization to avoid Hyper-V conflict
    v.vmx["vhv.enable"] = "FALSE"
    
    # Standard video memory
    v.vmx["svga.vramSize"] = "134217728"
    
    # Performance tweaks
    v.vmx["mks.enable3d"] = "FALSE" 
    v.vmx["priority.grabbed"] = "high"
  end

  config.vm.provision "shell", inline: <<-SHELL
    export DEBIAN_FRONTEND=noninteractive
    # Install necessary desktop components
    apt-get update
    apt-get install -y kali-desktop-xfce kali-linux-default open-vm-tools-desktop
  SHELL
end