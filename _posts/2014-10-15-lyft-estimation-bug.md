---
title: "Reframing a Lyft Bug as Product Feature" 
excerpt: "Discussing a bug as a feature in the Lyft app that potentially gets users rides at a lower 'prime time' multiplier."
categories:
  - Product
tags:
  - Bugs
  - Lyft
  - Product
toc: true
toc_sticky: true
---
I am a huge fan of pushing the limits when it comes to existing services. Lyft does just that. I recently stumbled across a 'bug' that may not actually be a bug in the typical software sense. However, from Lyft's perspective it may as well be a bug. Video example of "bug" at the end of the article.

### Positive **Product** Spin

I also wonder, maybe this doesn't **have** to be a bug. Hear me out for a second. Clearly, Lyft has a reason to charge less in certain areas:
- maybe a ride is already going that way
- maybe the pickup is on the opposite of the street so it takes longer
- maybe traffic is bad in that direction

What if Lyft was very transparent with the customer, "Hey, walk over here and save some money, or don't we don't care we already took it into account"

At the end of the day Lyft does have the necessary data to make that decision

### How-To Get a Lower Rate
You can get this cheaper rate by simply setting your potential pickup your location at a different address on your block or on an adjacent block. Yeah, it's really that easy. Check out the gif below that shows it in action. A video of the bug is also available at the bottom of this article.

<figure style='width: 30%' class='align-left'>
  <a href='/assets/posts/migrated-codehatcher-blog/lyft-bug.gif'><img src='/assets/posts/migrated-codehatcher-blog/lyft-bug.gif'></a>
  <figcaption>Lyft bug</figcaption>
</figure>

### Is this Really a Bug?
No...I mean yes... it kind of is. I suspect however Lyft is calculating the 'prime time' multiplier has the resolution down to an address not specific to the user. This means that whatever the radius is (or however they calculate the area with the multiplier) could have a boundary in your area giving the user incentive to search for these boundaries.
We are now talking about haggling with an app. Having to haggle means that you are:
1. Trying to spend more time finding the best price.
2. Not going to be satisfied when you don't get the opportunity to find a cheaper price.
3. Going to start considering your no hassle competitors.

People who have to haggle are generally less satisfied with their purchases vs someone who pays marginally more but is convinced a better deal was not available.


<iframe width="680" height="415" align="center" src="//www.youtube.com/embed/KFOZLP3UmU4" frameborder="0" allowfullscreen></iframe>