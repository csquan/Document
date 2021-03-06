Background

Users can play two roles, deeply participate in ecological construction, and can obtain considerable benefits.


Role Selection

Users can register as the council candidates or witness (BP) candidates or as both a Council and a Witness candidate.

Top 11 candidates which is sorted by it's votes in the Council Election  become active council members within 24 hours after successful voting, participate in online governance, and vote on proposals.

Top 11 candidates which is sorted by it's votes in the witness Election  become active witnesses within 24 hours after successful voting. You need to refer to the following configuration instructions to build block nodes and participate in block production.

Become an Active Council

1.Registered account name of main network

Firstly check [Developer wallet download and account registration](https://github.com/Cocos-BCX/Document/blob/master/chain_development/Developer%20wallet%20download%20and%20account%20registration.md) to download and operate the wallet, and then register for the COCOS MainNet account. As the current council threshold requires 50 million COCOS At the same time, registering a candidate costs 1000 COCOS, so you need to own a minimum amount of 50,001,000 COCOS.

2.Register for Council Candidate

Before the transaction, please follow [Developer wallet operation command](https://dev.cocosbcx.io/docs/22-cli_wallet) to import the referer account private key; otherwise, it prompts a permission verification error.


a.Upgrade Account

upgrade_account account name true

b.Registration Council Candidate

Type the command in the wallet command line

create_committee_member account name url true

3.Vote

Type the command in the wallet command line

vote_for_committee_member Voting account name Voted account name Voting amount * 100000 true

4.Check if the Current Votes can be Successfully Elected

You need to check whether the current number of votes can be successfully elected.

a.Get Council ID

Type the command list_committee_members "" 14

The results are as follows:

![图片](https://uploader.shimo.im/f/e50fyB5Unb4Zaq5Z.png!thumbnail)

b.Query the Number of Votes

Type commands

get_committee_member 1.5.0

The results are as follows:

![图片](https://uploader.shimo.im/f/2s8URu5AgA49BwKY.png!thumbnail)

Check if the number of votes in your account is within the top 11. If not, you should get more votes. Steps 3 and 4 may be repeated several times.

5.Check the Information After 24 hours

Type the command info in the command line

The results are as follows:

![图片](https://uploader.shimo.im/f/dboChfeOAhkW0pIY.png!thumbnail)

The red box here is the account id, you can get the account id by using the command get_account account name

![图片](https://uploader.shimo.im/f/sdVHKWu8C7IzjlQq.png!thumbnail)

Check if the account ID is in the active_committee_members list returned by info.

6.View Benefits

The income of the council will be immediately received, and it will be distributed once every 24 hours.

Become an Active Witness

1.Registered account name of main network

Firstly check [Developer wallet download and account registration](https://github.com/Cocos-BCX/Document/blob/master/chain_development/Developer%20wallet%20download%20and%20account%20registration.md) to download and operate the wallet, and then register for the COCOS MainNet account. As the current council threshold requires 50 million COCOS At the same time, registering a candidate costs 1000 COCOS, so you need to own a minimum amount of 50,001,000 COCOS.

2.Register Witness Candidates

Before the transaction, please follow [Developer wallet operation command](https://dev.cocosbcx.io/docs/22-cli_wallet)  to import the referer account private key, otherwise a permission verification error will be prompted.

a.Upgrade Account

upgrade_account account name true

b.Register Witness Candidate 

Type the command in the wallet command line

create_witness account name url true

The results are as follows:

![图片](https://uploader.shimo.im/f/eJbXUp4X44MwgOUa.png!thumbnail)

c.Get Witness ID

![图片](https://uploader.shimo.im/f/DeNxNk7AfjgMvu4v.png!thumbnail)

d.Export Signature Public and Private Keys

Type the command in the wallet command line

dump_private_keys

Export the current wallet private key

The results are as follows:

![图片](https://uploader.shimo.im/f/qCFwEw4EJT0hPgnY.png!thumbnail)


Find a pair of public and private keys that match block_singnning_key in a

3.Build Block Nodes

Check [Construction of Cocos-BCX node environment](https://github.com/Cocos-BCX/Document/blob/master/chain_development/Construction%20of%20Cocos-BCX%20node%20environment.md
) to build the node, install docker and run the installation script.

4.Configure the Config File

The installation script creates a new witness directory in the / mnt directory by default, enters the config directory under witness, edits the config file, and modifies as following:

![图片](https://uploader.shimo.im/f/NWgHa3mtFjgLvWoi.png!thumbnail)

Fill in the first red box with the obtained witness ID

Fill the second red box with the signed public and private key corresponding to the obtained block_signning_key, save and exit.

5.Restart

docker restart witness

After that view logs

tail -f /mnt/witness/logs/witness_node.log showing words got block is correct

6.Vote

Type the command in the wallet command line

vote_for_witness Voting account name Voted account name Voting amount * 100000 true

The results are as follows:

![图片](https://uploader.shimo.im/f/ysSLX11eIYEk4tyX.png!thumbnail)

7.Check if the Current Votes Can be Elected Successfully 

You need to check whether the current number of votes can be successfully elected.

a.List Current Witness Candidates 

Type the command list_witnesses "" 10

The results are as follows:

![图片](https://uploader.shimo.im/f/7bRwnAApZO0ZdFCY.png!thumbnail)

b.Querying Votes

Type get_witness 1.6.1

The results are as follows:

![图片](https://uploader.shimo.im/f/L3nQIdBCJvMxhufn.png!thumbnail)

                
Check if the number of votes in your account is within the top 11. If not, you should get additional votes. Steps 6 and 7 may be repeated several times.

8.Check Information After 24 Hours

Type command info in the command line 

The results are as follows:

![图片](https://uploader.shimo.im/f/BazAAaPraYQVH1x8.png!thumbnail)

The red box here is the account id, you can get the account id by using the command get_account account name

![图片](https://uploader.shimo.im/f/F3cSeaJ3HSo0F038.png!thumbnail)

Check whether the account ID is in the active_witnesses list returned by info.

Check the log tail -f /mnt/witness/logs/witness_node.log and you can see the words generate block appear every few lines.

9.Actively Claim Benefits

Witnesses' block rewards are issued in real time. (One block in 2 seconds, each block gets 100COCOS.) At present, witnesses need to claim actively.

a.Firstly get_vesting_balances account name View vesting ID and number of withdrawals

![图片](https://uploader.shimo.im/f/kx5MbbaDIXogPQ0i.png!thumbnail)

The first red box is vesting ID

The second red box is the number that can be taken out (with 5 digits of precision)

b.withdraw_vesting vesting_id amount COCOS true

Note: the amount here does not have precision, for example, enter 225490000000/100000 = 2254900

Appendix link:

1.Developer wallet download and account registration

[https://github.com/Cocos-BCX/Document/blob/master/chain_development/Developer%20wallet%20download%20and%20account%20registration.md](https://github.com/Cocos-BCX/Document/blob/master/chain_development/Developer%20wallet%20download%20and%20account%20registration.md)

2.Developer wallet operation command

[https://dev.cocosbcx.io/docs/22-cli_wallet](https://dev.cocosbcx.io/docs/22-cli_wallet)

3.COCOS_BCX node environment setup instructions

[https://github.com/Cocos-BCX/Document/blob/master/chain_development/Construction%20of%20Cocos-BCX%20node%20environment.md
](https://github.com/Cocos-BCX/Document/blob/master/chain_development/Construction%20of%20Cocos-BCX%20node%20environment.md)


.


