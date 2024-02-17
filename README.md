
The blueprint of this project is to loosen the complexity of certain useful tools and get more familiar with it. It aims to become able to make microservices communicate with each other through the implementation of Consul registration, Consul config along with Spring Cloud Config, Spring Cloud Gateway, Vault config to deal with the secrets 



Architecture:

![Uploading Activité Pratique N°4  Mise en oueuvre d'une architecture Micro-services avec Spring Cloud, Consul, Vault.png…]()



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
















