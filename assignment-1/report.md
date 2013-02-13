# Report

## Roles

- Bidder
- Seller
- Mediator (Auctioneer)
- BidHelper

## Protocol

- notifyWinnerOfAuction()
  - Description: Called when bidder winns an auction
  - Initiator: Mediator
  - Partner: Bidder
  - Input: {auction_id: Integer, price: Integer}
  - Output: Void
- notifyLoserOfAuction()
  - Description: Called when bidder loses an auction
  - Initiator: Mediator
  - Partner: Bidder
  - Input: {auction_id: Integer, price: Integer, winner_id: Integer}
  - Output: Void
- notifyNotHighestBidder()
  - Description: Called when bidder doesn't have the higest bid
  - Initiator: Mediator
  - Partner: Bidder
  - Input: {auction_id: Integer, price: Integer}
  - Output: Void
- makeOffer()
  - Description: Bid on an item
  - Initiator: Bidder
  - Partner: Mediator
  - Input: {auction_id: Integer, price: Integer, bidder_id: Integer}
  - Output: {status: STATUS}
- searchForItem()
  - Description: Search for an item
  - Initiator: Bidder
  - Partner: BidderHelper
  - Input: {query: String}
  - Output: {item_id: Integer}
- notifyAboutEndedAuction()
  - Description: Information about an ended auction
  - Initiator: Mediator
  - Partner: Seller
  - Input: {auction_id: Integer, winner_id: Integer, price: Integer}
  - Output: Void
- createAuction()
  - Description: Create auction for item
  - Initiator: Seller
  - Partner: Mediator
  - Input: {description: String, seller_id: Integer, min_price: Integer}
  - Output: Void
- searchForItem()
  - Description: Search for an item
  - Initiator: Bidder
  - Partner: BidHelper
  - Input: {query: String}
  - Output: {item_id: Integer}

### Seller

#### Description

Sells items on market

### Bidder

#### Description

Bid items on market

### BidHelper

#### Description

Search for items

#### Permissions

- reads auctions

### Mediator

#### Description

Our platform auctioneer

##### Permissions

- changes auctions
- changes bids

##### Safety

- exists(auction_id)
- exists(winner_id)
- exists(seller_id)
- exists(bidder_id)
- description.length > 0
- min_price > 0
- price > Auction.higest_bid