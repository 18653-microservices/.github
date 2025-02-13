# Hi there 👋 Welcome to Coffee Shop

## instructions for deployment

To deploy the coffee shop, we need to build seprately on each repo and run the docker compose file here https://github.com/18653-microservices/sadms/blob/main/docker-compose.yml

### sadms-gateway
```sh
docker build -t sadms-gateway .
```
### sadms-notification
```sh
docker build -t sadms-notification .
```
