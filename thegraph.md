# THEGRAPH Conceptual Layout 28-08-2020 

## THEGRAPH DESCRIPTION:

THEGRAPH is used to index calls/events from smart contracts over the entire blockchain and then enables a user to query those in different ways.

Those 'ways' are described in the Schema, which is a high level representation of the information that one wants to expose via the API.

It consists of different 'entities' which each have subcomponents, such as ID, name, balance, price, etc, relating to the entity.

Now the magic comes from the ability to map, or relate those entities and subcomponents to smart contract calls or/and events through assemblyscript and typescript. So for a very basic example if one entity would be Strategies, you could define 'Total AUM' by mapping it to a function that gets the values from each SC, multiplies them the asset price and sums them up.

Additionally the queries can be done for an arbitrary blockheight.

# YEARN LAYOUT CONCEPT IDEA:

## Vaults
* ID (address)
* Name
* Symbol
* Underlying asset (token)
* Controller
* Strategy {derived from **STRATEGIES**}
* Funds total
* Funds in strategy
* sharePrice
* ROI from block to block

## Strategies
* ID (address)
* Name
* Vault {derived from **VAULTS**}
* Funds
* ROI from block to block
* Controller
* Fees

## Treasury
* ID (address)
* Funds
* Fees/Revenue


With this Layout the question of 'take rate' can be answered in one query:

> Treasury{Revenue} / Strategies{Funds}

Furthermore, since thegraph indexes the *entire* blockchain charts can easily be created for revenue vs time, take rate vs time, ROI of strategies vs time, etc.