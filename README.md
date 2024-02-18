
The blueprint of this project is to loosen the complexity of certain useful tools and get more familiar with it. It aims to become able to make microservices communicate with each other through the implementation of Consul registration, Consul config along with Spring Cloud Config, Spring Cloud Gateway, Vault config to deal with the secrets 
Consul Discovery

☑️ Spring Cloud Config <br>
☑️ Spring Cloud Gateway
☑️ Customer Service
☑️ Inventory Service
☑️ Order Service
☑️ Consul Config (Billing Service)
☑️ Vault (Billing Service)
☑️ Frontend Web With Angular



Architecture:

<img width="1728" alt="Activité Pratique N°4 Mise en oueuvre d'une architecture Micro-services avec Spring Cloud, Consul, Vault" src="https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/67c29210-4508-4579-a984-938c957cd9a3">




The first thing we have to do is to start 'Consul.' The following interface indicates that Consul is working on this machine at port '8500.' 
This interface lists the registered services.

![Screenshot (1713)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/c4a8f5e0-219f-448c-8437-79040257415c)



Next, we created a Git repository to handle versioning. it is only local for the time being

![Screenshot (1714)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/af68d0a9-1b21-4bc2-b9d7-f15748a21eee)



The config service is up and running as indicated in the Consul interface.

![Screenshot (1716)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/6fe7bede-6c28-49e2-88e8-4ff97fbbc379)



When the microservices start, they will send a request to this config service. In this example, we request the configuration for the customer-service, 
displaying the parameters that this microservice will receive. 
It also shows the global parameters located in the application.properties of the conf-service. Therefore, it will return not only the specified parameters but also the global ones.


![Screenshot (1717)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/0573a0e0-2034-4d98-ac5f-d33df9fef1a1)



if we request the parameters of the dev environment, it will indeed provide us with the parameters of the mentioned environment, and these arguments will be the ones taken into account. 
However, if there are no arguments in this environment, it will then use the default ones


![Screenshot (1718)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/b627d69c-dffa-42c7-80e2-a2744e10d10f)



this was to test if we can actually get the values of our params from the "global.params" and "customer.params" of the config-repo to the customer-service

![Screenshot (1719)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/4266a057-4f2c-433b-b4fb-f5d02217122c)


thanks to "@RefreshScope" from "spring-cloud-starter-config" and the POST request to actuator, we can now get the updated values of our params without having to restart the services. 

******* video 1



Here is what our customer looks like. this service is present solely for the purpose of creating a microservice with which we can work within a larger architecture.


![Screenshot (1724)  ](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/b969f7d6-af8f-47fe-848c-e809f278bf37)


![Screenshot (1724) ](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/114c6bf6-f539-40ca-9d15-36987b069d01)


![Screenshot (1724)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/8803034c-fb83-458a-9896-49c0fa9d7c4e)




the following test shows how we can from now on get to our services through the gateway


![Screenshot (1727) ](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/fe2084a1-a17c-4c16-8dae-763a58d9d277)


![Screenshot (1727)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/c3dcdda0-aefc-4363-a6d0-78f6d19b157c)



creating the inventroy service and adding it to the rest 

![Screenshot (1728)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/0f639f36-19ef-4682-9e43-1365aa273264)




this is our progress so far, we have 2 "functional" micro services (customer and inventory) plus the rest of services that ensure the micro service architecture

![Screenshot (1729)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/c6f067d4-23aa-4378-8076-6d26399fd63f)



the following is the order service, which handles the customer's orders of the different products of the app.
notice that the customers are located in a whole different micro service housed in a separate database, and the same holds true for the products
next step is to get the rest of info about the customer that placed the order. 

![Screenshot (1732)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/9ea238a0-3ac9-43d4-a037-45bbec995c04)



And these are the items included in the order with the ID '1'

![Screenshot (1734)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/df9867d4-6028-443b-94e2-e0a54558adf6)


to be able to display the entirety of data regarding customers who placed a particular order we needed to create a new controller, and we have done so.
the fact that we re able to see this means/prouves that :
✅the discovery service works
✅the gateway works 
✅orther service works, which itself means that customer service and inventory service work as well, since orther service needs those 2 micro services inorder to provide the needed data

![Screenshot (1738) ](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/94b5fd07-9b81-417a-9977-caad331352e3)



and this tests the ability to get the value of those early created params from the consul config service to the billing service at port 8084

![Screenshot (1739)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/4978bc5e-ed6e-4684-845a-28999bd08296)



consul config assures "hot config".. the changes of the params' values take effect instantly either by including @RefreshScope to our controller or by creating a component that uses @ConfigurationProperties. unlike spring cloude config that needs a POST request + a git commit inorder to refresh without having to restart the service.
which is seen as one of the major advantages of Consul config over the other config services

****** VIDEO 2





next step is to start Vault.. once it s running it provides an unseal key and a root token, the later should be used to access Vault at the port 8200

![Screenshot (1741)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/70f84d30-ba7f-40d8-b83e-8e587a910aa2)



here we set a pair of secrets within "billing-service" : the username and password, then we listed the secrets of this servoce

![Screenshot (1743)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/c28eda26-2775-4872-b031-821476aa1ae2)

![Screenshot (1744)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/3203bda2-9619-4a72-ba9f-1733144ff8b1)



we can create and access vault's secrets either using the console or in the vault interface

![Screenshot (1746)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/b956a729-bfe1-4a6c-b6a9-29c1275a4747)



this is how things look in "billing-service" after introducing vault to deal with secrets along with consul that manages the config

![Screenshot (1747)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/c84d2b26-3bc6-4ef0-88a3-b3820b9a6348)



this is the result of using the "VaultTemplate" interface in the billingServiceApplication to share sacrets with other micro services. 
inside the "secrets" directory we asked "VaultTemplate" to create another directory within which he s goint to store 2 secrets (privKey and pubKey) located in a folder named "keypair"

![Screenshot (1748)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/e284f318-9bd3-449b-a86e-01c597acbc21)



once we are done with the back end, now is the turn of the front. here is a first glint of it. so far we can visualize the list of products previously created.
needles to say that the request to obtain this data goes trough the gateway. 

![Screenshot (1749)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/eee24f5c-18a0-49b9-a4a4-d04071ee39a8)



and this is our app after adding a new component to handle customers so that we can match the back end. it lists the customers in a somewhat detailed manner. we can click the 'orders' button to display the list of orders placed by a spesific customer

![Screenshot (1751)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/54adea54-5056-4ae5-bd9d-23ae168df354)



by clicking the 'order' button of a custommer under the 'Customers' section, we will be re... to a page that lists his orders. it s basically a the complete record of a customer's orders, past and current etc.
inorder to see whats inside a specific order, we only have to click the 'Order Details' button

![Screenshot (1755)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/71b10b69-6f55-45d9-a074-e11dc35e3127)



lastly, this interface shows full info about prodects perchased by a certain customer, this means the byer and the items that were baught and the total amount to pay.

![Screenshot (1756)](https://github.com/YassineAlami/E-commerce-Micro-Services-SpringCloudConfig-ConsulConfig-SpringCloudGateway-ConsulRegistry-Vault/assets/40896739/e429e66b-1167-40b2-a11d-c39d7b7f35c1)







