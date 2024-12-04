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
curl -X 'POST' \
  'https://api.elevenlabs.io/v1/text-to-speech/21m00Tcm4TlvDq8ikWAM' \
  -H 'accept: */*' \
  -H 'xi-api-key: sk_314977ee9ee7608bbde1ff681f50b2c0b5cb8f633e97a200' \
  -H 'Content-Type: application/json' \
  -d '{
    "text": "Hello! Today'\''s weather is beautiful. Would you like to go for a walk in the park?",
    "model_id": "eleven_monolingual_v1",
    "voice_settings": {
      "stability": 0.5,
      "similarity_boost": 0.75,
      "style": 0,
      "use_speaker_boost": true
    }
  }' \
  --output test-output.mp3
```