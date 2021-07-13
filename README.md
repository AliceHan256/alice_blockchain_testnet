# Set up a testnet blockchain for ZBank

First, download and install MyCrypto App in your computer.

Next, this blockchain testnet needs to run in the ethereum environment. To do this, you need to open your Git Bash (Windows) or Terminal (macOS) and run the code below:
conda activate ethereum

The following information has been created to run the testnet.
Network's name: blockpoa66, 
Chain ID: 5559,
Genesis block's folder name: ahblock1
Consesuss algorithm: Proof of Authority (PoA) 
Period: 5 seconds
Nodes information: 
node1:
  Public address: 0x85822CADFB2fAd5dE3f769733e8834413e9e645f
  Password: apple123
  Port numbers: 30303
node2:
  Public address: 0x48a8921Ee8d56D04E368E1Bb08f3FB7b6cFd3DD3
  Password: apple123
  Port numbers: 30304
local host: https://127.0.0.1:8545

Now, let's run the testnet. 
First, navigate to the folder named alice_blockchain_testnet in your Git Bash or Terminal:
cd ~/alice_blockchain_testnet

Using the below code to initialize each code with the blockpoa66.json file.
./geth --datadir node1 init ahblock1/blockpoa66.json
./geth --datadir node2 init ahblock1/blockpoa66.json

Run the node1 with the below command and use the password given above to unlock the account:
./geth --datadir node1 --unlock "0x85822CADFB2fAd5dE3f769733e8834413e9e645f" --mine --rpc --allow-insecure-unlock
When you see the words "Commit new mining work", you have successfully arranged node1 to mine blocks. 

Then open another Git Bash or Terminal to run node2 with the command below. When a password is required, use the password given above to unlock the account:
./geth --datadir node2 --unlock "0x48a8921Ee8d56D04E368E1Bb08f3FB7b6cFd3DD3" --mine --port 30304 --bootnodes "enode://3f5b781161aed7ba8264e67cdb1425051652f3b2b64064464d33aee82b72dec762532d9cf769a5f21c764a078602899321bb334813bd9dd9114301d835ad14a5@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock
When you see the words "Imported new chain segment", you have successfully get the node2 to start mining blocks.

The private PoA blockchain should be running by now. Let's connect this network to MyCrypto. 

Open the MyCrypto app, click "Change Network" at the bottom left, refers to figure_1 in the Screenshot folder.

Click "Add Custom Node", it will pop up a window. Select "Custom" in the dropdown list under the "Network" field. The node name is given as "AHnode2", the Chain ID set as "5559", and the network name set as "blockpoa66". These information are the same as when the network is built from the beginning. In the URL box, type "http://127.0.0.1:8545" to point to the default RPC port on your local machine. After connecting to the custome network in MyCrypto, select the "View & Send" option from the left menu pane. As a result, the custom network is appeared on the left pane when you want to make sure it's connected to the MyCrypto app by clicking "Change Network", see figure2 in the Screenshot folder.

The above step bring you to import your keystore file from your node1. By clicking "Keystore file", it pops up another window. Click "Select Wallet File", you can find your keystore directory inside your node1 directory, select the file located there, provide your password when prompted and then click "Unlock". This will open your account wallet inside MyCrypto. 

In the "To Address" box, type node2's account address, which is 0x48a8921Ee8d56D04E368E1Bb08f3FB7b6cFd3DD3, then fill in an amount of ETH, 8888 ETH in this case, clicking "Send Transaction" then "Send" button in the pop-up window. Wait for about 5 seconds, it will show "Successful" next to "Status" field.






