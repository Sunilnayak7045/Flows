# Flows

--> Suspend function returns a single object

![capture_3](https://user-images.githubusercontent.com/47368515/189876487-0827afeb-2b72-4403-a1b1-2a524467ce89.png)

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
  
  
--> Example : 
  
  ![capture_4](https://user-images.githubusercontent.com/47368515/189876916-5e99e7ab-0657-4749-89b4-6e26ee171c0f.png)
 
   --> channel.send is a suspending function... so we use CoroutineScope & dispatcher.main enables to runs on main thread


--> flows are Cold. Cold means it will produce only if there is consumer. 

![capture_5](https://user-images.githubusercontent.com/47368515/189884266-04a0bb74-08e7-444a-91b4-f3b16816d59d.PNG)

--> Method to stop flows in between by using job
  
  ![Capture_6](https://user-images.githubusercontent.com/47368515/189892945-115b9e45-f165-414e-a9c8-859bd6ed8271.PNG)

  o/p will be 1 , 2 , 3 because producer produces after 1 sec and job gets cancel after 3.5 sec
  
  ![Capture_7](https://user-images.githubusercontent.com/47368515/189893656-c0e48a47-c64d-40a5-91cf-b9278ea667e3.PNG)

  --> Case : when there is 1 producer & 2 consumer in which 2nd consumer starts at delay of 2.5 sec i.e data is never lost 
  
  ![Capture_8](https://user-images.githubusercontent.com/47368515/189898596-d815aebe-5813-4e3a-8087-a1d7994572a2.PNG)

  ![Capture_9](https://user-images.githubusercontent.com/47368515/189898656-7928aecd-d577-4864-9b63-dea4e2c3a0c4.PNG)

  
  

