# Real Time communication

Real time communication refers to a setup in which any two desired entites can instantly communicate data, information between each other with very minimal latency.
It has become a very important and necessary concept required by many of the mordern softwares. A very good example is a Stock site which requires constant updates and real time data otherwise it won't be of any use. A question that immediately comes to mind is isin't a normal client-server communication real time?

## Standard Client-Server Architecture
The standard Client-server architecture runs on HTTP protocol which is a one time request/response setup. What it means is that data or information is only communicated when a request is been sent to server and vice-versa for response. This can't possibily be a real time communication as data is only being communicated when we want it to. Also every time we create a request for data, huge amount of buffer information is being communicated every time between server and client making the data exchange slow. HTTP is a stateless protocol meanning that after a request/response cycle there is no prior information unintentionally stored for recommunication or exchange again. For a real time exchange we need to create a setup such that we dont need to again and again exchange same bulky information. These protocols lie on the application layer of OSI model.  
![HTTP](https://user-images.githubusercontent.com/51698593/155126329-bb824594-dc2b-4851-b33e-3acd26a9aba7.png)
