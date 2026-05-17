# Caddy Server Config sample

## caddy-trusted-cloudfront
(https://github.com/xcaddyplugins/caddy-trusted-cloudfront)
### Caddyfile
```
trusted_proxies cloudfront {
	interval <duration>
}
# interval How often to fetch the latest IP list. format is caddy.Duration. For example 12h represents 12 hours, and "1d" represents one day. default value 1d.

```

## WebDAV for Caddy
(https://github.com/mholt/caddy-webdav)
### Caddyfile
```
@notget not method GET HEAD

route @notget {
    basicauth {
        username hashed_password_base64
    }
    webdav
}
file_server browse

```




## caddy-events-exec
(https://github.com/mholt/caddy-events-exec)
### Caddyfile

```
{
	events {
		on cert_obtained exec systemctl reload mydaemon
	}
}
```

#### json

```json
{
	"apps": {
		"events": {
			"subscriptions": [
				{
					"events": ["cert_obtained"],
					"handlers": [
						{
							"handler": "exec",
							"command": "systemctl",
							"args": ["reload", "mydaemon"]
						}
					]
				}
			]
		}
	}
}
```
