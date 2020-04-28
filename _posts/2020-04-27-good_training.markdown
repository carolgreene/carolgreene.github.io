---
layout: post
title:      "Good Training"
date:       2020-04-28 01:19:22 +0000
permalink:  good_training
---


I've been working on some of the newer JavaScript lessons that were added after I completed that section in order to improve my skills.  This past week, I did the Pokemon Teams Project. It was  a really good exercise that had no tests, just goals of what the completed project would do.  It had cards for each Pokemon Trainer that included their name and the Pokemon on their team. You could add and delete the team members as long as the trainer had no more than 6 Pokemon on their team.  

Once I fetched the trainers, I had to iterate through the trainers and pass each one to a renderTrainerCard function to make their cards.  I've listed this function and the steps I followed below.

I broke this function apart into several steps to help me figure out how to create the cards.

The first thing I did was to create the elements for the card:

```
function renderTrainerCard(trainer) {
  let main = document.querySelector('main')
  let div = document.createElement('div')
  let p = document.createElement('p')
  let addBtn = document.createElement('button')
  let trainerUl = document.createElement('ul')
```

Once the elements were created, I set the attributes that the elements needed, giving each card a data-id of the trainer.id. I also added a data-trainer-id equal to the trainer.id to the button that I was using to add a Pokemon to the trainer's team. I also needed to have a data-trainer-ul equal to the trainer.id so I'd have that available to append the li's to it.

```
  div.setAttribute("class", "card")
  div.setAttribute("data-id", `${trainer.id}`)
  addBtn.setAttribute("data-trainer-id", `${trainer.id}`)
  trainerUl.setAttribute("data-trainer-ul", `${trainer.id}`)
```

I then added the text that would show at the top of the card and the button:

```
  p.innerText = `${trainer.name}`  
  addBtn.innerText = "Add Pokemon"
```

Then appended all of the children to the div and the div to main:

```
  div.appendChild(p)
  div.appendChild(addBtn)
  div.appendChild(trainerUl)
  main.appendChild(div)
```

I then iterated through the pokemon on the team and passed each one to my renderPokemon function to list them.

```
 trainer.pokemons.forEach(pokemon => {
    renderPokemon(pokemon, trainerUl)
  })
```

Once my pokemon were rendered, the program comes back and adds an event listener to the addPokemon button and passes it to the addPokemonToTeam function, passing in the trainer.

```
 addBtn.addEventListener("click", function(e) {
    addPokemonToTeam(trainer)  
  })
}
```

After this, I worked through the rest of the lab and have a much clearer understanding of using JavaScript to render cards in the DOM.

