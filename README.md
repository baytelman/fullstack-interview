# Enara Health • Fullstack Interview • Letters game!

*Version 1.3*

## This is a coding challenge for applicants interested in joining Enara Health.

[Full job description](http://bit.ly/2lCAJR7)

We ask you to *read this file carefully* **before** you begin writing a solution. 
There is a Q&A and an example section at the end of the file, which may help you to complete this challenge faster.

If you decide to continue with this process, **first, send us a message telling us WHAT DAY** you expect to submit your solution. 
This is really important so we can better arrange to wait for you, specially if you want to take a little bit longer. 

If you decide NOT to continue with this process, let us know! ... So we don't keep sending your reminders.

We sincerely thank you for your interest and your time.

Best, 
The Enara Health team!

## Create a React JS or React Native app

- You can use any boilerplate or start project. If you need help with this, let us know and we will share a quick-starter project promptly.
- Keep your code separated from the boilerplate, so it's easier to review your work.
- We prefer TypeScript or typed JavaScript.

### The app

- Our game will present a board with 16 tiles (4x4) in the center of the screen.
- Each tile has a letter read from a given json file (see [`test-board-1.json`](files/test-board-1.json) and [`test-board-2.json`](files/test-board-2.json)).
- The user can select tile by clicking/tapping them.
- At the bottom of the board, display the word formed by the selected tiles.
- Add a button `(x)` to reset the board, deselecting all tiles and clearing the word.

#### Example

In the following example, the initial board presents the content of the [test json file 1](files/test-board-1.json), and has no tile selected. There's no formed word either. The reset button is disabled.

Then, the user clicks the F tile, which gets selected. The formed word is now `F`. The reset button is now enabled.

The user selects the A tile by clicking it. The formed word is now `FA`. Finally, the user selects the N tile. The formed word is now `FAN`.

If the user clicks the reset button, the board is reset.

```
              ( )                 (x)                 (x)                 (x)
    A  B  C  D          A  B  C  D         [A] B  C  D         [A] B  C  D
    E  F  G  H          E [F] G  H          E [F] G  H          E [F] G  H
    I  J  K  L          I  J  K  L          I  J  K  L          I  J  K  L
    M  N  O  P          M  N  O  P          M  N  O  P          M [N] O  P
            
   [          ]        [ F        ]        [ FA       ]        [ FAN      ]
```

---

## Submitting your work 

Your deliverable should satisfy all these requirements:

- Explain if you are responding Part 1 (frontend), Part 2 (backend) or both (full stack). Part 3 is required for both types of roles.

- It should include *instructions on how to run* (installing dependencies, starting it, etc) and it shouldn't have any obscure environment requirements.

- It should be submitted using one of the following alternatives:
    1. bitbucket.org or github.com PRIVATE repo (*Note: Do NOT use a public repo because other candidates could copy your response*).
    1. Upload a compressed file somewhere and send us the URL.
    1. Email us your code.
    - *Note: Do NOT include `node_modules` or any other files that will be auto-generated*.

---

## Part 1
*If you want to be considered for Full stack (Backend + Frontend), answer both Parts 1 and 2. If you are only interested in a Backend position, skip this part. *

### Required if applying to Full Stack or Front End positions

Implement all the interactions described in sections "The app" and "Example".
- Choose whatever would be easier/faster for you – React JS or React-Native.
- Make it look like the following designs:
	- ReactJS only: Use *responsive* display for mobile and desktop.
	
	- Implement styles using exclusively CSS, not images.

	- Layour for mobile media:

		![Mobile dimensions.](./files/mobile.png)

	- Layout for desktop media (ReactJS only):

		![Desktop dimensions.](./files/desktop.png)

	- Although element size is different on each media, use the styles/colors above for valid/invalid cases.

- Deselect tiles, so you can enter [T][R][A][P] and then remove the [R].
- Validate if the word is contained in a [`dictionary.json`](files/dictionary.json) file. You should use our [secondary board file](files/test-board-2.json), which contains many words from the dictionary!

---

## Part 2
*If you want to be considered for Full stack (Backend + Frontend), answer both Parts 1 and 2. If you are only interested in a Frontend position, skip this part. *

### Required if applying to Full Stack or Back End positions

Pretend you are creating the backend for our game's lightweight client app, and that all logic will be performed at the server level. 

This part is independent from Part 1: Do not modify your solution for Part 1.

Implement a server using Node (ideally using Express, but other frameworks would work) to serve the following endpoints:

- Load the content of [`board.json`](files/test-board-1.json) and shuffle the tiles when your server starts. Serve the shuffled board via GET method.
- Serve the file [`dictionary.json`](files/dictionary.json) statically via GET methods.
- Validate a user's answer (entry) via POST method:
    - The body of the request should be a JSON including the index/location of the tiles.
    - Check the word formed with the given tiles exists in the [dictionary file](files/dictionary.json).
    
### Choose 2 (and only 2) features

Don't try to satisfy all of them. We need to understand what are you *most comfortable with* as part of your evaluation, so choose whatever is the easiest/simplest/fastest for you!

Your deliverable should satisfy 2 of the following requirements:

- Modify your validation only allowing neighbor tiles to be selected sequentially.
    - In the example, `B C G` would be legal and `F A N` would not.  
	- During server starts, confirm that at least one of the words of the [dictionary](files/dictionary.json) can be formed with your shuffled board.
- Add a player id to the validation request, keeping track of how many valid words each player has submitted. Add an endpoint to expose these scores.
- After successful validation, store the entry in a database and add to your response if the entry existed previously.

---

## Part 3 – Required for all applicants

Pretend a co-worker from your current job (clearly not at Enara Health!) submitted the following code. Imagine all external libraries and functions exist and do whatever they are supposed to do.

- List the most severe problems or improvements opportunities within the following code, listing the worst first.

- What process would you suggest to your team in order to address these issues?
 
```
const MyServer = require('../../../aug2018/MyServer'); 
import { MyUtility } from './shared_utils/MyUtility';
const StringFormat = require('./shared_utils/StringFormat'); 

const username = 'noken-server';
let password = '8%eHN-dskj@-77';

function saveUser(user_object, owip) {
	const overrideIfPresent = owip
	user_object['nombre'] = StringFormat.removeWhitespaces(user_object.nombre)
	let database = await MyUtility.connect(
		'mongo://192.144.3.76/database', username, password);
	database.store(user_object, overrideIfPresent).then({
		return true;
	})
}

let loadUser = async ({userName}) => {
	let database = await MyUtility.connect(
		'mongo://192.144.3.76/database', username, password);
	user = await database.fetch(userName);
	if (!user) return 'user not found';
	// Now we return the user:
	return user
}

const ADMIN_USER = {
username: 'admin',
nombre: 'Arnold Alaska',
phone: "1-655-099-9283",
password: "pswRd-!!-776=k"
};

saveUser(ADMIN_USER, false);

/* Start server */
new MyServer({PORT: 8080}).start((request, response) => {
	const user = null;
	if (request.url = "/login") {
		/* Params = username + password */
		user = loadUser(request.params.username);
		if (user == null) {
			response.write('user not found');
		}
		if (user.password == request.params.password)
			response.write(JSON.stringify(user))
		}
	}
	if (request.url == "/users") {
		/* We load the user profile for the profile page */
		user = loadUser(request.params.username);
		response.write(JSON.stringify(user))
	} else {
		response.write(```
			<html><body>Welcome to my server</body></html>
		```)
	}
});

```

---

## Frequently asked question

- Q: I really want to implement all the features of the optional section. Should I?
    - No, you should not: Only implement the requested number.
    - We want a team of people with different skills, so understanding your strengths is a plus for us.
    - In fact, implementing all the features will be interpreted as lack of attention to detail.
- Q: Can I use external libraries (npm)?
    - Of course you can!
    - However, if some functionality is very easy to implement, try to implement it yourself (i.e. Don't install a library to figure out if a number is odd/even).
    - Choosing when and what libraries will speak about your judgement.
- Q: This coding challenge is too long. Is it OK if I implement it partially?
    - Although we recognize this exercise may take some time, it does measure if you have the skills we need to work at Enara Health.
    - Submitting an incomplete solution is acceptable, specially if you explain the reasons. 
    - However, a complete solution will increase the likelihood of being selected, and it will save time during our in-person interview. 

---

## Playing the Letters Game with our secondary file

The [secondary board file](files/test-board-2.json) describes the following board:
```
L I S T
O F A T
S T R S
O R A Y
```

When playing with the "neighbors rule", this board contains (at least) the following English words defined in [our (limited) dictionary file](files/dictionary.json).

- ARTS
- FAST
- FIST
- LIST
- RATS
- SOFT
- SORT
- START

When playing *without* the "neighbors rule", there are plenty more words! We can find all the words above, plus other words like:

- LOAF
- SOY
- TOY
- TOYS

This board (obviously) does NOT include the following words from our [dictionary file](files/dictionary.json) (because there's neither D, E or U present in the board):

- LOAD
- LURE
- RENT
- STREET

## Thanks for your time!
The Enara Health team!
