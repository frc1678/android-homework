#Homework 1

Welcome. My purpose is to show you how layouts and UI work in android, as well as teaching you the basics of github.
Now to begin, clone this repository, where you will be demonstrating your prowess of android UIs and Layouts.
However, you may need some help along the way. To make your life easier, most, if not all, of the resources you require will be listed here.
Do not see their use as a weakness. In fact, navigating documentation is another key skill that even MLG Programmers make use of ~~from time to time~~ all day every day.

[Android Developer Website](http://developer.android.com/training/index.html)

Alright, so, on to the good stuff: the project. 

You'll be making a live chat app.  In this homework assignment, you'll create the layout for the first screen that the user will see.

To begin, create a new android project, and name it whatever your heart desires. However, you will soon encounter a screen that looks something like this:
![SDK image](Images/SDK.png)

Worry not! For I am here to tell you that setting it to API 19: Android 4.4(KitKat) will suffice for now. May I advise you, however, that whenever there are unfamiliar terms such as SDK or API, it is helpful to look up and at least have a basic understanding of what they mean. 
Anyway, continue hitting next and then finish. 

And Voila! You have created your first android application!
Now, you're faced with this scary interface: ![Default Image](Images/Default.png)

Do not fret, just navigate to the tab called activity_main.xml, and click the text tab.
You should be around here: ![XML Image](Images/XML.png)

Now, drumroll please, here is the game!
You must make an interface that conforms to the following specifications:

1. It must contain two [EditText](https://developer.android.com/reference/android/widget/EditText.html)s.  One EditText will be for the user to enter the name of the chat room that they want to join, and one EditText will be for the user's username.
2. Each EditText must have a [TextView](https://developer.android.com/reference/android/widget/TextView.html) to label what it's for.
3. Just below that, you'll have a [RelativeLayout](https://developer.android.com/reference/android/widget/RelativeLayout.html).  Inside the RelativeLayout, you'll have a [Switch](https://developer.android.com/reference/android/widget/Switch.html) that will enable Incognito Mode.  In this mode, users won't anounce that they're entering a chat room.  Perfect for spying on your friends!  You'll also have a TextView in the RelativeLayout, to tell the user what the Switch does.
4. Just below that, place a [Button](https://developer.android.com/reference/android/widget/Button.html) that the user will press to enter the chat room.
5. ????
6. Profit
7. For bonus points, Make all of it neon green (Hint: use #5BE300, you'll understand once you get there)

When you are done, you should have something that resembles this screen:

![Finished Homework 1](Images/chat1.png)

That's it from me! Well, one more thing. It may be helpful to tell you upfront that each homework assignment builds upon the next. So, it is advisable to do a good job on each part, or it may come back and bite you. Good Luck!


_TODO_:
* Resize final image
* Add help on XML
* Explain how to run app when finished writing it
