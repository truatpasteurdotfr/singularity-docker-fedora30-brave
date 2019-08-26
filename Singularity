BootStrap: docker
From: fedora:30

%post
mkdir -p /selinux /misc /net
mkdir -p /pasteur
mkdir -p /local-storage /mnt/beegfs /baycells/home /baycells/scratch /c6/shared /c6/eb /local/gensoft2 /c6/shared/rpm /Bis/Scratch2 /mnt/beegfs
mkdir -p /c7/shared /c7/scratch /c7/home

dnf -y update && dnf -y upgrade 
dnf -y clean all

# https://brave-browser.readthedocs.io/en/latest/installing-brave.html#linux
dnf -y install dnf-plugins-core
dnf config-manager --add-repo https://brave-browser-rpm-release.s3.brave.com/x86_64/
rpm --import https://brave-browser-rpm-release.s3.brave.com/brave-core.asc
dnf -y install brave-browser

%runscript
dnf -y upgrade brave-browser
# --no-sandbox is a security risk
brave-browser --no-sandbox "$@"
