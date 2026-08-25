# Create env variable

```
vim .env
```

```
DB_NAME=training
DB_HOST=ipaddress
DB_USER=peserta
DB_PASS=password
APP_PORT=3000
```

```
#sonar-scanner

sonar-scanner \
  -Dsonar.projectKey=simple-apps \
  -Dsonar.sources=. \
  -Dsonar.host.url=http://172.23.8.116:9000 \
  -Dsonar.token=sqp_628301705fdc4945064d76917947b8866c14fbc3
  
  ```