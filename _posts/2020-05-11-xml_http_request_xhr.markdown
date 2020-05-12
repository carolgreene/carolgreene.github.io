---
layout: post
title:      "XML HTTP Request (XHR)"
date:       2020-05-12 01:15:33 +0000
permalink:  xml_http_request_xhr
---


An XMLHttpRequest, also known as (XHR),  is a built-in browser object that allows us to make HTTP requests in JavaScript. It was invented by Microsoft in the early 1990's and was began to be used widely in the early 2000's for making asynchronous requests to API's.  

With the invention of XHR's, developers were able to update portions of a webpage without refreshing the whole page. Even though many people prefer the more current Fetch() method, it is good to be familiar with XHR's since they are often in older code and some developers still prefer to use XHR's.

It's easy to send an HTTP request using XHR. You just need to create the XHR object, open a connection to the URL you want the data from, and send the request.  Once the request is complete, the object will contain the response data and status code.

Here is an example of a simple XHR request:

First you need to create the XMLHttpRequest Object:
```
function loadCustomer(e) {
  const xhr = new XMLHttpRequest(); 
 
```
Then open the xhr connection passing in the type of request, the url, and if it's asychronous.

```
xhr.open('GET', 'https://yourUrl', true)
```

Once the request is ready, check that the status is ok, parse the response, and manipulate the data to get what you need.

```
xhr.onload = function() {
    if(this.status === 200) {
      const customer = JSON.parse(this.response)
      const output = `
      <ul>
         <li>Name: ${customer.name}</li>
        <li>Company: ${customer.company}</li>
        <li>Phone: ${customer.phone}</li>
      `;      
```

Then you can place it wherever you want in the DOM

```
  document.getElementById('customer').innerHTML = output
    }
  }
 
```

Just make sure to send the request to the server.

```
xhr.send()
}
```

One nice thing about XHR's is that you can access the state of the request by using xhr.readyState.

0- initial state
1- Open
2- Headers received
3- Loading
4- Done

This is really helpful if you run into a problem and need to know what stage the request is at.  Overall, this is an easy way to make asynchronous requests to an API and is good to know.










