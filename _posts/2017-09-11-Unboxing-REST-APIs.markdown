---
layout: post
title: Unboxing REST APIs 
comments: true
---
What do the terms API and REST mean and why they are so important.

<img class="no-shadow" alt="REST APIs" src="/Front/assets/img/2/rest-api.jpg" style="width: 60%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>Source: b2evolution.net</em></p>

### **APIs: Connecting Applications**

If you've been doing web development for a while, or starting to get into, you might have come across the terms like API and REST. API stands for **Application Programming Interface** and it enables multiple applications to share data with each other for a *seamless* user experience. 

That definition sounded quite bookish, here's a more relatable example.

Surabhi bakes delicious cookies. She prepares the finest cookie dough, adds choco chips and voila! Her friend Bruce wants to bake his own peppermint cookies but his dough is just not upto the mark. So Bruce asks Surabhi for her dough and prepares his perfect crunchy peppermint cookie. This is exactly what an API does. Surabhi's dough (API) enables other chefs (developers) like Bruce to *piggyback* and create new cookies (applications) without reinventing the wheel.  

<img class="no-shadow" alt="API usage" src="/Front/assets/img/2/api-usage.png" style="width: 60%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>Piggybacking on an existing application to create a new one</em></p>

APIs can be of various types but the one we will focus on is the Web (or HTTP) API, for exchanging data between multiple web applications. Some real life examples of HTTP APIs:

* Yelp uses [Google Maps API](https://developers.google.com/maps/) to display the locations of your favorite restaurants!

* Google uses [The Weather Channel](https://www.wunderground.com/weather/api) API to display the weather.

* The Weather Channel uses the [Geolocation API](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation/Using_geolocation) to fetch your coordinates from the browser and show the local weather.

We see that disparate organizations use each other's APIs to build their own products. APIs help establish the groundwork so that the organizations can focus on their actual products. 

It might seem that only the consumer benefits from the APIs but in reality, it works both ways. Facebook introduced the Graph API so that other developers can build applications centered around Facebook, thus bringing more users to them. Organizations such as Uber, Lyft and TripAdvisor pay a hefty sum to Google for consuming the Maps API. 

### **HTTP APIs**

Before we go behind the scenes, let's define some important terms.

* **HTTP:** Unsurprisingly, Web APIs work in a request-response mode. The client requests the HTTP server for data and the server (iff the request was successful aka 200) sends it back in JSON/XML.

* **Resource:** The nouns, the representation of objects. The location of restaurants and the weather in the previous examples are nothing but resources.

* **URI:** The path where the resource can be located.

Now, let's say we have an application to manage the student records in a class. We can then **view**, **add**, **edit** or **delete** a student record, as in a CRUD application.

```
http://myschool.com/class1/view_record?name=Bruce
http://myschool.com/class1/add_new_record?name=Thomas
http://myschool.com/class1/edit_record?name=Martha
http://myschool.com/class1/delete_record?name=Bruce
```
This works fine but the problem arises when everyone starts implementing their own APIs. For instance, `/view_record?name=Bruce` can also be defined as `/records/Bruce`.

Enter REST.

### **REST: Standardizing APIs**

REST stands for **RE**presentational **S**tate **T**ransfer and was first coined by [Roy Fielding](https://en.wikipedia.org/wiki/Roy_Fielding). REST reflects the principles of a well-designed web application where we have a **resource** (noun) upon which we can take certain **actions** (verbs) by going to suitable **path** (URI).

Let's rewrite our student example in a RESTful way, using the HTTP verbs (GET, PUT, POST, DELETE and some [others](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)).

Get all records:
```
GET http://myschool.com/class1
```

Get a specific record:
```
GET http://myschool.com/class1/Bruce
```

Add a new record:
```
POST http://myschool.com/class1/Thomas
{
	"Age": "20",
	"Location": "USA"
}
```

Edit a record:
```
PUT http://myschool.com/class1/Thomas
{
	"Age": "22"
}
```

Delete a specific record:
```
DELETE http://myschool.com/class1/Bruce
```

Evidently, a much better way to read and write data over the web.

Another important part of REST is to respond with the correct status code at the time of the request. Here's a quick refresher of HTTP codes:

* 2xx = Success
* 3xx = Redirect
* 4xx = Client-side error
* 5xx = Server-side error

A REST API should ideally respond with the requested data in case of 2xx and an error message in case of 4xx/5xx.

<img class="no-shadow" alt="Client-Server model" src="/Front/assets/img/2/client-server.png" style="width: 60%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>Server returns an error as there's no resource named Tom</em></p>

### **Securing APIs**

A question you might be wondering is that what if anyone could `GET`, `PUT`, `POST` or `DELETE`? In the previous example, anyone could goto the URI and change the records, but in real life, the access to read (or write) through an API is provided only after proper authentication.

[OAuth](https://en.wikipedia.org/wiki/OAuth) is one such widely used security standard that allows a user to access resources on a server by issuing access tokens (keys). More security practices for APIs can be found [here](https://www.owasp.org/index.php/REST_Security_Cheat_Sheet).

### **Furthermore**

Hope this brief introduction will get you started with REST APIs. Here are some additional resources:

* A nifty [video](https://www.youtube.com/watch?v=s7wmiS2mSXY) explaining APIs in general. 
* An [application](http://www.rahulxsharma.com/MyMoviePoster/) I built long ago to fetch movie posters using the [TMDb API](https://www.themoviedb.org/).
* [Designing RESTful APIs](https://www.udacity.com/course/designing-restful-apis--ud388) by Udacity.




