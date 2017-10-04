---
layout: page
title: A Case Study on Bloc Chat
thumbnail-path: "img/bloc-chat-landing.png"
short-description: Bloc Chat is an easy-to-use global messenger.
---

Bloc Chat is a single-page chat application built upon Firebase and AngularJS that allows users to send and receive messages in real-time. Upon entering the application, users are prompted to create a username via a modal, which is then saved to the browser with cookies. Users are then able to create or enter chat rooms to begin connecting with their peers.

##  Method

The project was built using HTML5, Bootstrap CSS, AngularJS, and Firebase.

Challenge

This project was my first time using cloud provider, Firebase to store and retrieve data in real-time.

##  Solution

#### Configuration


The configuration steps were similar to that used in Bloc Jams. I downloaded the correct dependencies that would be useful in deploying the application using Netlify. The app's presentation were implemented using Bootstrap CSS featuring a main navigation bar on the top and left hand sides.

I created a free account with cloud provider Firebase using my Google account.

####  Creating Chat Rooms

Rooms are stored as objects in Firebase, which allows for proper AngularJS binding to its applications. Angular's $firebase array service allowed me to store data such as rooms and messages in real-time. Using the $add() method inside AngularFire, I was able to add rooms to the firebase database.

{:.center}
![]({{ site.baseurl }}/img/bloc-chat-add-room.png)

In the app's interface, room creation was initiated using UI Bootstrap's $uibModal service. A form was created to store the room's data using ngSubmit.

####  List Messages

I had the most trouble with this checkpoint because I could not display the messages I created in the Firebase database. Each message data was associated with its parent data, in this case it was the roomId. The roomId references where the message was sent and the ID is generated every time an object was saved to Firebase. I created a Message factory within AngularFire's $firebase array.

{:.center}
![]({{ site.baseurl }}/img/list-message.png)

Here, my error that caused my messages not to display was not showing consistency with my reference name, which was "messages". Since I had defined my reference in Firebase as capitalized "Messages", then I should do the same in my code.

####  Set Username

Upon entrance to the chat application, users are prompted to create a username in order to begin using the application. If users chose to forgo creating a username, they would be continuously asked to create one before they are able to gain access to the application. I used Angular's .run() method to make sure a username is set at the time the app is initialized. The username is then saved as cookies.

####  Send Messages

The final portion of the app required the use of the send method inside the Message factory that takes a message object and injects it into the Firebase server. The ngSubmit method is used to specifies the Message controller to run when a user enters a message.
