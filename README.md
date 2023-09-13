# JS-Advanced-Concepts-Study

Playlist

1. What Are Design Patterns?
   General - Applied to multiple aspects of design.
   Reusable - Use all through app and in different scenarios.
   Formalization of best practices -formal written way of normal best practices.

   Make code, easier to read.
   Dont over use
   Sometimes Overkill

   Questions & Clarifications:
   None

2. Builder Pattern - Design Patterns
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
