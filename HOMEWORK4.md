#Homework 4

THIS IS NOT FINISHED:

Welcome back! You are doing very well indeed, and I am pleased to announce that you have made it to the final stage of the process. But that does not mean that you are almost finished. No, this part may prove to be the most difficult. You must navigate APIs, networking, and a myriad of other ideas and concepts to accomplish this chat application. 

First things first, we will be using a service called Firebase. You can get to their website simply by clicking the following link. I also advise you follow the instructions that they provide so that you can integrate Firebase into your application:
https://www.firebase.com/docs/android/guide/setup.html

It may be advisable to look into JSON, or Javascript Object Notation ( A way to conventiently transfer data ), since this is basically the structure that Firebase uses to store data.

Assuming you've done all the other assignments, which you should have, *cough* *cough*, you now have a way of displaying the chat messages. However, you're missing one thing...what could that be...oh yeah! Chat messages! Those are probably important. The problem is, we need to transfer these messages across multiple unconnected devices. 

This is where Firebase comes in. Firebase is essentially a giant syncing JSON file. So, by using Firebase, we can structure all of our data in a JSON file and then all of the phones that are using the app can see all of the messages. 

In order to make this work, you need to create a Firebase account. Please sign up for one at the Firebase website.

The account should start with an empty Firebase that can be reached with a link. In order to hook up our app to our Firebase, we need that link. So, copy the link. Got it copied? Ok. Good. 

Now, we want our app to connect to Firebase so it sees all of the data. When do we want to see all of that data? Yay! You're right! The app should connect immediately so the user does not have to wait for all of the data. Where does immediately happen in the code? Right again! The `onCreate()` of the first activity. So let's go into our `MainActivity.java` file. 

Wow, you took a long time to get into that file. I've been waiting here forever. Take your time, why don't you. We want to connect as immediately as possible, so let's put it as early as possible in the `onCreate()`. How early is as early as possible? Well, it's probably not a good idea to mess with what Android already puts in there for us (hint: it probably puts it in there for a reason). So after all of the setup stuff and the floating action button stuff, let's put these two lines of code:

```java
Firebase.setAndroidContext(this);
Firebase roomsRef = new Firebase("insert link here");
```




done.

good job, you have made chat app.

now make scouting system.

kthxbai.
