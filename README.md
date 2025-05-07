# Vecka 20: API Bootcamp - Veckans Code Review-uppgift

## Del 1: Todo App

Du ska i denna övning bygga ett API för en todo-app. Du kan i denna övning spara din todos i en array i en variabel.

Det ska kunna gå att:

- Hämta alla todos
- Lägga till en ny todo
- Uppdatera en todo
- Ta bort en todo

### Instruktioner

1. Skapa en mapp för ditt projekt.

2. Skapa en package.json med `npm init -y`.

3. Installera **express** med `npm install express`.

4. Skapa en _server.js_ där din kod ska ligga.

5. Skapa mappen _data_, och filen _todos.js_ där du klistrar in [följande kod](./data/todos.js). Importera sedan till din server-fil.

### Endpoints

URL: `/api/todo` - Hämta alla todos

Method: `GET`

---

URL: `/api/todo` - Lägg till en ny todo

Method: `POST`

Body: `{todo: 'Köpa trisslotter', id: nummer, done: false }` (done behöver inte skickas med utan kan alltid sättas till false när en todo skapas)

---

URL: `/api/todo/:id` - Togglar true/false på done för en todo

Method: `PUT`

---

URL: `/api/todo/:id` - Ta bort en todo

Method: `DELETE`

### Level ups

#### Level up 1

Lägg till en egenskap på varje nyskapad Todo Items som är när den skapades och när den uppdaterades. `createdAt`, och `updatedAt` läggs till på servern alltså skickas inte med i body från Insomnia. Tips! Använde date-objektet https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date

```js
{
    todo : String,
    id: Number,
    done: Boolean,
    createdAt: Date
}
```

#### Level up 2

Lägg på _pagination_ på routen som hämtar alla Todos.

**Exempel**

Om det finns mer än 5 todos i din array så ska routen som hämtar alla todos endast hämta de 5 första. Men med en query parameter (offset och limit) ska man kunna välja nästa 5 todos osv.

## Del 2: Login och Registrering

I denna övning ska du bygga ett API som ska kunna användas till inloggning och skapa en konto.
När man registrerar ett konto ska andvändaren ange användarnamn, lösenord och e-postadress. Det ska inte vara möjligt att registerera sig med ett användarnamn eller en e-post som redan finns. När en användare försöker logga in ska användarnamn och lösenord kontrolleras det som finns sparat.

### Instruktioner

1. Skapa två endpoints i din Node.JS - fil som heter **/api/login** och **/api/signup**.

   - **/api/login** - tar användarnamn och lösenord som har skickats in och kollar om användaren finns samt är samma som i arrayen med användarkonton. Endpoint:en ska returnera ett objekt med egenskapen **success** som antingen är true eller false till klienten, samt all info om den inloggade användaren.

   - **/api/signup** - tar emot användarnamn, lösenord, och e-post och kontrollerar så att användarnamn och e-post inte redan finns. Endpoint:en ska returnera ett objekt med egenskaparna: **success**, **usernameExists** och **emailExists**. Alla egenskapar är antingen true eller false.

2. Allt kan sparas i variabel på din server, ex `const users = [];`.
