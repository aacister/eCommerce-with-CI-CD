# eCommerce with CI/CD

* Built utilizing C#, ASP.NET Core, and Microsoft Azure Dev Ops
* This project has been moved to a Microsoft Azure DevOps environment under aacister organization at https://dev.azure.com/aacister/eCommerce with CI/CD setup.
* Microservice images and respective data source images have been deployed to Azure container registry at aacisterecommerceregistry.azurecr.io
* 3 microservice pipelins (UsersService, ProductsService, OrdersService) include builds, tests, and deployments to 5 separate environments (dev, qa, uat, staging, prod).
* Containers in Azure registry are deployed via respective microservice pipelines to a k8s (Azure Kubernetes Services) cluster.
* Project includes Users, Products, and Orders Microservices with MySql, MongoDb, Redis, RabbitMQ broker, Ocelot as internal Api Gateway and Azure API Mgmt Services as external API Gateway. Projects include Polly package for circuit breaker fault tolerance. 
* Originally built using Docker Compose with Products and Users images deployed to Docker Hub and Orders using local container build (to simulate real-world dev scenario).  Configured accordingly in Docker Compose yaml.  
* Later deployed to Azure Devops to include CI/CD. Azure pipelines include build, tests, and deployments to kubernetes cluster.  Azure API Management Services is API gateway for all external calls, forwarding to Ocelot internal gateway.
* OpenAI swagger json files are under respective microservice directories.

  #### API endpoints include below:

  ##### HTTP GET: 
  * https://aacister-ecommerce-api.azure-api.net/gateway/products
  * https://aacister-ecommerce-api.azure-api.net/gateway/products/search/product-id/:ProductID
  * https://aacister-ecommerce-api.azure-api.net/gateway/orders
  * https://aacister-ecommerce-api.azure-api.net/gateway/Orders/search/orderid/:orderID

  ##### HTTP DELETE: 
  * https://aacister-ecommerce-api.azure-api.net/gateway/products/:ProductID

  ##### HTTP POST:
  * https://aacister-ecommerce-api.azure-api.net/gateway/products
  <br> {
    "productName": "<string>",
    "category": 3,
    "unitPrice": "<double>",
    "quantityInStock": "<integer>"
}

  #####  HTTP PUT: 
  * https://aacister-ecommerce-api.azure-api.net/gateway/products
  <br? {
  "productID": "<uuid>",
  "productName": "<string>",
  "category": 3,
  "unitPrice": "<double>",
  "quantityInStock": "<integer>"
}


