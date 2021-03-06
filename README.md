

# Bug Of the Week – BOW

This repo is to document the BOW for the Junior and Senior Cohorts:
* Juniors HRSF 116-117
* Seniors HRSF 113-114



## Juniors

### Week 2

Welcome to your one and only... **Bug Of the Week**! (BOW) This is something new we’re starting with the cohorts, where once a week on Fridays or Saturdays I’ll be posting what the general bug or challenge of the week was. Btw, feel free to Slack me recommendations next week.

This week’s bug of the week was….. (drum roll)…

**The `this` binding during BlinkyDancer!** We noticed some struggling with the `this` binding but don't worry.. we've all gone through it while learning JavaScript. So, I highly recommend reading up on the `this` binding info in the lecture slides and making sure you know how `this` is interpreted in each of the cases when,


1. It refers to whatever’s to the left of the call-time dot
```javascript
const person = { 
   name: 'Jon',
   lastname: 'Snow',
   printName: function(o) { 
      console.log(this.name + ' ' + this.lastname); 
   },
};  
person.printName(); // logs 'Jon Snow'
```

2. It refers to the window object. E.g.
```javascript
console.log(this); // logs window in the browser
var x = 10;
console.log(this.x); // logs 10 in the browser
```

3. It refers to a new instance of a constructor function.
```javascript
let Car = function(name, model) {
  // this = Object.create(Car.prototype);  <— super important line to remember, this line is omitted but assumed to be there, same as the last line inside this function body
  this.name = name;
  this.model = model;
  // return this; <— this line is also omitted but assumed to be there
};
let lambo = new Car('Lamborghini', 'Murcielago');
```

Finally, there are cases when `this` is forced to be something. This is when we use `call`, `apply`, and `bind`. If you’re up for the challenge, try implementing `Function.prototype.bind` from scratch using `call` or `apply` as helper functions.


[Here’s a good resource to read](https://medium.com/quick-code/understanding-the-this-keyword-in-javascript-cb76d4c7c5e8)


Enjoy the rest of your day everyone!


### Week 3

Good evening everyone, @channel

Hope everyone is enjoying the CRUDdy Todo Sprint, it’s definitely an interesting one! Since I was away last week, I wasn’t able to send out the **Bug Of the Week**. So here it is!

Last week’s **BOW** was the **client-server architecture**!

It turns out, in its simplest form, the internet is based on client-server communications where servers serve (duh) many simultaneous users with website and all sorts of data. ([Source](https://www.techopedia.com/definition/438/clientserver-architecture).

**Client-server architecture has various forms**. However, the most important architectural style that’s most widely used in the web is **RESTful client-server interfaces** ([Source](https://en.wikipedia.org/wiki/Representational_state_transfer)). Think of a RESTful API as a **service** to which requests can be made. RESTful APIs support (at least) **GET**, **PUT**, **POST** and **DELETE** HTTP requests. These are the types of requests you worked with last week and will continue working on this week. Furthermore, so much backend work is developing RESTful web APIs for web services that there are thousands of Software Engineers that work at all kinds of companies developing APIs. They’re really important.

For example, querying the **Google Books API** (https://www.googleapis.com/books/v1/volumes?q=isbn:9780330316118) with this ISBN number – 9780330316118 – returns back a bunch of data from the Hitchhiker’s Guide To The Galaxy book. Software Engineers made that API respond to GET requests with an ID representing the ISBN. **When we talk about the API, we usually refer to the entire URL https://www.googleapis.com/books/v1**, and depending on what query string parameters you pass to the API (i.e. `volumes`, `q`, `isbn`), it will query the service’s database accordingly and respond with the appropriate data.

**Try querying this API with other ISBNs!** https://www.googleapis.com/books/v1/volumes?q=isbn:INSERT_ISBN_HERE

For more resources, feel free to send me a Slack message and I can point you in the right direction!

Have a good night everyone! 


### Week 4

Hi Juniors! @channel

Hope everyone’s week is going great! It’s time for the **BOW**!

This week we had two **BOWs**: 
1. Understanding callbacks (due to the **callback hell** confusion)
2. Understanding Node.js error-first callback pattern


**I. What is a callback?** 
According to Wikipedia (source: https://en.wikipedia.org/wiki/Callback_(computer_programming)), a callback is any executable code – e.g. a function – that is passed as an argument to other code that is expected to **call back** (execute) that argument at a given time. 

It’s important to note that **a callback doesn’t have to do with asynchronous behavior**. It does, however, have the nice property to it that it gets executed by another piece of code, which means that they’re perfect for asynchronous behavior since they can be passed into functions that behave asynchronously. When the asynchronous behavior is completed, it can pass data to a callback. This way, we don’t have to worry about when the data will be received, as we will know that at some future point it will be taken care of.

The problem with callbacks is – as you all experienced – that they can get messy and hard to follow once you have many layers of them. One can easily lose track of which callback was supposed to do what, and what data was passed in where, etc…

For this reason, promises were added to JavaScript. I highly recommend reading more about them here https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise. They’re very useful.

Finally, for fun and when you have some free time, read up on what `Promise.all` does and think of a way that you could implement it. More info about it here (https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)


**II. Error-first Callback Pattern**
Now, about the **Node.js error-first callback pattern**, the most important thing you should note is that it’s only a style of callbacks. It’s a pattern, a very useful one though. There are several articles that are worth reading about it: 
*  https://30secondsofinterviews.org/ (Cmd + ‘F’ + ‘error’)
* http://fredkschott.com/post/2014/03/understanding-error-first-callbacks-in-node-js/


Hope this was helpful! Enjoy the rest of your day!



## Seniors

### Week 7

This week’s bug of the week was….. (drum roll)…

**Proxy servers!** It seemed like a lot of people had issues with hooking up their teams' individual microservices with the proxy server, so here are a few resources that I found that can help to understand this concept.

**What is a proxy server?**
From [Wikipedia](https://en.wikipedia.org/wiki/Proxy_server), a proxy server is a server that acts as an intermediary for requests from clients seeking resources from other servers. A client connects to the proxy server, requesting some service, such as a file, connection, web page, or other resources available – in your cases, a specific micro service’s resources – from a different server and the proxy server evaluates the request as a way to simplify and control its complexity. Proxies were invented to add structure and encapsulation to distributed systems.

**Why do we need this?**
Well, turns out there are multiple ways of architecting web applications. A microservice-oriented architecture is one of those ways, and I believe the most commonly used. *I know for sure Uber and Airbnb are microservice oriented apps.*

**Benefits of microservice-oriented applications:**
“Microservice architectures are typically better organized, since each microservice has a very specific job, and is not concerned with the jobs of other components. Decoupled services are also easier to recompose and reconfigure to serve the purposes of different apps (for example, serving both the web clients and public API).” ([Source](medium.com/javascript-scene/10-interview-questions-every-javascript-developer-should-know-6fa6bdf5ad95)  — Question 9)

**Microservice oriented architectures achieve the following:**
* Unlimited ability to scale horizontally
* Separation of concerns
* Better organization of your web services
* There are many other pros, these are just the basics

**Here are some of my teammates’ implementations of their own proxy servers if you wanna check them out:**
* https://github.com/Quesarito/product-proxy/blob/master/proxy/server.js
* https://github.com/Quesarito/reviews-proxy/blob/master/proxy/server/index.js



### Week 8

SDC is rolling, and so is the data generation for your projects! Here comes your favorite part of the week (after TPQAs, of course)…

The BUG of the week! **BOW!**

We noticed this week the BOW has to do with data generation. Specifically, JavaScript heap running out of memory or the JavaScript runtime executing very slowly once the data generated is at the ~4-5 million marks.

However, you all figured it out. Using the `drain` event allows for the writeStream buffer to be emptied and not overflowed.

Here’s a great article on StackOverflow explaining this. In [this article](https://stackoverflow.com/questions/18932488/how-to-use-drain-event-of-stream-writable-in-node-js), there’s also an implementation. 



### Week 9

Good evening everyone,

It seems like there weren’t that many help desk tickets (*woohoo autonomy!*) last week from both senior cohorts. However, I want to share some resources that I found very useful when I was going through SDC and was scaling my micro service, to further understand some important concepts in system architectures.


**What is SSH?** I thought some of you would find useful to know what SSH is and what it means to SSH into an EC2 instance. I.e. connect to a remote computer securely and have access to the computer’s command line. ([More info](https://searchsecurity.techtarget.com/definition/Secure-Shell))


**What is Load Balancing?** In particular, 3 types of Load Balancing algorithms that you can read more in depth about are mentioned. ([More info](https://www.nginx.com/resources/glossary/load-balancing/))


**What is Redis caching?** For a further “fun” challenge, think about how you would implement a cache – a hashmap of keys and values – that supports setting an expiration time to each element as it’s added to the cache. It’s an interesting question similar to the LRU Cache and if anyone wants to talk about it in more detail, feel free to ambush me tomorrow or Wednesday. ([More info](https://codeburst.io/redis-what-and-why-d52b6829813))


Have a good night everyone!



### Week 10

Hello Seniors! @channel


I believe you are all done with SDC! Congrats said the bats and the cats!

Now, for your second favorite part of the week – TQPA is first, of course – the **BOW**! This week’s **BOW** is… **configuring EC2 instances to connect to the right IP and Port addresses of your other instances!** 

I’m sure a lot of time this week was spent configuring EC2 instances to run [daemons](https://en.wikipedia.org/wiki/Daemon_(computing)), such as Redis, Postgres, Mongod – mongo daemon –, etc. But before this, before these background processes can run and function appropriately, you had to specify in the configuration files for the programs to send requests to another EC2s, and you also had to specify what ports they accept requests from.


So let’s look into these steps a bit further and see what and why.

1. Each EC2 instance that you set up has a unique public and private IP address. For now, we’ll focus on the **public IP address**. The public IP address is something like 127.0.0.1 (<– this is localhost) or 84.52.220.193. They also have public DNS hostnames such as ec2-203-0-113-25.compute-1.amazonaws.com.


2. You can access this EC2 instance (and thus its services) by sending requests to that public IP address from anywhere that you have access to the internet and that’s not banned from the AWS network. So, pretty much everywhere in the world. 


3. You should allow requests at certain ports to be made (example ports: 80 – default, 443 – for https, 27017 – MongoDB default port, etc.). ([More info here](https://en.wikipedia.org/wiki/Port_(computer_networking))).


4. Once this is all set up, that is, (1) you have the IP addresses of your EC2 instances and what each of them is responsible for – caching, database, server, etc. –, (2) you open up those ports in the EC2 console to allow for requests and connections of certain types to be made to those ports, and (3) you explicitly specify these EC2 IP addresses and open port numbers, then you can run the programs such as MongoD, Redis, Postgres, Nginx, etc. and test whether the requests that are sent are running smoothly, and whether everything is working properly.


So, this was more of a recap of how these components fit into a bigger picture, and how everything works out. 


More info about AWS EC2 [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-instance-addressing.html)


For further exploratory research into system design, here are some resources that I’ve used quite a lot for preparing for interviews. 
  - YouTube channels that I highly recommend: https://www.youtube.com/watch?v=vvhC64hQZMk, https://www.youtube.com/watch?v=U0xTu6E2CT8, https://www.youtube.com/watch?v=fMZMm_0ZhK4&t=4s
  - Reading: https://github.com/donnemartin/system-design-primer
  - Pramp.com System Design Interviews
