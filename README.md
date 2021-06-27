# Zbank Proof of Authority Network instrucitons

Instructions
Ensure that you have downloaded and installed anaconda, puppeth, geth, and MyCrypto. You will need these tools in order to access ZBank's blockchain network and crypto wallets.
Open your Terminal and set your virtual environment to "zbanknet" with the command: conda activate zbanknet
Direct to the folder in which you have geth saved
To initialize the first node on the blockchain, run the command: ./geth init z.json --datadir znode1
To initialize the first node on the blockchain, run the command: ./geth init z.json --datadir znode2
Create a file called "password.txt" with the password for the node(s), and save it in the same directory as your node files
Ensure that there is an empty line below the password in the file (i.e. hit enter)
To start mining the first node, run the command: ./geth --datadir znode1 --mine --minerthreads 1 --rpc --unlock "Edf2aC0D77A16B4E1dd17224129cDcF1e0525a29" --allow-insecure-unlock --password password.txt
The --mine flag tells the node to mine new blocks.
The --minerthreads flag tells geth how many CPU threads, or "workers" to use during mining. Since our difficulty is low, we can set it to 1.
The --unlock flag unlocks the node for use - the password.txt value calls the file we created above
The --allow-insecure-unlock flag allows us to unlock in an insecure mananer
The --rpc flag allows this node to communciate via the internet
To start mining the second node, run the command: ./geth --datadir znode2 --port 30304 --bootnodes "enode://28fe67f78d070dd9247dfad901e21fc22b974e170b6a54e19d85e63b3a4f73f14c9932a369b0c0aad55a25f0626c41e0ebce1459ca07fad6213e4413289d69d3@127.0.0.1:30303"
Open the MyCrypto app, and create an account if you do not already have one
You will need to tap into the test network, in order to set this up on your app, please configure as shown in the "network-config" image in "Screenshots"
Once you have set up the network on your app, go to "View & Send" in the top left, and choose "Keystore File" as your authentication method. This will prompt you to direct to the file path of one of the crypto wallets below on your device. Select the file, and enter the password when prompted (also listed below).
You should now be in the wallet. In order to send ETH to the other account you are not currently in, copy and paste the receiving account's public key from below into the "To Address" input box, choose how much ETH you would like to send, and click on "Send Transaction"
Network Information
Network Name: z
Chain ID: 1929
Blocktime: 15
Accounts:
znode1 ** password = zbank ** Public address of the key: 0xEdf2aC0D77A16B4E1dd17224129cDcF1e0525a29 ** Path of the secret key file: znode1/keystore/UTC--2020-05-03T02-32-05.598612000Z--edf2ac0d77a16b4e1dd17224129cdcf1e0525a29 ** Port: 30303

znode2 ** password = zbank ** Public address of the key: 0x376454e075D4bEB0cd60e42001ea85D0DE33aCC8 ** Path of the secret key file: znode2/keystore/UTC--2020-05-03T02-32-38.828197000Z--376454e075d4beb0cd60e42001ea85d0de33acc8 ** Port: 30304
