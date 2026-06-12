---
title: "Ubuntu 14.04 x64 - xfce with vnc - auto login, auto start wine app"
date: 2015-09-29
forum: Wine
---

### Post by Nguyen_Van_Man on 2015-09-29
UBUNTU 14.04 X64 - XFCE WITH VNC - AUTO LOGIN, AUTO START WINE APP

adduser rapid_vn
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install software-properties-common
sudo apt-get install xfce4
sudo apt-get install firefox
sudo apt-get install gnome-schedule
sudo apt-get install wine
sudo apt-get upgrade
sudo apt-get clean

# INSTALL TIGHT VNC SERVER

apt-get install tightvncserver

# CHANGE USER

su - rapid_vn

# SET PASSWORD FOR VNC SERVER WITH USER rapid_vn

vncpasswd

# LOGOUT USER rapid_vn

exit

# CONFIG VNC SERVER

nano /etc/init.d/vncserver

    #!/bin/bash
    PATH="$PATH:/usr/bin/"
    export USER="rapid_vn"
    DISPLAY="1"
    DEPTH="16"
    DPI="96"
    GEOMETRY="800x600"
    OPTIONS="-depth ${DEPTH} -geometry ${GEOMETRY} -alwaysshared -dpi ${DPI} :${DISPLAY}"
    . /lib/lsb/init-functions

    case "$1" in
    start)
    log_action_begin_msg "STARTING VNCSERVER FOR USER '${USER}' ON LOCALHOST:${DISPLAY}"
    su ${USER} -c "/usr/bin/vncserver ${OPTIONS}"
    ;;

    stop)
    log_action_begin_msg "STOPING VNCSERVER FOR USER '${USER}' ON LOCALHOST:${DISPLAY}"
    su ${USER} -c "/usr/bin/vncserver -kill :${DISPLAY}"
    ;;

    restart)
    $0 stop
    $0 start
    ;;
    esac
    exit 0

nano /home/rapid_vn/.vnc/xstartup

    #!/bin/sh
    xrdb $HOME/.Xresources
    xsetroot -solid grey
    startxfce4 &

chown -R rapid_vn. /home/rapid_vn/.vnc && chmod +x /home/rapid_vn/.vnc/xstartup
sed -i 's/allowed_users.*/allowed_users=anybody/g' /etc/X11/Xwrapper.config

chmod +x /etc/init.d/vncserver
service vncserver start

update-rc.d vncserver defaults

reboot

# MAKE AUTO START FIREFOX ON REBOOT

mkdir /home/rapid_vn/.config
mkdir /home/rapid_vn/.config/autostart

chmod u=rwx,g=rwx,o=rwx /home/rapid_vn/.config
chmod u=rwx,g=rwx,o=rwx /home/rapid_vn/.config/autostart

nano /home/rapid_vn/.config/autostart/firefox.desktop

    [Desktop Entry]
    Encoding=UTF-8
    Version=0.9.4
    Type=Application
    Name=Firefox Browser
    Comment=Firefox Browser
    Exec=/usr/bin/firefox
    OnlyShowIn=XFCE;
    StartupNotify=false
    Terminal=false
    Hidden=false

# MAKE AUTO START MT4 ON REBOOT

nano /home/rapid_vn/.config/autostart/metatrader4.desktop

    [Desktop Entry]
    Encoding=UTF-8
    Version=0.9.4
    Type=Application
    Name=MetaTrader 4
    Comment=MetaTrader 4
    Exec=wine "C:\\Program Files (x86)\\MetaTrader 4\\Terminal.exe"
    OnlyShowIn=XFCE;
    StartupNotify=false
    Terminal=false
    Hidden=false

# MAKE SCRIPT RESTART METATRADER 4

nano /home/rapid_vn/restart_mt4.sh

    #!/bin/sh
    pkill Terminal.exe &
    pkill terminal.exe &
    env DISPLAY=:1 wine "C:\\Program Files (x86)\\MetaTrader 4\\Terminal.exe" &

# MAKE TASK SCHEDULE RUN SCRIPT

mkdir /home/rapid_vn/.gnome
mkdir /home/rapid_vn/.gnome/gnome-schedule
mkdir /home/rapid_vn/.gnome/gnome-schedule/crontab

chmod u=rwx,g=rwx,o=rwx /home/rapid_vn/.gnome
chmod u=rwx,g=rwx,o=rwx /home/rapid_vn/.gnome/gnome-schedule
chmod u=rwx,g=rwx,o=rwx /home/rapid_vn/.gnome/gnome-schedule/crontab

nano /home/rapid_vn/.gnome/gnome-schedule/crontab/1

    ver=5
    title=Restart MetaTrader 4
    desc=
    output=0
    display=0
    command_d=sh /home/rapid_vn/restart_mt4.sh

echo 1 > /home/rapid_vn/.gnome/gnome-schedule/crontab/last_id

# EDIT TIME RUN TASK SCHEDULE

su - rapid_vn
crontab -e

    58 23 * * * sh /home/rapid_vn/restart_mt4.sh # JOB_ID_1

exit

reboot

---

