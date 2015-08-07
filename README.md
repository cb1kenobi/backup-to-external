# backup-to-external

Simple bash script to turn on an external hard drive, perform an rsync, turn off
the drive, and e-mail you the results. Pretty rad, eh?

To power on/off the drive, this script communicates with a
[Remote Power Switch](http://3gstore.com/product/4186_single_outlet_remote_power_switch.html)
sold by 3Gstore.com.

This script has only been tested with the single outlet model. It also only
supports secure smtp servers, but you can hack the script to do non-secure.

## Installation

```
curl http://bit.ly/backup-to-external > /usr/local/bin/backup-to-external

chmod +x /usr/local/bin/backup-to-external
```

Next generate a default config file that you can tweak:

```
backup-to-external init
```

### Config Settings

The settings can be stored in either `/etc/backup-to-external` or
`~/.backup-to-external`.

```
ezoutlet_host="<hostname or ip>"

source_dir="/path/to/source"

dest_disk="/dev/sd?#"
dest_mount="/path/to/mount"
dest_dir="/path/to/mount/dest"

smtp_url="smtps://host:port"
smtp_user="user@domain.com"
smtp_pass="secret"

email_from="user@domain.com(backup-to-external)"
email_to="user@domain.com"
email_subject_prefix="[backup to external]"
```

## Usage

Simply run:

```
backup-to-external
```

To automate backups, create a symlink into your cron directory:

```
ln -s /usr/local/bin/backup-to-external /etc/cron.daily/backup-to-external
```

## License

(The MIT License)

Copyright (c) 2015 Chris Barber

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
