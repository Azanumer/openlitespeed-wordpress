# OpenLiteSpeed for WordPress

Production-ready starting configs for running WordPress on OpenLiteSpeed
(with LiteSpeed Cache), tuned for cheap VPS boxes (1–2 GB RAM).

## Files

| File | What it is |
|---|---|
| `vhost-wordpress.conf` | Full vhost template: pretty permalinks at vhost level, LiteSpeed Cache module config, static-asset browser cache, blocked sensitive files, log rotation |
| `htaccess-lscache.txt` | Drop-in `.htaccess` add-on: HTTPS redirect, browser-cache headers, no-cache rules for `wp-login.php`/`wp-cron.php`, LSCache plugin tuning notes |

## Quick start

1. Create the vhost in the WebAdmin console (or write to
   `/usr/local/lsws/conf/vhosts/<domain>/vhconf.conf`) and replace
   `EXAMPLE.COM` with your domain.
2. Graceful restart: `/usr/local/lsws/bin/lswsctrl restart`
3. Install the **LiteSpeed Cache for WordPress** plugin and follow the
   tuning notes at the bottom of `htaccess-lscache.txt`.

## Why OpenLiteSpeed over Nginx for small boxes?

Event-driven server + server-level page cache (LSCache) usually beats
Nginx + FastCGI cache on 1 GB RAM with zero extra daemons — one process
does HTTP, TLS, and caching. Pairs well with a small MariaDB.

MIT licensed.
