# QBittorrent Selinux
This is a policy for the program qbittorrent-nox that is distribute on Debian 11.

This policy is a personal project to learn selinux. It is not recommended for
production and is not expected to be safe.

## Installation
* Download and install qbittorrent module

      git clone https://github.com/pedrxd/qbittorrent-selinux.git
      cd qbittorrent-selinux
      make -f /usr/share/selinux/devel/Makefile
      semodule -i qbittorrent.pp
* Install qbittorrent-nox

      apt install -y qbittorrent-nox
* Create user qbt

      useradd qbt
* Create folder /var/lib/qBittorrent/

      mkdir /var/lib/qBittorrent/
  * Give permission to the user qbt

      chown -R qbt:qbt /var/lib/qBittorrent
* Set qbittorrent as a service, copy the qbittorrent.service to /etc/systemd/system/
* Run the service!

It can be necesary re-labels files. You can do it or using restorecon or using /.autolabel file.

## Booleans

* qbittorrent_read_privkeys: If you want qbittorrent to read tls privkeys
* qbittorrent_dir_search_mountpoints: If the download folder is on a external disk. You should set the label qbittorrent_downloads_t to the new folder.
