---
title: "Faster Deploy with MeteorJS" 
excerpt: "Quickly deploy MeteorJS to your own provider or services like Digital Ocean."
categories:
  - DevOps
tags:
  - Javascript
  - programming
  - Meteor.js
  - DevOps
toc: true
toc_sticky: true
---
In this example we will talk about a quick deploy technique for MeteorJS apps. I recommend using Digital Ocean for this deployment example but any Nix based server should work.

#### Dependencies
I assume you already have npm installed. If you don't go ahead and get npm installed from here: http://blog.npmjs.org/post/85484771375/how-to-install-npm and then meet me back here

The beauty of MeteorJS is it is a very quick to develop against, so why shouldn't deployment be super easy as well. Some of the current tutorials out there are out of date and don't work properly. I have made this tutorial with that in mind to make sure it actually get's you a deployment without error.

##### Step 1: Spin up a server
Get a digital ocean account. I used a 512MB Ubuntu 14.04 64bit install with password. (It's better to use PEM but for this example to keep it simple we just will use the password emailed to us)

##### Step 2: Install and setup MUP on our local machine.
While your server is being provisioned install mup globally using `npm install -g mup`. Read more about mup here https://github.com/arunoda/meteor-up. After that is installed go into your root MeteorJS project directory and type `mup init`. You will find a `mup.json` in your project. I recommend adding this to your `.gitignore` file as it will contain sensitive information. Go ahead and open that file and fill in the fields (it's very well commented). Here is an example of what mine looks like. 
![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/mupjson_large.png)

##### Step 3: Configure our remote server.
For this example we are going to do a very basic setup. If you need SSL or any other more complex setup, check out the mup docs. They are pretty awesome.
After you SSH in to your server (using the username/password that was emailed to you) run the following to import the key for official MongoDB repo
`sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10`
and then to create the file list
`echo "deb http://repo.mongodb.org/apt/ubuntu "$(lsb_release -sc)"/mongodb-org/3.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list`
and then update our packages
`sudo apt-get update`
Now we are good to go back to our local shell to actually deploy

##### Step 4: Build and Deploy
Now comes the good part, let's build and deploy.
Go back to our local term and type `mup setup`. You'll see a setup like this when it has successfully completed.

 ![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/mupsetup_large.png)

Then go ahead and deploy to our remote server by typing `mup deploy`. You'll see something like this when it has successfully completed. 

![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/mupdeploy_large.png)

##### Step 5: Enjoy
Grab a tasty beverage and sit back and relax. Your deployment was easy like the way MeteorJS should be.