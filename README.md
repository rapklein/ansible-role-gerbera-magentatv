ansible-role-gerbera-magentatv
=========

* This role adds Deutsche Telekom MagentaTV channels with udpxy (multicast-to-unicast/UDP-to-HTTP relay) URLs to Gerbera (UPnP Media Server).
* Works on Debian x86_64 (Buster and likely newer).

![Screenshot-VLC-Player-Android](docs/Screenshot-VLC-Player-Android.png?raw=true)

Requirements
------------

This role requires:
* there is verion of udpxy installed which is compatible to MagentaTV. At the time of writing the latest official udpxy release does not support source-specific multicast (SSM). There is a pull request open: https://github.com/pcherenkov/udpxy/pull/16 .
* Gerbera (UPnP Media Server) is installed.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):
```
gerbera_magentatv__sqlite_db: "/etc/gerbera/gerbera.db"
gerbera_magentatv__sqlite_db_default_schema: "/usr/local/share/gerbera/sqlite3.sql"
gerbera_magentatv__tmp_file: "/tmp/multicastadressliste.json"

gerbera_magentatv__url: "https://db.iptv.blog/multicastadressliste.json"

gerbera_magentatv__load_default_db: false

gerbera_magentatv__delete_pc_directory: false

gerbera_magentatv__container_name: "MagentaTV"
gerbera_magentatv__purge_container_contents: false

gerbera_magentatv__udpxy_port: 5056

gerbera_magentatv__owner: gerbera
gerbera_magentatv__group: gerbera
```

Dependencies
------------

None.

Example Playbook
----------------

```
- hosts: localhost
  become: yes
  roles:
    - role: ansible-role-gerbera-magentatv
      gerbera_magentatv__udpxy_ip: "192.168.0.1"
      gerbera_magentatv__load_default_db: false
      gerbera_magentatv__delete_pc_directory: false
      gerbera_magentatv__purge_container_contents: false
```

License
-------

MIT

Author Information
------------------

This role was created by Raphael Klein.
