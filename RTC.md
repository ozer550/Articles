# Real Time communication

Real-time communication refers to a setup in which any two desired entities can instantly communicate data, information between each other with very minimal latency.
It has become a very important and necessary concept required by many modern software. A very good example is a Stock site that requires constant updates and real-time data otherwise it won't be of any use. A question that immediately comes to mind isn't a normal client-server communication in real-time?

## Standard Client-Server Architecture

The standard Client-server architecture runs on HTTP protocol which is a one-time request/response setup. What it means is that data or information is only communicated when a request is been sent to the server and vice-versa for the response. This can't possibly be real-time communication as data is only being communicated when we want it to. Also every time we create a request for data, a huge amount of buffer information is being communicated every time between server and client making the data exchange slow. HTTP is a stateless protocol meaning that after a request/response cycle there is no prior information unintentionally stored for recommunication or exchange again. For a real-time exchange, we need to create a setup such that we don't need to, again and again, exchange the same bulky information. These protocols lie on the application layer of the OSI model.  

![HTTP](https://user-images.githubusercontent.com/51698593/155126329-bb824594-dc2b-4851-b33e-3acd26a9aba7.png)

So then how can we improve further from this standard model? Let's think about the possible solutions:
-  we can somehow repeatedly use this request/response mechanism to create an illusion of real-time data/info exchange.
-  we can try to establish an agreement between client and server that we are going to extensively exchange data now and try to reduce exchanging bulky headers every time i.e stimulate a stateful communication
- Make the server broadcast data to the client every time the database is being updated
- Create a separate frame for this communication between client-server which is always active.

## Real-Time Communication Techniques
Different Techniques available for real-time communication are as follows:
- Regular polling
- Long polling
- Server-sent events
- Web sockets

### Regular Polling

Imagine you have a gaming pc with lots of games on it. You have a little brother, who likes to play games and asks you every time that can he have the pc to play games, you always patiently and kindly respond "I'm currently busy doing my work". He keeps on asking that until you are free from work and then you finally respond "OK you can play some games now". 

![regualr_polling](https://user-images.githubusercontent.com/51698593/155139680-605a722c-ceda-4ea6-b75f-b34380ed4eb1.png)

This is what exactly regular polling is, in this technique, the client repeatedly in regular short intervals asks the server if there is any change. The server responds to this by either saying there is no update or exchanging data if there is some change. This is clearly not real-time but could have some benefits if the polling interval is short. Regular polling does involve repeated unnecessary round trips between client-server.

### Long Polling 
You slowly start getting annoyed by the fact that your brother keeps on asking again and again so you don't respond every time but only when you are done with the work and ready to give the pc to your brother to play games.


![HTTP-Long-Polling](https://user-images.githubusercontent.com/51698593/155141173-0881c655-9283-42f8-a368-77ec1b11465d.png)


In this technique, the server simply sits on the request until something noteworthy happens, or the request is about to time out. This guarantees that the server has an open request to fire off a response at all times and can pass along information in real-time. This way server also does not need to respond every time to the client, optimizing various aspects.

### Server-Sent Events

You finally decide to annoy your younger brother this time, Whenever you are free yo0u go to him and poke him saying "hey wanna play games?" again and again.

![sse](https://user-images.githubusercontent.com/51698593/155264618-cdd2941d-d965-459d-add5-a629259e1646.png)

Server-Sent Events facilitate real-time communication but are largely one-directional push from server to client.

### Websockets

It is the weekend and you are really happy, your brother comes and says that he wanna play games, this time you say to him yea why not, I'll join you too. You both guys play games together once you are both done you go and do your work.

![websockets](https://user-images.githubusercontent.com/51698593/155265052-5e2d90b2-6731-4c34-bff7-c58f2f130917.png)

At the start, the server and client do a little handshake to make sure they can both speak the same language over WebSockets. Once negotiations are in place, WebSockets enable true persistent connection for bi-directional communications—the server can call the client and the client can call the server at any time
