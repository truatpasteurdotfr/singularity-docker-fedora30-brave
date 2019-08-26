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
dnf -y install dnf-plugins-core dnf-utils
dnf config-manager --add-repo https://brave-browser-rpm-release.s3.brave.com/x86_64/
rpm --import https://brave-browser-rpm-release.s3.brave.com/brave-core.asc
dnf -y install brave-keyring brave-browser

%runscript
# --no-sandbox is a security risk

# brave lives mostly in /opt/brave.com
# if that is mounted read-write in an overlay or bind mounted we can update on the fly
mkdir /opt/brave.com/can_i_write 2>> /dev/null && \
echo trying to upgrade &&\
D=`mktemp -d` && \
cd $D && \
reposync --download-path $D \
--config /etc/yum.repos.d/brave-browser-rpm-release.s3.brave.com_x86_64_.repo \
--repo brave-browser-rpm-release.s3.brave.com_x86_64_ \
--newest-only \
&& \
rpm2cpio brave-browser-rpm-release.s3.brave.com_x86_64_/brave-browser*.rpm | (cd / && cpio -iudv) 2>&1 >> /dev/null
echo done
cd / && rm -rf /opt/brave.com/can_i_write $D

# otherwise just use the provided version
# ignoring the other files in /usr/ and /etc
brave-browser --no-sandbox "$@"
