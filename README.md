# VSHN Apprentice Linux Test for C2

## Tasks
### Connect to the Server
- Connect to the server with the IP XXXXX - use the User `cloud_user` and the Password `XXXXX`.
- Enable SSH to Connect with your Public Key and without a Password.

### Package Installation
- Install the `tree` utility
- Install the `apache2` package

### Aliases
- For the user `cloud_user`, create an alias named `data-tree` for the command `tree /data`. This alias must be persistent.

### Storage Management
- There is a Hard Disk available: /dev/nvme1n1
  - Create an LVM Volume Group (VG) named `vg-data`, containing this Hard Disk
  - Create a LVM Logical Volume (LV) named `lv-data` in the VG `vg-data`
  - Create an XFS Filesystem on the LV `lv-data` in the VG `vg-data`
  - Mount the LV `lv-data` from the VG `vg-data` persistently at `/data`

### File and Directory creation
- Create the directory `/data`
- Move the directory `/var/www` and its contents to `/data/`
- Create a symlink named `/var/www` pointing to `/data/www`

### Archives
- Download the archive `https://github.com/a-Tell/linux-test/raw/main/vshn-page.tar.gz` - Extract the contents of the archive to /data/www/html/, so in the end it should look like this:
  ```
  /data
  └── www
      └── html
          ├── img
          │   └── vshn-logo.svg
          ├── index.html
  ```

### Cronjobs
- Create a cronjob in `/etc/crontab` that executes the following command as `root` every minute:
  ```
  date >> /data/www/html/log.txt
  ```
  (you may use [crontab.guru](https://crontab.guru) as a help)

### Modifying files with `sed`
- Using the `sed`-command, replace all `VSHN` with `VSHN AG` in the file `/data/www/html/index.html`. Write the command to `/data/www/html/sed-command.txt`.

### Filesystem permissions
- Make sure the Owner of `/data/www` and all its contents is `www-data`
