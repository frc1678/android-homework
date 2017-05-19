#Homework 4

Welcome back! You are doing very well indeed, and I am pleased to announce that you have made it to the final stage of the process. But that does not mean that you are almost finished. No, this part may prove to be the most difficult. You must navigate APIs, networking, and a myriad of other ideas and concepts to accomplish this chat application. 

First things first, we will be using a service called Firebase. You can get to their website simply by clicking the following link. I also advise you follow the instructions that they provide so that you can integrate Firebase into your application. Your life will be a lot easier if you read through that whole guide before you start on this assignment. You don't need to understand it all immediately, but at least get a sense of it. You'll be referencing it a lot throughout this assignment:
https://firebase.google.com/docs/android/setup.html

It may be advisable to look into JSON, or Javascript Object Notation ( A way to conventiently transfer data ), since this is basically the structure that Firebase uses to store data.

Assuming you've done all the other assignments, which you should have, *cough* *cough*, you now have a way of displaying the chat messages. However, you're missing one thing...what could that be...oh yeah! Chat messages! Those are probably important. The problem is, we need to transfer these messages across multiple unconnected devices. 

This is where Firebase comes in. Firebase is essentially a giant syncing JSON file. By using Firebase, we can structure all of our data in a JSON file and then all of the phones that are using the app can see all of the messages. 

In order to make this work, you need to create a Firebase account. Go to Firbase.com and make a firebase account for the new firbase website and not the legacy one. If you go to the link given above, it will ask you to create a new firebase project and initiate a firebase database. To initiate a new Firebase database, click the blue link that says, "Firebase console". That will bring you to the Firebase main page where you will see a blue button that says, "CREATE NEW PROJECT". You will want to click that button and after you click it, it will ask you to name your new project which you can name it Chat App or whatever you desire. Next, you will be brought to another page where you be given the choice to choose which application type you want to develope in and you will choose the one that says, "Add Firebase to your Android App". Once you have chosen Android, you will be asked to follow three simple tasks to initiate and link your android application directly to the new Firebase Database that you have create.

After you have finished creating and intiating a Firebase database for your app, it will ask you to add firebase to your app and all the instructions on how to do that will be given in the link. In order to add Firebase to your android application, you will need to know how to use the Android Manifest file and the Firebase documentation (The link above) will tell you exactly where to put what line of code in your Manifest file in order for Firebase to work in your app. After you have followed all the instructions given in the documentation and added Firebase to your app, you are good to go!

Now, we want our app to connect to Firebase so it sees all of the data. When do we want to see all of that data? You're right! The app should connect immediately so the user does not have to wait for all of the data. Where does immediately happen in the code? Right again! The `onCreate()` of the first activity. Let's go into our `MainActivity.java` file. 

Wow, you took a long time to get into that file. I've been waiting here forever. Take your time, why don't you. We want to connect as immediately as possible, so let's put it as early as possible in the `onCreate()`. How early is as early as possible? Well, it's probably not a good idea to mess with what Android already puts in there for us (hint: it probably puts it in there for a reason). After all of the setup stuff and the floating action button stuff, let's put these two lines of code:

1.) Make a global variable above the onCreate() method to declare Firebase database.

```java
public class MainActivity extends AppCompatActivity {
    public static FirebaseDatabase dataBase;
    public static DatabaseReference ref;
}
```
2.) Now specify your database in the onCreate().

```java
@Override
    public void onCreate() {
        super.onCreate();
        dataBase = FirebaseDatabase.getInstance();
        ref = dataBase.getReference();
    }
```

Hey! You're connected! Now the way that you access data in Firebase might be a little different than you are used to. It is done via the concept called listeners. If you are interested in learning more, there is a really short and unorganized Wikipedia article: https://en.wikipedia.org/wiki/Observer_pattern. Other than that, well, I'm sure there's some other resource on the internet. I believe in you guys to find it.

Anyway, so with listeners, we tell our app that we want to look at a certain piece of data. The app listens to that piece of data and whenever whatever we are listening for happens to that data, the app does something. 

Before we progress any further, let's think through what we want our app to do. In terms of chatrooms, it needs to stay up to date with all the goings on in the chatroom-osphere. It also needs to create a new chatroom if it is not already there when the user is ready to chat. If it is there, well, then, we need to not make another or else stuff will get confusing. So let's do that!

The first thing that our app will need to listen to is the rooms list, right? We need to always be up to date on how many chatrooms there all and all of that other info. And when do we need to do that? Well, as soon as possible so we don't miss out on anything. If you need any help, I'd recommend you check out this page: https://firebase.google.com/docs/database/android/retrieve-data.html.

Got that done? Great. You're almost there! Wait. No. You're really not. This one is long. But don't give up! You are almost done with this activity.

Let's think about what we decided we wanted our `MainActivity.java` to do. What were those? Well, there were only two of them.

1. Stay up to date with all the latest chatroom trends.
2. Create chatrooms if necessary

We've done No. 1, so let's head over to No. 2.  Now, when do we want to create the chatroom? If you said when the user presses the Chat button, then you'd be right! Now, the nice thing is that we already have a method that is called when you click that button, so we can just modify that method. Now, all we need to check for is if the chatroom exists. If it does, then all good. If not, then we need to make that? Got that handled? Good. You should use the system you established in Step 1 to help out with this. For now, our chatrooms will just be strings containing the names of the chatrooms. For simplicity, ya know.

Nice job (probably, I can't see your code)! Remember how I said there are only two things that we need to do in the `MainActivity.java`? Well, there's one thing I forgot to tell you: there's one more! I know, you're so excited, right? Anyway, we want our app to look nice and be user friendly, so lets start refining our UI. One problem with our current system is that the user currently has to type in the full name of their chatroom. Well, that would not be very much fun if the chatroom name was "Donaudampfschiffahrtsgesellschaftskapitän" (The German word for "Danube steamship company captain." I'm sure that there are many German Danube steamship company captains using our app.). Maybe, instead of forcing them to type it in every time, we can just make a dropdown menu. Okay, so time to start with fragments and listviews and filtering and search algorithms and computational efficieny and cats and magic Assembly code and, while we're at it, why not write it in Haskell, right? 

Well, fortunately for all of you, Google already did most of that work for you (minus the cats and Assembly and Haskell). The UI object is called the `AutoCompleteTextView`. Short name, I know. In order to make this work, we have to go replace the `EditText` in our `content_main.xml` file with an `AutoCompleteTextView`. After that, we'll have to give that list an adapter, because the list needs to be modified. As a hint, your code should contain something like this:

```java
ArrayAdapter<String> dropdownAdapter = new ArrayAdapter<>(this, android.R.layout.select_dialog_item, rooms);
chatroomField.setAdapter(dropdownAdapter);
```

Okay. Now we're actually done with the `MainActivity.java`. You're almost kinda halfway through this assignment. Exciting, right? Hey, I warned you. Anyway, let's move on to the `ChatActivity.java` file now. Now, we'll need to access our Firebase in this part too. However, in this case, we really don't need to access the whole Firebase. I think we'll be good with just accessing the messages in this specific chatroom. In the `onCreate()`, let's include this:

```java
DataBaseReference roomRef = dataBase.child("messages").child("chatRoom");
```

We'll also need to stay all hip and cool to all the messages that are passing around. How do we make sure we are always paying attention to the messages? You're right, the thing you don't do in school! Listen! So yeah, if you didn't get that, use a listener. For now, let's pretend that our messages are strings. We'll come back to that later. 

Great, now we always know the messages that are happening. However, as fun as that is, we can't see them (our eyesight is just really bad). Remember that adapter you initially wrote to display the messages? Yeeaahh, that's no longer gonna work. Now, we have to update that list whenever we get a new message and the adapter you used initially won't update when you get new data. To make the updating work in a nice and simple way, we're again gonna borrow from Google (they're very generous, aren't they?). The class we're going to use is `BaseAdapter`. The one thing I'm going to let you know about our good ol' friend `BaseAdapter` is that he has this handy-dandy method called `notifyDataSetChanged()`. I'm just going to hope that you can figure out what that means. Just in case you can't, look at these four links:

1. http://dictionary.reference.com/browse/notify?s=t
2. http://dictionary.reference.com/browse/data?s=t
3. http://dictionary.reference.com/browse/set?s=t
4. http://dictionary.reference.com/browse/change?s=t
Note: These are just dictionary definitions. Don't be trolled
You're about 75% of the way through now! Good job! Now just go back and make sure that you call that method whenever you need the list to update with the info. If you do that correctly, you should now start seeing all of the messages. Cool! But as fun as listening is, I want to talk! Let's get sending messages working. It's not much different from creating a chatroom in the `MainActivity.java`. There is just one thing I want to go over. After you hit the send button, the `EditText` you enter the message in should be cleared. It's another little UI tweak that makes the user not want to attack the developer with a candlestick in the library. 

Almost there! Just hang on a little longer! Now, one of the best (and worst) things about Firebase is how unstructured it is. It's like an book full of blank pages, and you can put whatever you want in, and interpret it and all that wonderful fuzzy stuff. One problem: computer's don't like interpreting unstructured stuff. And when computers don't like things, you get errors. Errors are nice, because they try to tell you why your code wont work, and save you from destroying important data, hurting your computer, or picking up the lead pipe (if you are Colonel Mustard).
_So_, let's learn how to structure the data we send to Firebase. 

The best way to do this is by creating a new class in our code. Let's create a new Java Class and call it `Message.java`. Get it? Got it? Good. You should be figure out how to structure the data from this page: https://www.firebase.com/docs/android/guide/saving-data.html. You need to include the text of the message (String), the sender (String), and the time it was sent (Long). To find out the time in milliseconds, use the command `System.currentTimeMillis()`. Also, if they are in incognito mode, make sure that their sender name is "???" or something else equally mysterious. (e.g. "thisisnot%s", sender_name)
An example of where to start would be:
`public class Message {

    private String username;
    private long sendTime;
    private String chatMessage;
    private String messageType = "null";
    private boolean isComplete = false;  `
    
   `In a new method (you should be able to figure this method with firebase) write
   `this.username = username; `
   And repeat it for each variable.
   Now we need to fetch our data. An example for the Username is:
   `public String getUsername() {
        return username; 
        `
If you are reading this, nice job. You figured it out all by yourself (with the help of this assignment, Firebase's many-person development team, Google, etc.). Not bad. Now that you've created your `Message.java` class, go back and replace all the ways use used to use strings for messages. It'll make your code a lot cleaner and nicer and happier. And `happy code == happy programmer`. In addition, we also should show the sender in grey underneath the message now. We'll do this by using `android.R.layout.simple_list_item_2` now. The documentation for this layout can be found online.

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
10. Test the app and debug until it meets your quality standards. For 1678 programmers, those can be found on the team google drive.

Okay, if that all is done, then nice job!!!! Your app should work across as many devices as you can hook up to the chat system. I hereby confer upon you the title of "Novice App Programmer". 

![The Knighting of the App Programmer](Images/knighting.jpg)


Now, to quote a wise man:

"good job, you have made chat app.

now make scouting system.

kthxbai."

See you all this season!
