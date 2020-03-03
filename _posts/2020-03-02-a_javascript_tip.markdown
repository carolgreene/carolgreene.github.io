---
layout: post
title:      "A JavaScript Tip"
date:       2020-03-03 01:56:30 +0000
permalink:  a_javascript_tip
---


I've been busy reviewing different parts of the curriculum by working on small projects. This week I decided to create a Tip Calculator app in vanilla JavaScript. It was fun getting the HTML set up to display the calculator and to get my event listener going to listen for the click to calculate the tip. 

Everything was going smoothly and I felt good about refreshing my memory on these skills. The calculator was working perfectly until I decided to check it using a bill that wasn't just a whole  number.

That's when my program broke. My program was not set up to handle decimals. It calculated the tip as if the bill was just the whole number. I did some research online, looking at Stack Overflow hoping that there was a currency setting I could use. As it turns out, there was no currency setting. Different people had different ideas for fixes. I decided to use the following when I set up my HTML for my bill.

 `<div class="form-group">
                <label>Enter amount of bill</label>
                <input type="number" step=0.01 min=1 class="form-control" id="bill_amount">
            </div>`
						
I set up the step at .01 to handle denominations down to the penny.  Once I did that, I didn't get an error any more when I entered in the bill, however, my calculations still weren't working right.  I ended up setting up my code in index.js to use the bill amount in cents instead of dollars with a decimal.

`const billAmountCents = document.getElementById("bill_amount").value * 100``

```
This enabled me to get my calculations done correctly. Once I calculated the tip amount, I then converted the bill amount to dollars & cents & added it to the tip amount to get the total due.

```const tipAmount = (billAmountCents * (percent/100))/100  
  const calculatedTotalDue = ((billAmountCents/100) + tipAmount).toFixed(2)

```
I used .toFixed(2) to set it to just 2 decimal places. Once I had these figures, I just returned & displayed the total due. This was a great exercise to go through to help me understand the inner workings of my program.  I'm looking forward  to refactoring it further to clean it up some more & then adding some additional CSS to make it look better. After that it's on to my next project!


