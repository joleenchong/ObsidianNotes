PDF:
https://www.hasbro.com/common/instruct/00009.pdf

A web app that allows users to customise their monopoly board and host games online. I will use this app to practice JavaScript & figure out web dev.
[[Polypoly breakdown.canvas|Polypoly breakdown]]

# Game flow
## Goal
Become the last player left after everyone else becomes bankrupt OR after a certain amount of turns, have the most worth calculated from owned properties and cash.
## Preparation
### Lobby
The head player creates a room and shares the password and code with other players up to a maximum of 8 players. The head player can choose what board they will play with and the goal of the game.
### Game start
Chance and community chest cards are shuffled randomly. Each player chooses a token to represent them on the board. Each player receives a total of $1500 divided as follows: 2 $500s, 2 $100s, 2 $50s, 6 $20s, 5 $10s, 5 $5s, and 5 $1s. We could adjust this based on number of players in the game. Each player rolls a 6-sided die (or we could potentially increase the number of sides) to determine turn order. The person who rolled the highest will go first.
## Turns
At a player's turn, they roll a d6 to determine how far they travel. The location they land on determines what sort of actions they can do.
# Classes
## Location
> [!info] Fields
name : String
locationType : String
Image : image file

This is what the tokens land on after each dice roll.
### Properties
Locations on the game board that can be bought.
#### Sets

#### Train stations

#### Utilities

## Player
> [!info] Fields
> name : String
> token : image file
> money : int
> owned properties : property array?
> bankrupt : boolean

## Tokens

## Cards
### Chance

### Community Chest

## Money
We could customise the money face too.

## Actions
Customise triggers and actions to make custom rules for the game.