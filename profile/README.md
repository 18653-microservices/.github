# Hi there 👋 Welcome to Coffee Shop
## Project Structure
![image](https://github.com/user-attachments/assets/56e23d1b-0e6b-47dc-98dc-eea61f318f15)


## Deployment Instructions
Take a look at the main docker compose file [here](https://github.com/18653-microservices/sadms/blob/main/docker-compose.yml)

## Prerequisite
Make sure docker desktop and docker compose has version below

```Docker Compose version 27.4.0```

```Docker Desktop version: 4.37.2```

Makre sure you are using arm based M-chip Macbook

## Deployment

### Step 1. Run coffee shop 

clone the main docker compose using [sadms](https://github.com/18653-microservices/sadms/blob/main/docker-compose.yml)

run `docker compose up`

### Step 2. Run scottymq

clone two scotty repo using [MQProxy](https://github.com/CMU-SV-MQ/MessageQueueProxy) and [MQ](https://github.com/CMU-SV-MQ/MessageQueue)

**Start Message Queue Brokers** (first, build and run brokers):
```sh
cd MessageQueue
mvn clean install
docker build -t message-queue .
docker-compose up
```

**Start the Proxy Service**:
```sh
cd MessageQueueProxy
./mvnw clean install
docker build -t mq-proxy .
docker compose up
```

### Step 3. Run Coffeshop Frontend

clone coffee frontend repo using [Coffee Shop Frontend](https://github.com/18653-microservices/sadms-frontend)

run `npm run setup`

run `npm run dev`

Note: Frontend will run on port 3000 and 3001


### Step 4. Run MQ dashboard

clone mq dashboard repo using [MQdashboard](https://github.com/18653-microservices/sadms-mq-dashboard)

**Install the dependencies.**

We recommend using pnpm. If you want to use `npm`, just replace `pnpm` with `npm`.

```bash
npm install
```

**start the development server.**

```bash
npm run dev
```

Note: this is also running on port 3000, which already be taken by coffeeshop frontend, change to other port if you want.



## Useful Tips
All docker images are being pushed to docker hub using account 
`cmusv:cmusv`
