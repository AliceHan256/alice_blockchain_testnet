# Set up a testnet blockchain for ZBank

First, download and install MyCrypto App in your computer.

Next, this blockchain testnet needs to run in the ethereum environment. To do this, you need to open your Git Bash (Windows) or Terminal (macOS) and run the code below:
conda activate ethereum

The following information has been created to run the testnet.
Network's name: blockpoa889, 
Chain ID: 889,
Genesis block's folder name: ahblock2
Consesuss algorithm: Proof of Authority (PoA) 
Period: 5 seconds
Nodes information: 
node1:
  Public address: 0xc46ec486E0877B328dD63d0380Bf9d14B52b0530
  Password: apple123
  Port numbers: 30303
node2:
  Public address: 0x18cB02Bae51fF0136e43Af33DddF66e766D32BF5
  Password: apple123
  Port numbers: 30304
local host: http://127.0.0.1:8545/

Now, let's run the testnet. 
First, navigate to the folder named alice_blockchain_testnet in your Git Bash or Terminal:
cd ~/alice_blockchain_testnet

Using the below code to initialize each code with the blockpoa889.json file.
./geth --datadir node1 init ahblock2/blockpoa889.json
./geth --datadir node2 init ahblock2/blockpoa889.json

Run the node1 with the below command and use the password given above to unlock the account:
./geth --datadir node1 --unlock "0xc46ec486E0877B328dD63d0380Bf9d14B52b0530" --mine --rpc --allow-insecure-unlock
When you see the words "Commit new mining work", you have successfully arranged node1 to mine blocks. 

Then open another Git Bash or Terminal to run node2 with the command below. When a password is required, use the password given above to unlock the account:
./geth --datadir node2 --unlock "0x18cB02Bae51fF0136e43Af33DddF66e766D32BF5" --mine --port 30304 --bootnodes "enode://3d6a55888d972137e099d2179ca5d2368513c3e2edf876bd6ffaf8d11ea6a3442e539cf3c40ebf51ff96dbe54813fb7486259557c8da999d7c33e90a744cf7b9@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock
When you see the words "Imported new chain segment", you have successfully get the node2 to start mining blocks.

The private PoA blockchain should be running by now. Let's connect this network to MyCrypto. 

Open the MyCrypto app, click "Change Network" at the bottom left, refers to figure_1 in the Screenshot folder.

Click "Add Custom Node", it will pop up a window. Select "Custom" in the dropdown list under the "Network" field. The node name is given as "AHnode5", the Chain ID set as "889", and the network name set as "blockpoa889". These information are the same as when the network is built from the beginning. In the URL box, type "http://127.0.0.1:8545/" to point to the default RPC port on your local machine. 
After connecting to the custome network in MyCrypto, select the "View & Send" option from the left menu pane. As a result, the custom network is appeared on the left pane when you want to make sure it's connected to the MyCrypto app by clicking "Change Network", see figure1 in the Screenshot folder.

The above step bring you to import your keystore file from your node1. By clicking "Keystore file", it pops up another window. Click "Select Wallet File", you can find your keystore directory inside your node1 directory, select the file located there, enter the password shown as above when prompted and then click "Unlock". This will open your account wallet inside MyCrypto. Please see video1 in the Screenshot folder.

In the "To Address" box, type node2's account address, which is 0x18cB02Bae51fF0136e43Af33DddF66e766D32BF5, then fill in an amount of ETH, 8888 ETH in this case, clicking "Send Transaction" then "Send" button in the pop-up window. In about 5 seconds, it will show "Successful" next to "Status" field. These steps can be seen in video2 located in the Screenshot folder.






