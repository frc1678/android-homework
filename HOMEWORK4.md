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

Hey! You're connected! Now the way that you access data in Firebase might be a little different than you are used to. It is done via the concept called listeners. If you are interested in learning more, there is a really short and unorganized Wikipedia article: https://en.wikipedia.org/wiki/Observer_pattern. Other than that, well, I'm sure there's some other resource on the internet. I believe in you guys to find it.

Anyway, so with listeners, we tell our app that we want to look at a certain piece of data. The app listens to that piece of data and whenever whatever we are listening for happens to that data, the app does something. 

Before we progress any further, let's think through what we want our app to do. In terms of chatrooms, it needs to stay up to date with all the goings on in the chatroom-osphere. It also needs to create a new chatroom if it is not already there when the user is ready to chat. If it is there, well, then, we need to not make another or else stuff will get confusing. So let's do that!

The first thing that our app will need to listen to is the rooms list, right? We need to always be up to date on how many chatrooms there all and all of that other info. And when do we need to do that? Well, as soon as possible so we don't miss out on anything. If you need any help, I'd recommend you check out this page: https://www.firebase.com/docs/android/guide/retrieving-data.html.

Got that done? Great. You're almost there! Wait. No. You're really not. This one is long. But don't give up! You are almost done with this activity.

Let's think about what we decided we wanted our `MainActivity.java` to do. What were those? Well, there were only two of them.

1. Stay up to date with all the latest chatroom trends.
2. Create chatrooms if necessary

We've done No. 1, so let's head over to No. 2.  Now, when do we want to create the chatroom? If you said when the user presses the Chat button, then you'd be right! Now, the nice thing is that we already have a method that is called when you click that button, so we can just modify that method. Now, all we need to check for is if the chatroom exists. If it does, then all good. If not, then we need to make that? Got that handled? Good. You should use the system you established in Step 1 to help out with this.

Nice job (probably, I can't see your code)! So remember how I said there are only two things that we need to do in the `MainActivity.java`? Well, there's one thing I forgot to tell you: there's one more! I know, you're so excited, right? Anyway, we want our app to look nice and be user friendly, so lets start refining our UI. One problem with our current system is that the user currently has to type in the full name of their chatroom. Well, that would not be very much fun if the chatroom name was "Donaudampfschiffahrtsgesellschaftskapitän" (The German word for "Danube steamship company captain." I'm sure that there are many German Danube steamship company captains using our app.). Maybe, instead of forcing them to type it in every time, we can just make a dropdown menu. Okay, so time to start with fragments and listviews and filtering and search algorithms and computational efficieny and cats and magic Assembly code and, while we're at it, why not write it in Haskell, right? 

Well, fortunately for all of you, Google already did most of that work for you (minus the cats and Assemble and Haskell). The UI object is called the `AutoCompleteTextView`. Short name, I know. In order to make this work, we have to go replace the `EditText` in our `content_main.xml` file with an `AutoCompleteTextView`.






done.

good job, you have made chat app.

now make scouting system.

kthxbai.
