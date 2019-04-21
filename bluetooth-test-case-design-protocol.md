## Bluetooth Test Case Design Protocol

### Structure

How to construct a valid `JSON` file that the test Application can understand?

### Datagram

Define some variables to represent `TYPE`

#### READ TYPE

We have two ways to get data from a bluetooth characteristic: `READ` it and `Notify` it.

Use key "read-type" to describe a Characteristic's INPUT Method

Value|Name|Description
---|---|---
0|NO READ| This characteristic does not have READ and NOTIFY permission
1|READ| This characteristic has READ permission
2|NOTIFY| This characteristic has READ permission
3|READ&NOTIFY| This characteristic has both READ and NOTIFY permission

#### WRITE TYPE

We have two ways to send data to a bluetooth characteristic: `WRITE WITH RESPONSE` and `WRITE WITHOUT RESPONSE`

Use key "write-type" to describe a Characteristic's OUTPUT Method

Value|Name|Description
---|---|---
0|NO WRITE| This characteristic does not have WRITE permission
1|WRITE WITH RESPONSE| This characteristic has WRITE WITH RESPONSE permission
2|WRITE WITHOUT RESPONSE| This characteristic has WRITE WITHOUT RESPONSE permission
3|WRITE| This characteristic has both WRITE permission

#### TEST TYPE

I think there are 2 types of test is need in a Product Test: `RECORD` and `DATA CHECK`

RECORD: collect data and send it to server for record.

DATA CHECK: 