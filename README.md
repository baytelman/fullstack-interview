# Goodtalk • Interview • Letters game!

## Create a React JS or React Native app

- Choose whatever would be easier/faster for you – React JS or React-Native.
- You can use any boilerplate or start project. If you need help with this, let us know and we will share a quick-starter project promptly.
- Keep your code separated from the boilerplate, so it's easier to review your work.

### The app

- Our game will present a board with 16 tiles (4x4) in the center of the screen.
- Each tile has a letter read from a given json file (see `test-board-1.json`).
- The user can select tile by clicking/tapping them.
- At the bottom of the board, display the word formed by the selected tiles.
- Add a button `(x)` to reset the board, deselecting all tiles and clearning the word.

#### Example

In the following example, the initial board presents the content of the test json file, and has no tile selected. There's no formed word either. The reset button is disabled.

Then, the user clicks the F tile, which gets selected. The formed word is now `F`. The reset button is now enabled.

The user selects the A tile by clicking it. The formed word is now `FA`. Finally, the user selects the N tile. The formed word is now `FAN`.

If the user clicks the reset button, the board is reset.

```
          	x                  (x)                 (x)                 (x)
 A  B  C  D          A  B  C  D         [A] B  C  D         [A] B  C  D
 E  F  G  H          E [F] G  H          E [F] G  H          E [F] G  H
 I  J  K  L          I  J  K  L          I  J  K  L          I  J  K  L
 M  N  O  P          M  N  O  P          M  N  O  P          M [N] O  P
        
[          ]        [ F        ]        [ FA       ]        [ FAN      ]
```

---

## Submitting your work 

Your deliverable should satisfy all these requirements:

- Explain if you are responding Part 1 (frontend), Part 2 (backend) or both (fullstack).

- It should be submitted using the following alternatives:
    1. bitbucket.org or github.com PRIVATE repo (*Note: Do NOT use a public repo because other candidates could copy your response*).
    1. Upload a compressed file somewhere and send us the URL.
    1. Email us your code (*Note: Do NOT include `node_modules` or any files we can generate ourselves*).

- It should be include instructions on how to run (installing dependencies, starting it, etc) and shouldn't have any weird environment requirements.


---

## Part 1
*Only if you want to be considered for Frontend / Fullstack*

### Required

Implement all the interactions described in sections "The app" and "Example".

### Choose 3 (and only 3) features

Don't try to satisday all of them. We need to understand what are you *most comfortable with* as part of your evaluation, so choose whatever is the easiest/simplest/fastest for you!

Your deliverable should satify 3 of the following requirements:

- Use responsive display – Look amazing in mobile and desktop (ReactJS only)
- Use fancy animations.
- Deselect tiles, so you can enter [T][R][A][P] and then remove the [R].
- Validate if the word is contained in a `dictionary.json` file.
- Only allow neighbor tiles to be selected sequentially.
    - In the example, `B C G` would be legal and `F A N` would not. 

---

## Part 2
*Only if you want to be considered for Backend / Fullstack*

### Required 

Pretend you are creating the backend for our game's lightweight client app, and that all logic will be performed at the server level.

Implement a server using Node (ideally using Express, but other frameworks would work) to serve the following endpoints:

- Serve the static files (`board.json` and `dictionary.json`) via GET methods.
- Validate a user's answer (entry) via POST method:
    - The body of the request should be a JSON including the index/location of the tiles.
    - Check the word formed with the given tiles exists in the dictionary file.
    
### Choose 2 (and only 2) features

Don't try to satisday all of them. We need to understand what are you *most comfortable with* as part of your evaluation, so choose whatever is the easiest/simplest/fastest for you!

Your deliverable should satify 3 of the following requirements:

- Modify your validation only allowing neighbor tiles to be selected sequentially.
    - In the example, `B C G` would be legal and `F A N` would not.  
- Shuffle the tiles when your server starts, confirming that at least one of the words of the dictionary can be formed. Then, serve the modified board.
- Add a player id to the validation request, keeping track of how many valid words each player has submitted. Add an endpoint to expose these scores.
- After successful validation, store the entry in a database and add to your response if the entry existed previously.

## Thanks for your time!
The Goodtalk team!