# Flows

--> Suspend function returns a single object

![capture_3](https://user-images.githubusercontent.com/47368515/189871400-6462c81d-31dd-40f9-89cd-c4f71ff9fad6.png)

--> getUserNames() fun will get suspended unless and until all the user get added to the list.

![Capture_1](https://user-images.githubusercontent.com/47368515/189870973-db27fd6c-11be-4574-bcf5-b974e7d3914e.PNG)


suspend fun getUser() : User
{

// network call

return user

}

------------------------------------

suspend fun getUser() : List<User>
{

// network call

return list

}

-----------------------------------

Suspend functions work great for things like : 

-> Storing some value in database

-> Network calls

-> Doing task that returns single value.

------------------------------------
What are streams?
  
  ![Capture_2](https://user-images.githubusercontent.com/47368515/189871133-b2fd9fe6-9041-4244-88ec-56541c395614.PNG)
  
  --> IN case of streams as soon as user 1 gets the data it will return and so on... & In case of coroutines, getUserNames() fun will get suspended unless and until all the user get added to the list.

But there are scenarios where you have streams of data : 

--> Video Streaming ( phele 2 sec ka daata aayega.. phir next 2 sec ka data aayega..
i.e server's sends continuous data.
i.e single request raise kare phir server continuous data send kar raha h.)

--> FM radio (jese hi radio ko channel pe set karte h.. continuous data receive karne laagte h)

--> Mobile sending audio signals to Bluetooth speakers.
( when the phone is connected to speaker we r sending audio signal data from phone to speaker i.e we r streaming the data)

e.g : stock price , gps navigation uber,ola in  which continuous data is received etc. so here we reqd streams.


-> kotlin has asynchronous stream support using channels & flows.

1) Channels (Send & Receive)
2) Flows (Emit & Collect)

--> Channels are Hot.
Hot means producer is producing data continuously. 
irrespective of consumer, whether hey are consuming or not.

for e.g Movie Theater (movie will start on time, if we reaching 15 min late then, 15 min's data is being lost). 
i.e continuously data flow.

--> Flows are mostly Cold.
Cold means it will produce only if there is consumer. 


for e.g Hotstar/Netflix (we can watch movie at any time & pause the movie and we can watch them later, i.e no data is being lost). 
i.e non-continuously data flow.

--> Cold Stream are preferred over Hot Stream.
Cold Stream prevents Resource Wastage

--> Hot Stream
disadvantage : 
1) Resource Wastage
2) Manual Close (i.e mechanism is reqd to tell when we have to stop the data flow).




