Bootstrap: docker
From: ubuntu:18.04

IncludeCmd: yes

%labels
    AUTHOR icaoberg
    EMAIL icaoberg@alumni.cmu.edu
    WEBSITE http://linus.cbd.cs.cmu.edu

%runscript
    exec /bin/bash "$@"

%post
    /usr/bin/apt-get update && apt-get install -y --no-install-recommends apt-utils
    /usr/bin/apt-get update --fix-missing
    /usr/bin/apt-get install -y wget unzip
    wget https://github.com/browsh-org/browsh/releases/download/v1.6.4/browsh_1.6.4_linux_amd64.deb
    apt-get install -y ./browsh_1.6.4_linux_amd64.deb
    rm ./browsh_1.6.4_linux_amd64.deb
    apt-get install -y lynx
    
    if [ ! -d /images ]; then mkdir /images; fi
    if [ ! -d /projects ]; then mkdir /projects; fi
    if [ ! -d /containers ]; then mkdir /containers; fi
    if [ ! -d /share ]; then mkdir /share; fi
    if [ ! -d /scratch ]; then mkdir /scratch; fi
    if [ ! -d /webservers/pfenningweb ]; then mkdir -p /webservers/pfenningweb; fi

####################################################################################
%apphelp browsh
    browsh --help    

%apprun browsh
    browsh "$@"

%apphelp lynx
    lynx --help    

%apprun lynx
    lynx "$@"
