# MNTC Auditions Quiz App Backend

## To use this app

- Create a `.env` file with the following data:

```
HOST=localhost # Host of the server
PORT=3000 # Port of the server

DB_HOST=localhost # MONGODB_HOST
DB_PORT=27017 # MONGODB_PORT

SECRET_KEY='' # SECRET_KEY FOR SESSIONS
```

- Run `node init-db.js` in a shell to initate the database with questions.
- Run `node index.js` to start the server.

## How to use this API

### Signup

```javascript
fetch("/signup", {
  headers: {
    "Content-Type": "application/json",
  },
  method: "POST",
  body: JSON.stringify({
    username: "username",
    password: "password",
  }),
});
```

Return format:

```json
{
  "success": "<boolean (success or not)>",
  "msg": "<string (message from server)>"
}
```

### Login

```js
fetch("/login", {
  headers: {
    "Content-Type": "application/json",
  },
  method: "POST",
  body: JSON.stringify({
    username: "username",
    password: "password",
  }),
});
```

Return format:

```json
{
  "auth": "<boolean (success or not)>",
  "msg": "<string (message from server)>"
}
```

### Get the next question

```js
fetch("/question");
```

Return format:

```json
{
  "question": "<question_text>"
}
```

### Answer the question

```js
fetch("/answer", {
  headers: {
    "Content-Type": "application/json",
  },
  method: "POST",
  body: JSON.stringify({ answer: "your-answer" }),
});
```

### Get the user level

```js
fetch("/usrlvl");
```

Return format:

```json
{
  "level": "<int (level of the user [1-10])>"
}
```

Return format:

```json
{
  "correct": "<boolean>"
}
```

When a user answers the question correctly, the server will automatically
increase his level until he correctly answers the last question (level 10).
The new question can be fetched by accessing `/question` again.

### TODO

- Set expiry to session cookies.
- Use constant time function to validate password.

### References

The questions in questions.json have been taken from [here](https://www.gktoday.in/quizbase/current-affairs-quiz-january-2022).
