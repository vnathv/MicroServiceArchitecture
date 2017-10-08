# MicroServiceArchitecture


By this time you might definitely have heard about the term "Microservice". Here I will give a quick introduction of microservice and design principles to develop highly effective microservice.

Before start explaining microservice let's check what really a service is. In short, service is a piece of software which provides some kind of service to another piece of software, that another piece may be any kind of device/system such as a mobile phone, a tablet, a website, a database etc. In an SOA (Service oriented architecture) world, each of these different components will be communicating to service using the internet.

The main idea behind SOA is instead of using packaged modules within each client applications create it as a service so that many client applications (mobile, tablets, desktop, website, another service etc) can reuse the same functionality and in future if I want to create another type of client application then I don't need to write separate business logic for that client as I can reuse the logic I have written as service . Also, SOA allows us to scale up the service as demand increase (running copy of a service in multiple service or different containers ).

Let's jump into microservice architecture. Microservice is an improved version of SOA hence it will share all key characteristics of SOA, of scalability, reusability, standardized contracts and interface etc. So microservice is an evolution of SOA. Microservice basically introduce a new set of additional design principle which teaches we have to size a service correctly. The problem with traditional monolithic large SOA design was the difficultness of scaling up the service and change in an allowable way because of its size. Microservices basically provide services which are more efficiently scalable, which is flexible and which can provide high performance. An application based on microservice architecture is normally an application which is powered by multiple microservices and each one of these micro services will provide a set of related functions to a specific part of the application. Microservice normally has a single focus, it does one thing and it does it well.

In microservice architecture communication mechanism should be lightweight and quick as when we carry out a transaction within a microservice architecture system, the transaction will be a distributed transaction which is completed by multiple services, therefore the services should communicate in a quick and efficient way over the network. Microservice should be technology agnostic. It means to say if you have 10 microservices for you distributed transactions and you microservices should be technology agnostic in such a way that you can use any technology to create each one of these services. In the monolithic application, we usually will have a centralized database to share data between services and applications but in microservice architecture, each service has its own database. Microservice should be independently changeable, means I can upgrade, enhance or fix a specific microservice without changing any of the clients or any of the other services in the system. As microservices are independently changeable they should also be independently deployable. Let's take an example of a typical e-commerce system designed in microservice architecture.


            
   ![Micro-Service Architecture](../Architecture.jpg?raw=true "Micro-Service Architecture")  
  

            
          

            
          

            
          


        
      

As you can on the left-hand side of the picture above the shopping website is running on user's web browser. The browser connects to our shopping website via the internet. All the processing required for all the interactions with the website is carried out by a number of microservices which are running in the background. Each microservice has a single focus or a single set of related functions. Each microservice has it's own data storage and it's also independently changeable and deployable. For example, I could upgrade order service without upgrading any other part of the system. There might also be multiple instances of each type of microservice. For example, if order service is in demand, we might have several instances of the order service in order to satisfy demand. In order to direct a request from the shopping website to the correct instance of an order service, we have an API gateway. API gateway manages and routes a request to correct service. In the above example diagram when the customer places an order the shopping website might use multiple services and multiple functions within those service in order to satisfy that transaction and that is why in a microservice architecture a transaction is usually a distributed transaction because a transaction is actually satisfied by a number of services. As the transaction is distributed between different service the communication between these services should be super fast and lightweight. Below is few microservice design principle we should follow to produce highly effective microservices.

High Cohesion: Microservice content and functionality in terms of input and output should be coherent. It should have only a single focus and do it well. Each microservice should solely responsible for only one thing or there should only be one for the service to change. As a microservice focusing on doing only one thing it will be very flexible, scalable and flexible to accept new changes without worrying about breaking another part of the system.

Autonomous: Microservice should be autonomous which means a microservice should not be subject to change because of an external system it interacts with. A microservice should be stateless which means there should be no need to remember any previous transaction details. Each microservice should be independently changeable and independently deployable.

Business domain centric: A microservice should be business domain centric which means a service should represent a business function. For example, the organization you might have an accounts department that has a lot of accounting functionality and if we creating a microservice for accounts department then that microservice should only functionalities specific to accounts department. This idea is taken from domain driven design.

Resilience: A microservice should be resilient enough to embrace failure. Failure might be in the form of another service not responding to your service or it might be a 3rd party system not fails to connect. Whatever the failure microservice should embrace that by degrading the service or by using default functionality, for example, say postage service is down and account service wants to get data from postage service then account service can use default postage charges.

Observable: We need a way to be able to observe our system's health in terms system status, logs etc. This type of monitoring and logging needs to be centralized so that there is only one place where we need to go in order to view systems health check. One other specific reason we need centralized monitoring mechanism because as I have mentioned transaction in a microservice architecture will be distributed and it's will be difficult to monitor systems health if we don't have centralized monitoring.

Automation: We need automation tools to reduce all manual effort. You need automation testing written which will reduce manual regression testing and which will reduce the time taken to test integration between service and clients, also to reduce the time taken for environment setup. As microservice should be independently deployable we need all continuous integration tools which reduce the time of deployment. 
