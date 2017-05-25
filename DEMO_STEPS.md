## Start
* rm -rf rjug4
* mkdir rjug4
* cd rjug4
## Microservice
* mkdir catalog
* cd catalog
* yo jhipster
    * Microservice application
    * Defaults except MySQL dev db
* yo jhipster:entity Product
    * name: String
    * description: String
    * price: BigDecimal
* mvn test
* mvn -Pprod package docker:build
## Gateway
* cd ..
* mkdir gateway
* cd gateway
* yo hipster
    * Microservice gateway
    * Defaults except MySQL dev db AND Angular 4
* yo jhipster:entity Product
    * Y
    * ../catalog
    * Yes, regenerate
* mvn -Pprod package docker:build
## Docker Compose
* cd ..
* mkdir docker-compose
* cd docker-compose
* yo jhipster:docker-compose
    * Microservice application
    * ../
    * (a)ll
    * Yes, for logs and metrics with JHipster Console
* docker-compose up -d
## URLs
* Gateway - http://localhost:8080
* Registry - http://localhost:8761
* Kibana - http://localhost:5601
    * Dashboard - Open - jvm-dashboard
## Scaling
* docker-compose scale catalog-app=2
## Finish
* docker-compose down

