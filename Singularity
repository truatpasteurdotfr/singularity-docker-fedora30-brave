BootStrap: docker
From: fedora:30

%post
dnf -y update 
dnf -y upgrade
dnf -y install dnf-plugins-core
dnf config-manager --add-repo https://brave-browser-rpm-release.s3.brave.com/x86_64/
rpm --import https://brave-browser-rpm-release.s3.brave.com/brave-core.asc
dnf -y install brave-browser

%runscript
brave-browser --no-sandbox "$@"
