# Arcade Rhythm games Map

## Overview

A map of known locations of specific arcade rhythm games contributed by users.
Users can either add specific games and their costs/conditions to an existing location or 
they can add a new location to the map.
This site is based on bemanicn.com, a website that shows locations of arcades with rhythm games in China.

Milestone 2 Update:
* Started research on Next.js by building webapp in next.js
* Started research on google maps api by adding a working map to my site
* Implemented a form for adding location objects to a MongoDB database

Milestone 3 Update:
* 3 Forms are working, User Registration, Location, and Game
* Continued research on Next.js by continuing development of web
* Continued research on Google maps API for adding custom pointers on map
* Begun implementation on a login system and research on password security

Milestone 4 Update:
* Implemented all 3 forms. Game, Location, and Review for Games. Users can create and view data from each form.
* Used 2 instances of built-in higher-order functions filter and map.
* Implemented 4 mongoose schemas. User, Location, Game, and Comment (Game Review)
* Added Authentication required for restricted pages like the Admin page.
* Implemented password salting and hashing.

## Data Model

This application will store Users, games, locations, and Reviews

* Locations will store games

An Example User:

```javascript
const userSchema = new Schema({
    Username: {type: String, required: true},
    Password: { type: String, required: true },
    Email: {type: String, required: true},
    Admin: {type: String, required: true}
  });
```

An Example Location:

```javascript
const locationSchema = new Schema({
    Name: {type: String, required: true},
    Description: {type: String, required: false},
    Image: {type: String, required: false},
    Games: [{ type: Schema.Types.ObjectId, ref: 'Games', required: false }],
    XCoord: {type: Number, required: false},
    YCoord: {type: Number, required: false}
});
```

An Example Review:

```javascript
const commentSchema = new Schema({
    Game: {type: String, required: true},
    User: {type: String, required: true},
    Subject: {type: String, required: false},
    Comment: {type: String, required: false},
    Rating: {type: String, required: false}
});
```

An Example Game:

```javascript
const gameSchema = new Schema({
    Name: {type: String, required: true},
    Condition: {type: String, required: false},
    Cost: {type: Number, required: false},
    Description: {type: String, required: false},
    Image: {type: String, required: false}
});
```


## [Location Schema](app/models/locations.js) 
## [Game Schema](app/models/games.js) 
## [User Schema](app/models/users.js) 
## [Review Schema](app/models/comments.js) 

## Wireframes

/login - player login page
![alt text](public/img/login.png)

/home - page that has a map with marked points representing a location
![alt text](public/img/home.png)

/home/filter - page that shows all the filtering options
![alt text](public/img/filter.png)

/home/add-location - page that allows a user to add a location
![alt text](public/img/addarcade.png)

/home/add-game - page that allows a user to add a game
![alt text](public/img/addgame.png)

/home/account - page that display's the games and locations a the user has added
![alt text](public/img/account.png)

The main changes I made to the site is I decided not to include an account page. I also added seperated pages to display games and locations and added a filter function to location list. I also added a admin page.

## Site map

![alt text](public/img/sitemap.png)

## User Stories or Use Cases

1. as non-registered user, I can register a new account with the site
2. as a user, I can log in to the site
3. as a user, I can view the map and its locations and games
4. as a user, I can filter locations by their games
5. as a user, I can add a game to a location
6. as a user, I can add a location to the map
7. as a user, I add reviews to games
8. as an admin, I can manage non-admin users and locations


## Research Topics
* (3 points) Configuration Mangagement and dotenv
    * dotenv allows me to store configuration in a .env file without it being in the source code.
    * This improves security especially since I must store my mongoDB login credentials somewhere secure.
    * I also used dotenv to store my api key for Google Maps.
* (6 points) Frontend with next.js
    * I will be using next.js as the frontend framework for my website
    * Originally I wanted to use react but I realized I would have to deploy 2 seperate apps
    * With next.js, I can use all the functionalities of react while making everything in 1 app.
* (2 point) Google Maps api
    * I will use the google maps JS api to function as the actual map containing the locations
    * The google maps api allows me to display a rendition of google maps on my website.
    * I also used the google maps api to allow the user to easily specify the location they want to add an arcade.
    * It also allows me to add pointers/markers which will be essential in showing the location of each arcade interactively
    * I am increasing this to 2 points since I find that research on building custom pointers and implementing user-added pointers is harder than expected.


## Annotations / References Used
2. [Documentation on Google Maps API](https://developers.google.com/maps/documentation/javascript)
3. [Dotenv homepage and information](https://www.npmjs.com/package/dotenv)
4. [React references](https://react.dev/reference/react)