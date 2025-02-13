# Hi there 👋 Welcome to Coffee Shop
## Project Structure
![image](https://github.com/user-attachments/assets/56e23d1b-0e6b-47dc-98dc-eea61f318f15)


## Deployment Instructions
Take a look at the main docker compose file [here](https://github.com/18653-microservices/sadms/blob/main/docker-compose.yml)
### [sadms-gateway](https://github.com/18653-microservices/sadms-gateway) (implemented in javascript)
```sh
docker build -t sadms-gateway .
```
### [sadms-notification](https://github.com/18653-microservices/sadms-notification) (implemented in javascript)
```sh
docker build -t sadms-notification .
```
### [sadms-frontend-employee](https://github.com/18653-microservices/sadms-frontend-employee) (implemented in nodejs + vue.js)
```sh
docker build -t sadms-frontend-employee .
```
### [sadms-frontend](https://github.com/18653-microservices/sadms-frontend) (implemented in nodejs + vude.js)
```sh
docker build -t ssadms-frontend .
```
### [sadms-user](https://github.com/18653-microservices/sadms-user) (implemented in java 18, updating to java 21 in progress) (initialize mysql userdb here)
```sh
docker build -t sadms-user .
```
### [sadms-auth](https://github.com/18653-microservices/sadms-auth) (implemented in java 18, updating to java 21 in progress) (initialize mysql authdb here)
```sh
docker build -t sadms-auth .
```
### [sadms-pay](https://github.com/18653-microservices/sadms-mypay) (implemented in java 18, updating to java 21 in progress)
```sh
docker build -t sadms-pay .
```
### [sadms-orchestrator](https://github.com/18653-microservices/sadms-order) (implemented in java 18, updating to java 21 in progress) (initialize mysql orchestratordb, kafaka, CDC, zookeeper here)
```sh
docker build -t sadms-orchestrator .
```
### [sadms-menu](https://github.com/18653-microservices/sadms-menu) (implemented in typescript)
```sh
docker build -t sadms-menu .
```
### [sadms-buyer](https://github.com/18653-microservices/sadms-buyer) (implemented in python 3.8)
```sh
docker build -t sadms-buyer .
```
### [sadms-inventory](https://github.com/18653-microservices/sadms-inventory) (implemented in java 18, updating to java 21 in progress)
```sh
docker build -t sadms-inventory .
```
### [sadms-banking](https://github.com/18653-microservices/sadms-banking) (implemented in java 18, updating to java 21 in progress)  (initialize mysql inventorydb here)
```sh
docker build -t sadms-banking .
```
### [sadms-employee](https://github.com/18653-microservices/sadms-employee) (implemented in java 18, updating to java 21 in progress)  (initialize mysql employee and rabbitmq here)
```sh
docker build -t sadms-employee .
```
### [sadms-player](https://github.com/18653-microservices/sadms-player) (implemented in java 18, updating to java 21 in progress) 
```sh
docker build -t sadms-player .
```






### [sadms-employee](https://github.com/18653-microservices/sadms-employee) (implemented in java 21)
```sh
docker build -t sadms-frontend-employee .
```
