# SGS OpenMRS 3.0 Application

This project holds the build configuration for the SGS OpenMRS 3.0 application, found on
[http://sgs.uwdigi.org/](sgs.uwdigi.org).

## Quick start

### Build the custom gateway, frontend and backend images

### Frontend

cd frontend

```
docker build -t sgs/frontend:v1.0.0 . 

```

### Gateway

cd ../gateway

```
docker build -t sgs/gateway:v1.0.0 . 

```

### Backend

cd ../

```
docker build -t sgs/backend:v1.0.0 . 

```

docker image ls

### Run the app

```
docker compose -p sgs_emr up -d
```

OR 

```
docker-compose -p sgs_emr up -d
```

## Clean up 

```
docker-compose -p sgs_emr down -v
```



