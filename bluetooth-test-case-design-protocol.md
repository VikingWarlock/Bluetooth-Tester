## Bluetooth Test Case Design Protocol

### Datagram

Before construct the configure file, we should regulate some rules.

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

DATA CHECK: simulate a procedure, take some key datas in the progress and analyse whether the device responds right or not.

Use key "type" in "test case" to describe a test case's type

Value|Name|Description
---|---|---
0|RECORD| Collect DATA
1|DATA CHECK| Check response

---

### Structure

After defining some values. We can forcus on the configure file.

How to construct a valid `JSON` file that the test Application can understand?

    |- "name":string <test configure name>
    |- "filter-service":string <filtered service's uuid>
    |- "device-define":list <describe services and characteristic that needed>
        (define every service that is needed in the test)
        |- "service":string <service's uuid>
        |- "characteristic":list
            (define every characteristic that is needed in the test)
            |- "uuid":string <characteristic's uuid>
            |- "name":string <characteristic's name>
            |- "read-type":READ TYPE <characteristic's read type>
            |- "write-type":WRITE TYPE <characteristic's write type>
    |- "test case":list
        (define every test case)
        |- "type": TEST TYPE
        |- "step":list
            (define every step in this test case)
            (it will be told later)
        |- "repeat":integer
    
Test case is difficult to describe, because it is complicated and complex, so the first version of the test case may not be able to use in some situation.

First determine the `RECORD` test case. This is easier than `DATA CHECK`.

