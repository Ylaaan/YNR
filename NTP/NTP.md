# NTP

## 📜Configure NTP client📜

The configuraiton is generally situated in `/etc/ntp.conf`

## 🔁Restart the NTP client🔁

Either :

```bash
sytemctl restart ntp
```

or (CentOS)

```bash
systemctl restart ntpd
```

Note : Sometimes, Chrony is used instead of the classic NTP client, in that case use `chrony` or `chronyd`

## 💹Check NTP stat💹

### Classic NTP

```bash
ntpstatus
```

To see the server list and infos :

```bash
ntpq -pn
```

### Chrony

Une fois le service redémarré, attendre quelques minutes.

```bash
chronyc tracking
```

## 📆Check server date📆

```bash
date
```
