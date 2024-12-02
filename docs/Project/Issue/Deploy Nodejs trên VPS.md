---
Created: 22:44 01-12-2024
tags:
  - issue
---
Link relate:
- https://hayksimonyan.substack.com/p/deploying-nodejs-app-to-digitalocean-419

---

TLDR: 


## Enable Firewall
ufw enable
ufw allow ssh && ufw allow http && ufw allow https

```
curl -X 'GET' \

'https://api.elevenlabs.io/v1/voices' \

-H 'accept: application/json' \
-H 'xi-api-key: sk_314977ee9ee7608bbde1ff681f50b2c0b5cb8f633e97a200'
```