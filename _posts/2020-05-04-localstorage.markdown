---
layout: post
title:      "localStorage"
date:       2020-05-04 21:00:35 -0400
permalink:  localstorage
---


I've been working on creating small vanilla JavaScript apps to improve my skills and realized that without a backend database to keep track of my data, I needed a way to persist it in order to make my apps usable. I did a little research and found that localStorage was just what I was looking for. 

localStorage allows you to access a storage object in the browser and it does not expire until you clear it.  This means your data remains in storage even after you close your browser.  The keys and values in local storage are always strings, objects and integers will automatically be converted to strings.

localStorage is really easy to use and has the following methods:

1.  setItem()
2.  getItem()
3.  removeItem()
4.  clear()
5.  key()


**setItem(**)

This method allows you to store values in the localStorage object.

```
localStorage.setItem(tasks, JSON.stringify(tasks))
```

**getItem()**

This method allows you to access a value that is stored in the localStorage object.

```
localStorage.getItem(tasks)
```

**removeItem()**

This method allows you to remove an item from localStorage. If the item is not there to start with, the method will to nothing.

```
localStorage.removeItem(tasks)
```

**clear()**

This method clears out all items in localStorage. It does not take any parameters.

```
localStorage.clear()
```

**key()**

This method allows you to find the key name by passing in the index.

```
let keyName = localStorage.key(1)
```

It really is easy to use localStorage and is a great way to persist data in the browser when you have a vanilla JavaScript app with no backend database. It's certainly doesn't take the place of a full database, but is a great tool to have.


