# REST API
REST stands for representational state transfer and is a particular standardized architecture designed with some constraints for the fast and efficient working of an API. Some of the important benefits of following this architecture while designing your API are as follows:

- They are simple and standardized in the community
- They are scalable and stateless meaning can be easily expanded or modified and do not depend on the state of the data
- They provide high performance as they support caching

## what are the constraints of a REST API?

## Client-Server constraint
This constraint states that the API should follow Client-Server architecture meaning there should be a client to request for services and a server to serve those requests. This constraint helps in separating both of these entities so that they can evolve separately. This way server does not need to know anything about the frontend and vice-versa.

## Stateless
This Constraint states that the server should not store any session related client data, Which means when a request is made, all the data should be in the request which is required by the server to respond precisely. The server will not store any data related to the client. Whereas the client is allowed to store sessional data in its context. This improves scalability as it reduces complexity.

## Cache constraint
This constraint states that every response by the server should include whether the provided response is cacheable or not. This reduces network latency.

## Uniform-interface constraint
This is one of the most important constraints of the REST architecture. It states that every client should be able to interact with the API uniformly. This constraint provides uniformity meaning the communication from the server is uniform to different clients.

## Layered system
It states that the API architecture should be composed of multiple layers to reduce complexity. For example, the model view and controllers in Django are layered system.
