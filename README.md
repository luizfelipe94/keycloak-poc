# POC Keycloack

## Docker deploy

### build e push
```
docker build -t VENDOR/IMAGE:TAG .
docker login -u "myusername" -p "mypassword" docker.io (caso use o docker hub)
docker push VENDOR/IMAGE:TAG .
```

### run container
Com h2. Banco de dados em memória
```
docker run -e KEYCLOAK_USER=admin -e KEYCLOAK_PASSWORD=admin VENDOR/IMAGE:TAG
```

Com postgres (Criar database e schema)
```
-e DB_DATABASE=keycloak
docker run -e DB_VENDOR=postgres -e DB_DATABASE=postgres -e DB_SCHEMA=keycloack -e DB_ADDR=<SERVER_IP> -e DB_PORT=9091 -e DB_USER=keycloak -e DB_PASSWORD=password -e KEYCLOAK_USER=admin -e KEYCLOAK_PASSWORD=admin -p 8080:8080 VENDOR/IMAGE:TAG
```

Obs: usar o docker-compose para testes locais