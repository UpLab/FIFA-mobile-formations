# Fifa mobile formations

## Technical Requirements:

*	React
*	ES6
*	SASS
*	Meteor
*	Mongo
*	GraphQL # ?

## Features:

*	Sign up
*	Sign in
*	Password reset
*	CRUD (Create, Update, Delete) your players
*	Display a list of your players
*	Display a list of Formations
* CRUD your Formations
* Calculate teamwork and power

## Constant data

* Formations
* Leagues


## Schemas

### Type Metadata

```
{
  createdAt: Date, # date of document creation
  createdBy: String # user id
  updatedAt: Date, # date of document last update
}
```

### type Squad

{
  _id: String # MongoDB-generated id
  formationId: String # id of formationId
  players: [{
    index: Number
    playerId: # id of Player
  }]
  power: Number # calculated
  teamwork: Number # calculated
  ...Metadata
}


### type Player

```
{
  _id: String # MongoDB-generated id
  fullName: String # name of the player
  biography: {
    team: {
      name: String # name of the team
      multiplier: Number
    } 
    league: {
      name: String # name of the league
      multiplier: Number
    }
    country: {
      name: String # https://ru.wikipedia.org/wiki/ISO_3166-1_alpha-2 2-letter country code
      multiplier: Number
    }
    source: {
      name: String # where did we get this player 
      multiplier: Number
    }
  }
  power: Number # 40...150 # power of the player
  ...Metadata
}
```

### type Formation

```
{
  _id: String, # MongoDB-generated id
  name: String, # display name of the tactic
  nodes: [
    {
      index: Number # index of the player
      relations: [Number] # indexes of the players that are related
      row: Number # row index. goalkeeper has row index 0
      position: Number # column index. leftest has index 0
    }
  ]
  ...Metadata
}
```
