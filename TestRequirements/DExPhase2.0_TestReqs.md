# DEx Phase 2.0

Transaction Type 21: [Sell Master Protocol Coins for Another Master Protocol Currency](https://github.com/mastercoin-MSC/spec/blob/master/README.md#sell-master-protocol-coins-for-another-master-protocol-currency)

Each application under test (AUT) must adhere to [The Master Protocol / Mastercoin Complete Specification](https://github.com/mastercoin-MSC/spec/blob/master/README.md) and pass the applicable tests listed in [Major Items & Scenarios To Be Tested](https://github.com/mastercoin-MSC/spec/blob/master/MastercoinDistributedExchangeTestPlan.md#major-items--scenarios-to-be-tested). Reminder: for DEx Phase 2, Mastercoin (MSC) or Test Mastercoin (TMSC) must be either the Currency identifier for sale or the Currency identifier desired.

The tests for Sell Master Protocol Coins for Another Master Protocol Currency include:

1. user is able to enter valid values for all appropriate fields:
    * Currency identifier for sale
    * Amount for sale
    * Currency identifier desired
    * Amount desired
    * Action
1. valid input data is parsed and interpreted correctly, including all valid MSC Protocol transaction types in the blockchain that are supported by the AUT
1. erroneous input data, including a corrupted blockchain, is detected as not valid and handled correctly
1. correct Sell Master Protocol Coins for Another Master Protocol Currency transactions are generated from valid test input data
1. runtime error conditions are detected and handled correctly (e.g. insufficient funds, application/network/OS failure)
1. all edge cases are handled correctly
1. correct, meaningful messages reflecting transaction success/status or failure are presented to the user

For each test sequence, start in a known state and return to a known state after the test is complete. Run the tests separately and also simultaneously. The simultaneous tests should be run by the same users/addresses in the same roles where possible, and also by different users/addresses.

Where appropriate, tests should be run using the end-user UI and using the API directly.

## Positive Tests - Valid
There are many valid combinations of Sell Master Protocol Coins for Another Master Protocol Currency terms & conditions.

Positive tests should exercise as many combinations and conditions as possible, including both low and high ends of input value ranges, a mix of divisible and indivisible property types.

### Create a Sell Order 
1. U1: Create New Property Creation via Crowdsale with Variable number of Tokens message(s) with valid values 
1. U1: See that the sell order has been created 
1. U1: See that the seller's available and reserved balances are changed
1. U2: See that the sell order has been created 
1. U2: See that the seller's available and reserved balances are changed

### Modify an existing Sell Order

### Cancel an existing Sell Order

### Create two or more additional Sell Orders for the same currencies

### Create two or more additional Sell Orders that should be merged with an existing Sell Order

### Create a Sell Order that exactly matches an existing Sell Order

### Create a Sell Order that partially fills an existing Sell Order

### Create a Sell Order that fully fills an existing Sell Order, with an unfilled Amount desired

## Negative Tests - Invalid
### Attempt to Create an Incorrect Sell Order
1. U1: Attempt to create tx21 message(s):
    * Currency identifier for sale = 0 or any non-existent id or any id not owned by the address
    * Currency identifier desired = 0 or any non-existent id
    * Amount for sale = 0 or exceeds the number owned and available by the address
    * Amount desired = 0
    * Neither currency identifier is MSC or TMSC
    * currency identifiers are in different ecosystems
    * Action is not 1, 2 or 3
    * For Action = 2 or 3, there is no corresponding sell order
1. U1: See that a sell order has not been created (or modified or canceled)
1. U1: See that the seller's available and reserved balances are unchanged
1. U2: See that a sell order has not been created (or modified or canceled)
1. U2: See that the seller's available and reserved balances are unchanged

The spreadsheet [DEx Phase 2.0 Tests](https://docs.google.com/a/engine.co/spreadsheets/d/1oL2jGfG3BwslURyDTYNvM6Z2p79ux46NmwcXDYleEbg/edit#gid=0) has sequences of tx21 transactions with expected outcomes. Tests and sequences will be added/improved over time.

The tester and developer should work together to write and run procedures that thoroughly test this functionality in the AUT.
