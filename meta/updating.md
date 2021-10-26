Post-update
===========

Steps to restore custom reMarkable stuff after an update

SSH/SCP access
--------------

Access at `root@10.11.99.1` or, since configuring in `~/.ssh`, at `root@rem`.
The root password is `SMyutEAChp`.

**The RSA key will have changed:**
If you get 'Host key verification failed.' due to rem's identification
changing from the stored value in 'known hosts', remove the old line
from `~/.ssh/known_hosts` (check the IP address to make sure you've got
the correct one).

Templates
---------

SCP the PNG files in `~/code/rem/templates` into the device:

```
scp ~/n/rem/templates/*.png root@rem:/usr/share/remarkable/templates/
```

and add their metadata from inside `/n/rem/templates/metadata.json` into
`/usr/share/remarkable/templates/templates.json` (you have to interleave the
JSON, I recommend to `pbcopy < metadata.json` and paste and indent it in the
appropriate place inside `templates.json` using `vim`).


Splash-screens
--------------

This is simpler. Just get the files in `~/n/rem/splashscreens/matt`
into `/usr/share/remarkable`. You may want to preserve those that are
already there if you haven't already. Then:

```
scp ~/n/rem/splashscreens/matt/*.png root@rem:/usr/share/remarkable
```

rmview
------

This should reinstall itself on the device. So just plug in and run rmView?

Ah, I have to reset the public key, just delete the line from the ssh config
known hosts file and confirm the new key.

Entware
-------

From readme:

> Entware remains intact in `/home/root/.entware`, [but] the mount over
  `/opt` has to be recreated with `entware_reenable.sh`.
> 
> ```
  wget -O - http://raw.githubusercontent.com/Evidlo/remarkable_entware/master/reenable.sh | sh
  ```

(TODO: It would be good to get a local version of this script?)
