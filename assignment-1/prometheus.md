# Prometheus

## Scenarios

### User

#### Sell an item

Given I have an item that I want to sell
When I go to the service desk I give the service desk
  the minimum price,
  the end date for the auction
  and the item it self
Then I should receive a unique id

#### Bid on an item

Given I search for a car
When I click on any given car and make my bid
Then I should be able to see that my bid was added
If my bid is the highest after auction end date
Then I win the auction

### Service desk

#### Start an auction

Given a user hands in 
  an item,
  a type,
  a minimum price
  and an end date
Then I should be able to tell my database to create the given item
Then I return a unique id to the user

#### Take a bid

Given a user hands in 
  an auction id
  and a minimum price
When the database has been updated
Then I should be able to return an action state

#### Search for item

Given a search string provided by the user
When the user clicks search
Then it should be able to list all matched items

### Database

#### Add an item

Given 
  an item,
  a min price,
  a user id,
  and an action end date
When I create action is executed I create a database record
Then I return a unique id representing the item in question

#### Add an invalid item

Given 
  an item id,
  a price,
  a user id,
When I add an invalid bid with a lowver price
Then I return a status code equal to fail

#### Add bid to action

Given 
  an item id,
  a price,
  a user id,
When I add a valid bid
Then I return a status code equal to success

### Auction event loop

#### An action ends with bids

Given I'm on the next tick
When I list all actions 
  marked as "not finished"
  and where end date > current date
Then I should 
  notify the higest bidder for each action
  and mark the given action as closed
  
## System goals

- Vilken funktionalitet ska systemet ha?

## Protocols

- Klart(ish)

## System overview

## Agent descriptors

## Agent description

## Agent overview

## Capability descriptors

## Capability overview

## Event description

## Data description

## Plan description