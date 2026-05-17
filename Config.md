


# Caddyfile

```
{
	events {
		on cert_obtained exec systemctl reload mydaemon
	}
}
```

# json

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
