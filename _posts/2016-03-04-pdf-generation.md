---
title: "Mobile App PDF generation from HTML" 
excerpt: "Client side generation of PDFs using jsPDF, HTML, DataURIs, and Cordova on iOS8+ and Android in MeteorJS"
categories:
  - Programming
tags:
  - Meteor.js
  - Javascript
  - iOS
  - jsPDF
  - Android
toc: true
toc_sticky: true
---
We want to be able to generate an PDF document from HTML without needing direct processing by the server such that it is presented to the client in the Cordova app with a **done button**. This allows the user to generate a pdf, view it, and then close it and return to the app. I'll take a MeteorJS specific approach but it's very applicable to any Cordova ENV.

There are multiple ways to accomplish this but all I have seen rely on at least one of the below. We won't rely on any.

1. Generate a PDF file on the server.
2. Send a PDF file from the server to the client.
3. Open the PDF file in an external reader (specifically, `https://docs.google.com/viewer?url=`)
4. Saving file to iOS device before viewing it.

Yes, i'm excited to show you.

![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/excited_large.gif){: .align-center}

## 1. Install the proper plugins (InAppBrowser, jsPDF)
We will install the [InAppBrowser](https://github.com/apache/cordova-plugin-inappbrowser) plugin since it has been removed since Cordova 3.0ish and we are using Meteor 1.2.X which uses Cordova 5.0ish. This will allow us to control how the client views the PDF.

```javascript
meteor add cordova:cordova-plugin-inappbrowser@1.1.0
```

We will also install [jsPDF](https://github.com/MrRio/jsPDF). The [documentation](https://mrrio.github.io/jsPDF/doc/symbols/jsPDF.html) is horrible, hidden and possible old but there is a decent [examples](http://mrrio.github.io/jsPDF/) page. Go ahead and git clone that into whatever directory works for your env.

## 2. Generate the PDF
There are many ways to use jsPDF to generate a PDF. I want to use the HTML renderer because I am already showing my user similar information in the app and just want to give them a way to view a PDF which they can save for later or send to other users.
We are going to generate the PDF as a data URI string. This means the content of the PDF will all be in a URI. Here is some more [information](https://developer.mozilla.org/en-US/docs/Web/HTTP/data_URIs) on it as well as sites that will [generate data URIs](http://dopiaza.org/tools/datauri/index.php) for you to play with.
There will be some limitations with this (mainly with old version of IE, because that's where the limitations always lie...)
Here is how we will generate the data URI (`var uri`) from my HTML elements, specifically my cleverly named #pdf id selector while ignoring anything in my #nothing selector.

```javascript
    var doc = new jsPDF();
    var specialElementHandlers = {
      '#nothing': function(element, renderer){
        return true;
      }
    };
    var elementToRender = $('#pdf').get(0)
    doc.fromHTML(elementToRender, 15, 15, {
      'width': 200,
      'elementHandlers': specialElementHandlers
    });
    var uri = doc.output('datauristring');
```

## 3. Show the PDF file to the user
Time to show the user, we will use the InAppBrowser plugin with the correct target. You can check that page for more info but basically like this.For this example I am hiding the location bar to give the user a slightly cleaner experience.

```javascript
window.open(uri, '_blank', 'location=no');
```

Our final product will look like this. Not an amazing design but very usable.

![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/Screen%20Shot%202015-12-04%20at%2017.53.20_medium.png){: .align-center}

That's it! Good job everyone!

![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/goodjobguys_large.gif){: .align-center}


