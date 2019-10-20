Fraud Detection
Fraudsters create fake transactions to boost sales/shop ratings. Fake transactions are defined as transactions where the buyer and seller are the same individual (in reality). To help Shopee tackle this issue, you are expected to detect these fake transactions from normal transactions. Sample data for transactions and users' details will be provided.

Task:
Find fake orders where the buyer and the seller are directly or indirectly linked and output the shortest link between the buyer and the seller.

Direct link: the buyer and the seller share the same details, based on any of the following: Device, Credit Card, Bank Account.
Indirect link: the buyer and the seller are not directly linked, but users who share the same details as them share details with one another:
e.g. buyer - user A - user B - user C - … - user Z - seller
If there are more than one shortest link found, please output only one link based on the following rules:
Link shall follow this priority: Credit Card > Bank Account > Device, i.e. use as many Credit Card links as possible first, then followed by Bank Account links and finally Device links.
If there are more than one results from the previous step, sort the links alphabetically in ascending order based on the priority list (i.e. sort Credit Cards first, then followed by Bank Account links and finally Device links) and output the first one.
Basic Concepts
Each userid represents a distinct user on Shopee.
Each orderid represents a distinct transaction on Shopee.
Device, Credit Card, Bank Account data is encrypted to preserve data privacy. Each distinct value represents a unique entity.

Examples:
Example 1
orderid: 1955598428, buyer userid: 35545436, seller userid: 70763052.

The buyer has this device: "/3TLpeou8xXsNxpACFFKr34Kqqwxiu5Hi1keJ6plk5E=".
The seller also has this device: "/3TLpeou8xXsNxpACFFKr34Kqqwxiu5Hi1keJ6plk5E=".
Therefore, we consider that the buyer and the seller are directly linked by device.

This order is a fraud order by definition.
-> Expected output: (Please strictly follow the format)
35545436-"device:/3TLpeou8xXsNxpACFFKr34Kqqwxiu5Hi1keJ6plk5E"->70763052.

Example 2
orderid: 1953543830, buyer userid: 223406364, seller userid: 193350172.

User 223406364 is linked to user 227839480 by sharing the same device "7q1zwUrfP8+09Z+EPh+YyNYTwxhHW7wfGuIFWhRE490=".

User 227839480 is linked to user 193350172 by sharing the same device "IkGjfHwwIGYxZ4WkM30COPKkmALyJfSSODpNTTPuMyS=".
Therefore, buyer (userid: 223406364) is indirectly linked to seller (userid: 193350172).

This order is a fraud order by definition.
--> Expected output: (Please strictly follow the format)
223406364-"device:7q1zwUrfP8+09Z+EPh+YyNYTwxhHW7wfGuIFWhRE490="->227839480-"device:IkGjfHwwIGYxZ4WkM30COPKkmALyJfSSODpNTTPuMyS="->193350172

Submit Format
Two columns required:

orderid
is_fraud:
if the order is not fraud order, assign the value "not fraud".
otherwise, please assign the value based on how they are linked. Example output format:
user1-"device:xxx"->user2-"bank_account:yyy"->user3-"credit_card:zzz"->user4
Example
orderid	is_fraud
1953277092	not fraud
1952278092	155985556-"device:mXMinTpserdP3oRZVouadvY8pFTEnc59iXSa1NQ7N7O8="->133103869
Tips:
1) You are advised to run your tests on a sample of the dataset first.
2) If you are unable to solve the entire problem within the time limit, create the output csv with the required number of columns and rows based on a subset of the problem first.

Teams which do not make a successful submission for both rounds of the competition will not be considered for the overall ranking.




Input
orders.csv: It contains orders information. Columns: [orderid, buyer_userid, seller_userid].

devices.csv: It contains devices used by the users. Each value represents a unique device. If two users use the same device, they are linked by device. Columns: [userid, device].

credit_cards.csv: It contains credit cards used by the users. If two users use the same credit card, they are linked by credit card. Columns: [userid, credit_card].

bank_accounts.csv: It contains bank accounts used by the users. If two users use the same bank account, they are linked by bank account. Columns: [userid, bank_account].

Output
Find fake orders where the buyer and the seller are directly or indirectly linked, and output how they are linked.



When csv file is opened in Notepad 

Your submission should have 620947 rows, each with 2 columns.

Teams which do not make a successful submission for both rounds of the competition will not be considered for the overall ranking.
