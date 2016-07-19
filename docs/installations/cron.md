## What is Cron?

>Cron is a time-based job scheduler in Unix-like computer operating systems.
>(Source: [https://en.wikipedia.org/wiki/Cron](https://en.wikipedia.org/wiki/Cron), 2016-07-09)

##### Creating a Cronjob

* Open the terminal and open the system-wide cron-table with the following command:

```bash
sudo /etc/crontab
```

* An entry has the simple form: **TIME-SETTINGS -> USER -> COMMAND**

* Create an entry for Redis, to automatically start after rebooting:

```bash
@reboot         root    /home/n_schi16/redis-3.0.7/src/redis-server /home/n_schi16/redis-3.0.7/redis.conf
```

* Create an entry for the nodejs-server, to automatically start after rebooting:

```bash
@reboot         root    cd /home/n_schi16/GWoT-VST/server && node server.js --email_user EMAILADDRESS --email_password PASSWORD --postgres_user USER --postgres_password PASSWORD --redis --socket_io >> /home/n_schi16/log.txt
```

* Don't forget to change the missing `Usernames` and `Passwords`.

* Create an entry for the timeseries-creator, which will be executed every day at **00:01** :

```bash
1 0 * * *       root    cd /home/n_schi16/GWoT-VST/server && node timeseries.js --postgres_user USER --postgres_password PASSWORD >> /home/n_schi16/log_timeseries.txt
```

| `*` | `*` | `*` | `*` | `*` |
|-----|-----|-----|-----|-----|
| MINUTES <br> (0-59) | HOURS <br> (0-23) | DAYS <br> (1-31) | MONTH <br> (1-12) | WEEKDAY <br> (0-7), 0=Sunday |

More details can be found here: [https://wiki.ubuntuusers.de/Cron/](https://wiki.ubuntuusers.de/Cron/)

* For logging the `console.log()` and `console.error()` in the nodejs-scripts extend the executing-command with a logfile, like this:

```bash
node server.js >> /home/n_schi16/log.txt
```

* Create an entry for the weather-service, which will be executed every **30 minutes**:

```bash
*/30 * * * *   root    cd /home/n_schi16/GWoT-VST/server && node weather-service.js --postgres_user vst --postgres_password cloud >> /home/n_schi16/log_weather_service.txt
```
