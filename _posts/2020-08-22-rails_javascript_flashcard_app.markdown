---
layout: post
title:      "Rails/JavaScript Flashcard App"
date:       2020-08-22 17:08:42 +0000
permalink:  rails_javascript_flashcard_app
---


Lately I've been working on an app called Code Card. It's a flashcard app with a Rails api backend and a vanilla JavaScript frontend. I wanted to have  a centralized place to keep study questions that I could easily go over and I figured putting it in an app would be a good way to improve my coding skills and practice the concepts of the different languages.

I designed  a simple Rails api with a User, Deck, and Card models. Users can sign in, create a deck, and then add cards to their deck. They can then choose a deck to quiz themselves. When the user clicks the button to pick a deck, it calls the fetchDecks() function which then calls the renderDeck() function.

```
function fetchDecks() { 
  fetch(`http://10.0.0.99:3000/api/v1/decks`)
  .then((res) => res.json())
  .then(results => {  
    decks = results  
    renderDeck()      
  })
}

function renderDeck() {  
  main.innerHTML = ''   
  decks.forEach(deck => {   
    
    let div = document.createElement('div')
    let p = document.createElement('p')
    let pickDeckBtn = document.createElement('button')
    let deckUl = document.createElement('ul')

    div.setAttribute('class', 'card')
    div.setAttribute('data-id', `${deck.id}`)
    pickDeckBtn.setAttribute('data-deck-id', `${deck.id}`)    
    deckUl.setAttribute('data-deck-ul', `${deck.id}`)

    p.innerText = `${deck.name}`
    pickDeckBtn.innerText = "Pick this deck"

    div.appendChild(p)
    div.appendChild(pickDeckBtn)
    div.appendChild(deckUl)
    main.appendChild(div)  

    pickDeckBtn.addEventListener("click", function(e) { 
      e.preventDefault()     
      chooseDeck(deck)
    })
  })
```

The program fetches the decks from the backend and places the results in the decks variable that I set up earlier. In the renderDecks() function, I iterate through the decks variable and then set up the DOM elements to display each deck. I set the class to 'card' so each deck would display as a card and made sure to add a data attribute for deck-id to the deckUl and the button to pick a deck. I appended the elements I created to the main element and added an event listener to listen for a click on the pickDeckBtn. Once this is clicked, it will bring the user to the deck that they clicked by calling the chooseDeck(deck) function.

```
function chooseDeck(deck) {
  main.innerHTML = ''
  
  let div = document.createElement('div')
  let h2 = document.createElement('h2')
  let addCardBtn = document.createElement('button')
  let quizBtn = document.createElement('button')
  
  h2.innerText = deck.name  
  addCardBtn.innerText = 'Add Card'  
  quizBtn.innerText = 'Quiz Yourself'

  main.append(div, h2, addCardBtn, quizBtn)

  addCardBtn.addEventListener('click', function(e) {
    addCard(deck)
  })
	
	quizBtn.addEventListener('click', function(e) {
   quizYourself(deck)
  })
}
```

The chooseDeck() function first clears the DOM and then creates the elements needed to display the deck name and 2 buttons, giving the user the option of adding a card to the deck or quizzing themselves. I've added event listeners for each of these options, which will then call the appropriate function.

This project has been a lot of fun to work on. I wrote out a basic plan before I started coding, but I've been fine-tuning as I've been working through it in the browser to improve the UX.  I've gotten through running the quiz, adding additional decks and cards, and finishing a deck and will be working on editing and deleting cards and decks next. Once it's fully functional, I'm going to spend some time on the layout to improve the appearance and functionality. I'll do another blog on this once these are completed.
