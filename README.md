# jotto

## A React / Redux app used to demonstrate testing

### Components

- App
  - Title, contains children Componets
- Input
  - Input box and submit button
- GuessedWords
  - Table of guessed words
- Congrats
  - Congradulation message

### Redux State

| Key          | Data Type        | Description                                                          | Starting value   |
| ------------ | ---------------- | -------------------------------------------------------------------- | ---------------- |
| secret word  | string           | Word the user is trying to guess                                     | word from server |
| success      | boolean          | Whether or not the word has been guess correctly                     | false            |
| guessedWords | array of objects | Array of objects: { guessed words: string, letterMatchCount: number} | {}               |

- **Work with** _succes_ **piece of state**
- **Action creator creates** _CORRECT_GUESS_ **action**
- **Reducer updates** _success_
- _Input_ **conditionally renders**

### Redux Thunk

- **Action creators that fire off multiple actions**
- _guessWord_
  - **Add to** _guessedWords_
  - **Conditionally update** _success_

### Aysnc action creators and Axios

- **Test action creator that gets** _secretWord_ **from server**
  ![Async Action Creators and Axios](images/2019_Update__React_Testing_with_Jest_and_Enzyme___Udemy.png)

### Redux Props in Connected Components

- **Test state and action creator props in**
  - _Input_
  - _App_
- **Test action creator calls**

### _success_ State Planning

- **Action creator for** _CONNECT_GUESS_ **action**
- **Success reducer**
  - **Controls** _success_ **piece of state**
  - **Start with value of** _false_
  - **Flip** _success_ **to** _true_ **upon** _CONNECT_GUESS_ **action**

#### 1. Number of Guesses

![Number of Guesses Wireframe](https://raw.githubusercontent.com/mojaray2k/jotto/master/images/number-of-guesses_wireframe.png)

- _Note_: Try to accomplish this _without_ adding a new piece of state!
- Add “guess number” column to the "guessed words" table
  - The first guess should show 1, second guess 2, etc.
- Add a component that displays total guesses as shown in wireframe

##### 2. Reset Game

![Reset Game Wireframe](https://raw.githubusercontent.com/mojaray2k/jotto/master/images/new-game_wireframe.png)

- Create a “New word” button component
  - only display after successful guess
- Upon click, reset the game with a new word from the server
- _Note_: This can be done with a connected component (which lends itself to state testing similar to `Input.js`) or with an unconnected component which receives the action creator from the parent `App.js` component (which will require unit testing for action creators and reducers instead, as using a store with an unconnected component is not covered in this course). The solution in the `jotto-challenges` branch covers the second approach.

##### 3. “Give up” Button

![Give Up Button Wireframe](https://raw.githubusercontent.com/mojaray2k/jotto/master/images/give-up-button_wireframe.png)
![After Give Up Click Wireframe](https://raw.githubusercontent.com/mojaray2k/jotto/master/images/after-give-up_wireframe.png)

- Create a “Give up” button
  - only display when word has not been guessed correctly
- Upon click:
  - Show secret word
  - Display "better luck next time" message
  - Display “new word” button component

#### 4. User inputs secret word

![Enter Secret Word Button Wireframe](https://raw.githubusercontent.com/mojaray2k/jotto/master/images/enter-secret-word_wireframe.png)  
 ![Secret Word Entry Form Wireframe](https://raw.githubusercontent.com/mojaray2k/jotto/master/images/secret-word-entry-form_wireframe.png)

- _Note: This one is quite involved, with a new piece of state, Redux Thunk, and testing that an action creator receives the correct argument. Not for the faint of heart! It is great for using existing tests to see whether new code breaks old functionality._
- Add a button for the user to input the secret word
  - This way, the user can play against a friend
- After submission, the game should use the user’s secret word, not a word from the server
- This button should disapppear once the user has nonzero `guessedWords`
  - Should disappear whether the word came from the server or user input

##### 5. Random Word Server Error

![Random Word Server Error Wireframe](https://raw.githubusercontent.com/mojaray2k/jotto/master/images/random-word-server-error_wireframe.png)

- Display an error if:
  - There’s a problem contacting the “random word” server
  - The server responds with status 4xx or 5xx

##### 6. Use Wordnik to get secret word

- Get a [Wordnik auth token](http://developer.wordnik.com/)
- Use the [words/randomWord](http://developer.wordnik.com/docs.html) endpoint.

#### Credits

This project was bootstrapped with [Create React App](https://github.com/facebookincubator/create-react-app).
