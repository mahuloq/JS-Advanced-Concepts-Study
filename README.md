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

Questions & Clarifications
