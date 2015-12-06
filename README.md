# backupd
Compressed and encrypted backups with 7zip and GPG

### KISS: Keep It Secret, Subhuman
Don't expect any sort of fanciness. Really. It is just a simple script that compresses the selected folder with 7zip, encrypts it with GPG and then moves it to a destination folder (local or remote). Plain and simple.

It does include basic support for WebDAV, but using other protocols shouldn't be hard to implement.

### Requirements
* A decent OS ¯\_(ツ)_/¯
* Bash
* GnuPG
* p7zip
* Some stuff to backup
* davfs2 (optional)
* A pinch of [love](http://i2.kym-cdn.com/photos/images/newsfeed/000/982/798/717.jpg)

### Installation

```bash
install -m644 backupd /usr/bin/
install -m644 backupd-daemon /usr/bin/
install -m644 backupd.service /usr/lib/systemd/user/
install -m644 backupd.timer /usr/lib/systemd/user/
chmod +x /usr/bin/{backupd,backupd-daemon}
install -g 0 -o 0 -m 0644 backupd.1.gz /usr/share/man/man1/
```

Or, if an Arch Linux / Parabola user, just install ```backupd ``` from [AUR](https://aur.archlinux.org/packages/backupd/). 

![Default view](http://i.imgur.com/4bvHVjO.png)

### Usage

```backupd [OPTION...] ```


| Option | Description |
|:-------------|-------------:|
| ```-s, --sync ``` | Force the creation of the backup file |
| ```-c, --config ``` | Re-generate the configuration file |
| ```--status ``` | Display the current settings |
| ```-d, --daemon ``` | Use as daemon with systemd |
| ```-h, --help ``` | Display the help message |

The output files will be named by hostname and creation date,
E.g.,

| File | Description |
|:-------------|-------------:|
| ```myPC-2015-12-05.gpg ``` | Backup file |
| ```myPC-2015-12-05.gpg.asc ``` | Digital signature |

You can run this script manually or let the systemd service do it for you.
By default, it will run the sync process weekly, 10 minutes after boot, but you can
change this editing the section ```[Timer] ``` of ```/usr/lib/systemd/user/backupd.timer ``` .
