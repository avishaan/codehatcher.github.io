---
title: "SMS Implementation Examples in iOS8" 
excerpt: "How various iOS apps implement SMS/Text based sharing. We consider the pros and cons of each."
categories:
  - product development
tags:
  - product development
  - iOS
  - SMS
toc: true
toc_sticky: true
---
## Product Considerations
When a requirement to be able to SMS/text users in the address book of the user of an app is necessary there are different implementation methods that we see in various apps. 
Here we consider how the user chooses the addresses to include in the SMS/text message. We also consider the pros and cons of each option as well as look at a list of the most popular apps that have this ability and see which option they chose for their implementation.

**Update 12-5-2014**
I now realize that the only apps that implement an address book for sharing are those that need the contacts for other purposes.


## Option A

![OptionA sb_float](/assets/posts/migrated-codehatcher-blog/VenmoAddressBook_medium.png)

In implementation A you allow the user to see a complete list of their contacts and select which ones they want to send a text to. Once the user has selected the list they proceed to the next step which shows them their text message to send.

### Pros
- You can see all possible recipients

### Cons
- Requires 2x the amount of steps to complete
- Scrolling the entire list of contacts can cause the user to put it off to another time
- Some users (wrongly) assume this means the app is storing this information



## Option B
![Quipics sb_float](/assets/posts/migrated-codehatcher-blog/QuipicsDirectMessage_medium.png)

In this implementation, you skip right to showing the user the familiar SMS/text message screen where they have to enter the names of those they want to share with. The text message can (and generally should) be seeded with some sort of message.

### Pros
- Familiar (comfort) to normal texting interface
- 1 step process
- Easy to invite known groups (such as close friends)

### Cons
- You may miss potential recipients.



## Verdict
I don't think there is a clear winner here. The pros and cons of each implementation option make them very even. It comes down to what you want. 

The most interesting piece of information is that a couple of users don't use implementation A because it looks like it is saving your contact information. Although this is not the case sometimes the perception of the user is all that matters. 

Since there is no clear winner I think it's worth looking at other apps that have some form of SMS/text sharing implemented and see what they do. The idea being that these big companies have done the research into this and have decided on the optimal implementation (of course this is based on a set of assumptions that may not apply to your app).

If you don't want to spend the time looking at each you'll find that most of the apps **implement option B** for whatever reason.

*Side Note: It's amazing how many apps don't even implement this feature*

### Uber
**Option B** Implementation

![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/uber_medium.PNG)

### Tinder
**Option B** Implementation

![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/tinder_medium.PNG)

### Whatsapp
**Option A** Implementation

![Silvrback blog image](/assets/posts/migrated-codehatcher-blog//whatsapp_medium.PNG)

### Spotify
**Option B** Implementation

![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/spotify_medium.PNG)

### Waze
**Option B** Implementation (Approx.)

![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/waze_medium.PNG)

### Evernote
**Option B** Implementation (Approx.)

![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/evernote_medium.PNG)

### Venmo
**Option A** Implementation

![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/VenmoAddressBook_large.png)

### HotelsTonight
**Option B** Implementation

![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/hoteltonight_medium.PNG)

### Shazam
**Option B** Implementation

![Shazam](/assets/posts/migrated-codehatcher-blog/shazam_medium.PNG)