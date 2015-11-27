#Homework 4

THIS IS NOT FINISHED:

Welcome back! You are doing very well indeed, and I am pleased to announce that you have made it to the final stage of the process. But that does not mean that you are almost finished. No, this part may prove to be the most difficult. You must navigate APIs, networking, and a myriad of other ideas and concepts to accomplish this chat application. 

First things first, we will be using a service called Firebase. You can get to their website simply by clicking the following link. I also advise you follow the instructions that they provide so that you can integrate Firebase into your application. Your life will be a lot easier if you read through that whole guide before you start on this assignment. You don't need to understand it all immediately, but at least get a sense of it. You'll be referencing it a lot throughout this assignment:
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

Hey! You're connected! Now the way that you access data in Firebase might be a little different than you are used to. It is done via the concept called listeners. If you are interested in learning more, there is a really short and unorganized Wikipedia article: https://en.wikipedia.org/wiki/Observer_pattern. Other than that, well, I'm sure there's some other resource on the internet. I believe in you guys to find it.

Anyway, so with listeners, we tell our app that we want to look at a certain piece of data. The app listens to that piece of data and whenever whatever we are listening for happens to that data, the app does something. 

Before we progress any further, let's think through what we want our app to do. In terms of chatrooms, it needs to stay up to date with all the goings on in the chatroom-osphere. It also needs to create a new chatroom if it is not already there when the user is ready to chat. If it is there, well, then, we need to not make another or else stuff will get confusing. So let's do that!

The first thing that our app will need to listen to is the rooms list, right? We need to always be up to date on how many chatrooms there all and all of that other info. And when do we need to do that? Well, as soon as possible so we don't miss out on anything. If you need any help, I'd recommend you check out this page: https://www.firebase.com/docs/android/guide/retrieving-data.html.

Got that done? Great. You're almost there! Wait. No. You're really not. This one is long. But don't give up! You are almost done with this activity.

Let's think about what we decided we wanted our `MainActivity.java` to do. What were those? Well, there were only two of them.

1. Stay up to date with all the latest chatroom trends.
2. Create chatrooms if necessary

We've done No. 1, so let's head over to No. 2.  Now, when do we want to create the chatroom? If you said when the user presses the Chat button, then you'd be right! Now, the nice thing is that we already have a method that is called when you click that button, so we can just modify that method. Now, all we need to check for is if the chatroom exists. If it does, then all good. If not, then we need to make that? Got that handled? Good. You should use the system you established in Step 1 to help out with this. For now, our chatrooms will just be strings containing the names of the chatrooms. For simplicity, ya know.

Nice job (probably, I can't see your code)! So remember how I said there are only two things that we need to do in the `MainActivity.java`? Well, there's one thing I forgot to tell you: there's one more! I know, you're so excited, right? Anyway, we want our app to look nice and be user friendly, so lets start refining our UI. One problem with our current system is that the user currently has to type in the full name of their chatroom. Well, that would not be very much fun if the chatroom name was "Donaudampfschiffahrtsgesellschaftskapitän" (The German word for "Danube steamship company captain." I'm sure that there are many German Danube steamship company captains using our app.). Maybe, instead of forcing them to type it in every time, we can just make a dropdown menu. Okay, so time to start with fragments and listviews and filtering and search algorithms and computational efficieny and cats and magic Assembly code and, while we're at it, why not write it in Haskell, right? 

Well, fortunately for all of you, Google already did most of that work for you (minus the cats and Assemble and Haskell). The UI object is called the `AutoCompleteTextView`. Short name, I know. In order to make this work, we have to go replace the `EditText` in our `content_main.xml` file with an `AutoCompleteTextView`. After that, we'll have to give that list an adapter, because the list needs to be modified. As a hint, your code should contain something like this:

```java
ArrayAdapter<String> dropdownAdapter = new ArrayAdapter<>(this, android.R.layout.select_dialog_item, rooms);
chatroomField.setAdapter(dropdownAdapter);
```

Okay. Now we're actually done with the `MainActivity.java`. You're almost kinda halfway through this assignment. Exciting, right? Hey, I warned you. Anyway, let's move on to the `ChatActivity.java` file now. Now, we'll need to access our Firebase in this part too. However, in this case, we really don't need to access the while Firebase. I think we'll be good with just accessing the messages in this specific chatroom. So, in the `onCreate()`, let's include this:

```java
Firebase roomRef = new Firebase("{your Firebase link}/messages/" + chatroom);
```

We'll also need to stay all hip and cool to all the messages that are passing around. How do we make sure we are always paying attention to the messages? You're right, the thing you don't do in school! Listen! So yeah, if you didn't get that, use a listener. For now, let's pretend that our messages are strings. We'll come back to that later. 

Great, now we always know the messages that are happening. However, as fun as that is, we can't see them (our eyesight is jut really bad). Remember that adapter you initially wrote to display the messages? Yeeaahh, that's no longer gonna work. Now, we have to update that list. Whenever we get a new list, we need to put that new message into our list. To make that all work in a nice and simple way, we're again gonna borrow from Google (they're very generous, aren't they?). The class we're going to use is `BaseAdapter`. The one thing I'm going to let you know about our good ol' friend `BaseAdapter` is that he has this handy-dandy method called `notifyDataSetChanged()`. I'm just going to hope that you can figure out what that means. Just in case you can't, look at these four links:

http://dictionary.reference.com/browse/notify?s=t
http://dictionary.reference.com/browse/data?s=t
http://dictionary.reference.com/browse/set?s=t
http://dictionary.reference.com/browse/change?s=t

You're about 75% of the way through now! Good job! Now just go back and make sure that you call that method whenever you need the list to update with the info. If you do that correctly, you should now start seeing all of the messages. Cool! But as fun as listening is, I want to talk! So let's get sending messages working. It's not much different from creating a chatroom in the `MainActivity.java`. There is just one thing I want to go over. After you hit the send button, the `EditText` you enter the message in should be cleared. It's another little UI tweak that makes the user not want to attack the developer with a candlestick in the library. 

Almost there! Just hang on a little longer! Now, one of the best (and worst) things about Firebase is how unstructured it is. It's like an book full of blank pages, and you can put whatever you want in, and interpret it and all that wonderful fuzzy stuff. One problem: computer's don't like interpreting unstructured stuff. And when computers don't like things, you get errors. And errors are bad. Bad. So let's learn how to structure the data we send to Firebase. 

The best way to do this is by creating a new class in our code. So let's create a new Java Class and call it `Message.java`. Get it? Got it? Good. You should be figure out how to structure the data from this page: https://www.firebase.com/docs/android/guide/saving-data.html. This time, I'm gonna let you guys figure it out on your own. You need to include the text of the message (String), the sender (String), and the time it was sent (Long). To find out the time in milliseconds, use the command `System.currentTimeMillis()`. Also, if they are in incognito mode, make sure that their sender name is "???" or something else equally mysterious.

If you are reading this, nice job. You figured it out all by yourself (with the help of Firebase's many-person development team). Not bad. Now that you've created your `Message.java` class, go back and replace all the ways use used to use strings for messages. It'll make your code a lot cleaner and nicer and happier. And `happy code == happy programmer`. 

Okay, bear with me for one last second. You're so close to done. The last thing is something that we always need to think about when transferring data across networks. The devices can have all different network speeds, or all sorts of different issues, so we need to make sure that all the messages are all sorted correctly. How about we sort the messages whenever we get a new one (or something a little more efficient and sophisticated, if you feel up to it). Either way, you'll be using the `Comparator` class. See if you can figure it out. 

Nice job! Before we finish with this chat app, let's run through one final checklist, to make sure everything is functioning as it should.

1. The UI is all correct as was described in the homework.
2. The dropdown feature of the chatroom selection works properly. 
3. Only valid usernames can be chosen (the length should be longer than "")
4. Can select incognito mode if desired.
5. When the user is ready to chat, if the chatroom does not exist, the app creates it. If the chatroom does exist, it does not create a new one.
6. Sends chat messages with sender, text, and time. Remembers not to send sender if they are incognito.
7. Displays chat messages upon receival in the proper chronological order, showing both sender and message.
8. All chat messages show up again when you leave the chatroom and then come back.
9. You have bought all of the app programmers a proper bribe of candy. (Kidding. Kind of.)

Okay, if that all is done, then nice job. Your app should work across as many devices as you can hook up to the chat system. Nice job! I hereby confer upon you the title of "Novice App Programmer". 

Now, to quote a wise man:

"good job, you have made chat app.

now make scouting system.

kthxbai."

See you all this season!
