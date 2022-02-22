# Real Time communication

Real time communication refers to a setup in which any two desired entites can instantly communicate data, information between each other with very minimal latency.
It has become a very important and necessary concept required by many of the mordern softwares. A very good example is a Stock site which requires constant updates and real time data otherwise it won't be of any use. A question that immediately comes to mind is isin't a normal client-server communication real time?

## Standard Client-Server Architecture

The standard Client-server architecture runs on HTTP protocol which is a one time request/response setup. What it means is that data or information is only communicated when a request is been sent to server and vice-versa for response. This can't possibily be a real time communication as data is only being communicated when we want it to. Also every time we create a request for data, huge amount of buffer information is being communicated every time between server and client making the data exchange slow. HTTP is a stateless protocol meanning that after a request/response cycle there is no prior information unintentionally stored for recommunication or exchange again. For a real time exchange we need to create a setup such that we dont need to again and again exchange same bulky information. These protocols lie on the application layer of OSI model.  

![HTTP](https://user-images.githubusercontent.com/51698593/155126329-bb824594-dc2b-4851-b33e-3acd26a9aba7.png)

So then how can we improve firther from this standard mode? Lets think about the possible solutions:
-  we can somehow repeteadly use this request/response mechanism to create a illusion of real time data/info exchange.
-  we can try to establish an agreement between client and server that we are going to extensively exchange data now and try to reduce exchanging bulky headers every time i.e stimulate a statefull communication
- Make the server broadcast data to client everytime database is bieng updated
- Create a seperate frame for this communication between client-server which is laways active.

## Real-Time Communication Techniques
Different Techniques available for real-time communication are as follows:
- Regualr polling
- Long polling
- Server-sent events
- Web sockets

### Regular polling

Imagine you have a gaming pc with lots of games in it. You have little brother, who likes to play games and asks you everytime that can he have the pc to play the games, you always patiently and kindly respond "I'm currently busy doing my work". He keeps on asking that untill your free from work and then you finally respond "OK you can play some games now". 

![regualr_polling](https://user-images.githubusercontent.com/51698593/155139680-605a722c-ceda-4ea6-b75f-b34380ed4eb1.png)

This is waht exactly regualr polling is, in this technique the client repeteadly in regular short interval asks server if there is any change. The server responds to this with either saying there is not update or exchanging data if there is some change. This is clearly not real time, but could have some benefits if the polling interval is short. Regular polling does involve repeated unnecessary round trips between client-server.

### Long polling 
You slowly start getting annoyed by the fact that your brother keeps on asking again and again so you dont respond everytime but only when you done with the work and ready to give the pc to your brother to play games.


![longpolling](https://user-images.githubusercontent.com/51698593/155140978-cd25ca0a-83fa-4438-87fe-d823f90f3f38.png)

In this technique the server simply sits on the request until something noteworthy happens, or the request is about to time out. This guarantees that the server has an open request to fire off a response at all times and can pass along information in real time. This way server also doesnot need to respond everytime to client optimising various aspects.



