# JS-Advanced-Concepts-Study

Playlist

1.  What Are Design Patterns?
    General - Applied to multiple aspects of design.
    Reusable - Use all through app and in different scenarios.
    Formalization of best practices -formal written way of normal best practices.

    Make code, easier to read.
    Dont over use
    Sometimes Overkill

    Questions & Clarifications:
    None

2.  Builder Pattern - Design Patterns
    2 ways to use builder -
    Original- Only required paramaters in this that we need for User, use methods in the builder for each other info you need.
    Class User{
    constructor(name) {
    this.name = name
    }
    }
    class UserBuilder{
    constuctor(name) {
    this.user = new User(name)
    }
    setAge(age) {
    this.user.age=age;
    return this
    }
    build(){
    return this.user
    }
    }

    JavaScript Way - Dont need to construct UserBuilder

    Class User{
    constructor(name, {age, phone, address}={}) {
    this.name = name
    this.age = age
    this.phone = phone
    this.address = address
    }
    }

    Questions & Clarifications
    What is the purpose of the build() and the returns in the UserBuilder

3.  Facade Pattern - Design Patterns

Facade - lets you change code
Take repeated parts of code and put it into a facade.
lets you replace just the facade intstead of everywhere in the file.
Makes refactoring easier

Questions & Clarifications
Hows this work

function getFetch(url,params={}){
const quesryString = Object.entries(params).map(param => {
return `{$param[0]}=${param[1]}`
}).join('&')
return fetch(`${url}?${queryString}`, {
method:"GET",
headers: {blahalasdl}}).then(res => res.json())
}

4. Observer Pattern - Design Patterns in JavaScript
   An object(The subject) maintains a list of dependents (observers) and notifies them when state changes, usually by calling a broadcast method.
   EventTarget.addEventListener() is an example

## CLASS WAY

class Observable (
constructor(){
this.subscribers = [];
}

subscribe(fn){
this.subscribers.push(fn)
}

unsubscribe(fn) {
this.subscribers = this.subscribers.filter((item)=> item !== fn);

} broadcast(data) {
for (let i = 0; i < this.subscribers.length; i++) {
this.subscribers[i](data);
}
}
)

const observer = new Observable();

const fn = (data) => {
console.log("Callback was executed with data", data);
};

observer.subscribe(fn);

observer.broadcast("Hello from the observable");

## FUNCTION WAY

function createObservable() {

return {
subscribers: [];

subscribe(fn){
this.subscribers.push(fn)
},

unsubscribe(fn) {
this.subscribers = this.subscribers.filter((item)=> item !== fn);
} ,

broadcast(data) {
for (let i = 0; i < this.subscribers.length; i++) {
this.subscribers[i](data);
}
},
}
}

onst observer = createObservable();

const fn = (data) => {
console.log("Callback was executed with data", data);
};

observer.subscribe(fn);

observer.broadcast("Hello from the observable");

Questions & Clarifications
Just go over the clicker +/-

5. Learn JavaScript Destructuring in 20 minutes (For Beginners)
   Instead of doing
   let person = {
   firstname: "blah",
   lastName: "blah"
   }
   then pulling that info out, you can skip it by doing
   let {firstName, lastName} = person
   or rename them
   let {firstName: fName, lastName: lName} = person

   Can also do it with arrays.
   const arr[1,2,3]
   let [x,y,z] = arr
   or skip const and go
   let [a,b,c,d] = [1,2,3,4]

can also pull out part of info
const names = ['Son','Jay','Brian','Bob']

const [x, ...y] = names
console.log(x) = Sonny
console.log(y) = 'Jay', 'brian', 'bob'

Nested object destructuring
let member = {
id:01,
name:{
firstName: "James",
lastName: "Bond"
}
}

let {name: {firstName, lastName}} = member;

let displayFullname = (person) => `${person.firstName} ${person.lastName}`;
let person = {
firstName: 'Sonny'
lastname: 'Sangha'
}

displayFullName(person)

or do
let displayFullname = ({firstName, lastName}) => `${firstName} ${lastName}`;

Questions & Clarifications
None

6. JS Spread
   ...variable
   spreads an interable

const fullfamily2 = [...parents,...kids]
combines arrays into one

or make an actual copy of an array
const painting = [paint1, paint2, paint3]

const copies =[...painting]

Questions & Clarifications
None

7. Memoization And Dynamic Programming Explained
   Store previous values to increase speed of code executing
   do it by returning results already gathered back into the function, if they repeat

Questions & Clarifications
what does putting prevValues in result= fib(n-1, prevValues) + fib(n-2, prevValues)
do

8. JavaScript Callbacks Explained
   Has a function do some work, then report/callback a previous function
   Map, reduce, sort ect
   functions that Gets passed to another function as a parameter
   that function will do some work, then call the callback function

const names = ["james", "jess", "lily", "sevy"]

const myForEach = (arr, cb) => {
for (let i=0;i<arr.length; i++;){
const element = arr[i];
cb(element)
}
}

myForEach(names,(name) => {
console.log(name);
})

const loadPokemon( id, cb) => {
fetch(`https://pokeapi.co/api/v2/pokemon/${id}`)
.then(res=>res,json())
.then(data => {
cb(data)
})
}

loadPokemon(56,(pokemon) => {
console.log(pokemon);
})

Questions & Clarifications
Maybe just a few more call back functions. Its easy when you see them written for you, writing them is hard.

9. Async Javascript
   Call Stack
   Event Loop
   Web APIs
   Promises

const promise = new Promose((Resolve, reject) => {
resolve('We did it babyyy')
})

promise.then(data => {
console.log(date)
})
.catch(err => {
console.log(err)
})

fetch is a promise

async function getTodos(){
conse response = await fetch("fetch here")
console.log(1)
console.log(response)
console.log(2)
}

Questions & Clarifications
None

Reflection

1. Clarity of these set of videos was good overall, a few terms or functions seem a bit beyond what we have done before but it did not slow comprehension overall.

2. Will help clean up code, and also the destructuring will be immediately useful. Many more tools in making a page do what you want.

3. More work on Asych, callbacks, observables and builders would prob be needed.
   The rest dont seem too bad at this time, but trying to put them in practice might show something different.
