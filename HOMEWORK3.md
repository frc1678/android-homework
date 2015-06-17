#Homework 3

Welcome back! I must say, you are tenacious. HOWEVER! This project will prove more difficult, and will require even more ingenuity and technique to accomplish. It is about Listviews and, more importantly, creating Listviews programmatically. You see, lists are a very important and effective way to display a lot of information, and is commonly used in many android applications. Learn them, live them, love them. Now, before we begin, here are some useful resources that you may need along your journey:

[ListViews](http://developer.android.com/guide/topics/ui/layout/listview.html)

[ListAdapters](http://developer.android.com/reference/android/widget/ListAdapter.html)

So, since you're here, I assume you've completed homework 2, and you should have an application that looks someting like this:

![MainActivity](Images/chat1.png)
![ChatActivity](Images/chat2.png)

So, the application is beginning to take shape! But if this chat app is going to work, it will need some way to display the chat messages! But how will that be accomplished?, you may ask. Well, let me introduce ListViews and ListAdapters. Now, you may remember that your app already has an embedded ListView. In layman's terms, a Listview is basically the (scrollable) space on the screen that allows users to look at all the different cells, or in this case, chat messages.

So, to actually put cells in your little ListView, you're going to have to use ListAdapters.


  <pre><code> setListAdapter(new ListAdapter() { </code></pre>
            @Override
            public boolean areAllItemsEnabled() {
                return false;
            }
            
            @Override
            public boolean isEnabled(int position) {
                return false;
            }

            @Override
            public void registerDataSetObserver(DataSetObserver observer) {

            }

            @Override
            public void unregisterDataSetObserver(DataSetObserver observer) {

            }

            @Override
            public int getCount() {
                return 0;
            }

            @Override
            public Object getItem(int position) {
                return null;
            }

            @Override
            public long getItemId(int position) {
                return 0;
            }

            @Override
            public boolean hasStableIds() {
                return false;
            }

            @Override
            public View getView(int position, View convertView, ViewGroup parent) {
                return null;
            }

            @Override
            public int getItemViewType(int position) {
                return 0;
            }

            @Override
            public int getViewTypeCount() {
                return 0;
            }

            @Override
            public boolean isEmpty() {
                return false;
            }
        });
       

Yep, you heard that right. You're going to have to implement that whole mess of code. Hey, its not that bad, really the biggest method that you're going to have to add code to is the <code>Public View getView</code> method. Thats the one that actually makes the cells for you, so make sure you do a good job. I should also probably mention that all of these methods are actually automatically called for you when our ListView get generated, so you don't have to worry about calling them manually anywhere(pretty slick, eh?)

Oh, I almost forgot, you're going to have to make sure this all works from data from an array. SO! First, we have to make an array of some sort. How about an array of your favorite foods?
So for me, it would look something like this:
<pre><code>
ArrayList<String> foodList = new ArrayList<String>();
        foodList.add("Chips");
        foodList.add("Electricity");
        foodList.add("Lost Souls");
        foodList.add("Wires");
        foodList.add("Disks");
        </code></pre>

Now, make sure you use your array to determine all of the methods that you're implementing. What do I mean by that? I'll give you an example: if my <code>getCount</code> method just returned 5 instead of <code>foodList.length</code>, then whenever my food preferences changed my application would not show all of the results properly. And we don't want that. This is known as hardcoding, and its risky business, so use with extreme caution. Oh and don't worry, you'll be changing up the data source very soon, this is just a placeholder to get you warmed up.



Well, thats it for me!
Best of luck, and I'll see you again in homework 4!
