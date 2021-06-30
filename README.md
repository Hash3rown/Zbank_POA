# ZBank Proof of Authority Netowrk instructions

### Important: Please ensure you have the necessary packages installed on your machine prior to setup.
You will need:
  * anaconda with installations of geth and puppeth (we recommend you create a new python (3.7) virtual environment for these installations. Be sure to note the location of the geth install.
  * Mycrypto desktop app (from Mycrypto.com)  - you will need this to perform functions such as decrypting private keys as well as performing transactions int he network.

### 1. Create the accounts and data directories for your nodes
  * Open a terminal window and navigate to folder containing geth (default for macOS = /usr/local/bin)
  * Create the accounts using the command `$ ./geth --datadir zbank1 account new` and `$ ./geth --datadir zbank2 account new` **provide a new password and do not forget it.
  * Retain the addresses provided for each account - you will need these later.
  * create a password file using `$ echo "<password> > password.txt`

### 2. Configure your private network using puppeth
  * use `$ ./puppeth` from the containing directory to run puppeth
  * follow the prompts to create a new genesis, select PoA, use the default block time and include both of your node addresses for permission and pre-funding. You should choose 'no' when prompted to pre-fund the 'precompiled' accounts.
  * After completing all of the prompts choose 'Manage existing genesis' then 'export genesis configuraitons'. This will create a <networkname>.json file which we will use to initialize each node.

### 3. Initialize the nodes using the .json configuraiton file
  * Use the commands: 
      *`$./geth --datadir zbank1 init <networkname>.jason` for node 1 and;
      * $./geth --datadir zbank2 init <networkname>.jason` for node 2.

### 4. Now the nodes can be used to begin mining blocks.
    * Run the nodes in separate terminal windows with the commands:
        *  ./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock --password password.txt
        *  ./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock --password password.txt

##### Note - 
 * The --mine flag tells the node to mine new blocks.
 * The --minerthreads flag tells geth how many CPU threads, or "workers" to use during mining. Since our difficulty is low, we can set it to 1.
 * The --unlock flag unlocks the node for use - the password.txt value calls the file we created above
 * The --allow-insecure-unlock flag allows us to unlock in an insecure mananer
 * The --rpc flag allows this node to communciate via the internet
 * The --bootnodes flag allows node 2 to locate the already operating node 1
  
### 5. Test your blockchain with transactions
 * Using Mycrypto or any other software wallet/keymanager which supports the derivation of private keys from a .keystore file. If using MyCrypto see the image below (choose import your node 2 wallet address by selecting the corresponding .keystore file (../Zbank2/keystore/<keystore_file>)
 ![screenshot_mycrypto](/Screenshots/mycryptmain.png)
 * Now you have access to your test wallet you can initiate a test transaction from the node 2 wallet to the node 1 wallet.
 ![screenshot_mycrypto](/Screenshots/transact.png)
 * send a transaction and check the details by reviewing the transaction hash:
 ![screenshot_mycrypto](/Screenshots/TX_HASH.png)
 ### CONGREATULATIONS YOU'RE A BLOCKCHAIN USER!!!!
 
### Network Information
Network Name: zbanknet
Chain ID: 543321
Blocktime: 15
Accounts:
zbank1 ** password = password.txt ** Public address of the key: 0x56b029987E640c45Bb711281DfA3759ffF7d30BC

zbank2 ** password = password.txt ** Public address of the key: 0x4176EA076995F4E6CB72eDc72174f7057afC4076
