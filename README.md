# sparkplug-mac-wallet
This is the wallet code for the sparkplug chain for Mac OS
Mine for blocks with macOS

Mine for blocks with your macOS wallet and the following instructions.

Open Spotlight Search and type the following:

terminal

Click on terminal.

Execute the following command, to open your downloads directory:

cd Downloads

Install Homebrew with the following command:

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

Enter your sudo password to install Homebrew.

Install wget with the following command:

brew install wget

Download your macOS wallet with the following command:

wget "https:sparkplugcoin-qt.dmg" -O sparkplugcoin-qt.dmg

Download the macOS tools for your wallet with the following command:

wget "https://github.com/SparksChain/sparkplug-mac-wallet/raw/main/sparkplugcoin-tools-macos.tar.gz" -O sparkplugcoin-tools-macos.tar.gz

Extract the tar file with the following command:

tar -xzvf sparkplugcoin-tools-macos.tar.gz

Create the data directory for your coin with the following command:

mkdir "$HOME/Library/Application Support/SPARKPLUGCOIN/"

Open nano.

nano "$HOME/Library/Application Support/SPARKPLUGCOIN/sparkplugcoin.conf" -t

Paste the following into nano.

rpcuser=rpc_sparkplugcoin
rpcpassword=dR2oBQ3K1zYMZQtJFZeAerhWxaJ5Lqeq9J2
rpcallowip=127.0.0.1
listen=1
server=1
addnode=node1.sparkschain.network

Save the file with the keyboard shortcut ctrl + x.

Go to the directory sparkplugcoin-tools-macos, with the following command:

cd sparkplugcoin-tools-macos

Open nano.

nano mine.sh -t

Paste the following into nano.

#!/bin/bash
SCRIPT_PATH=`pwd`;
cd $SCRIPT_PATH
echo Press [CTRL+C] to stop mining.
while :
do
./sparkplugcoin-cli generatetoaddress 1 $(./sparkplugcoin-cli getnewaddress)
done

Save the file with the keyboard shortcut ctrl + x.

Make the file executable.

chmod +x mine.sh

Open your downloads directory in Finder.

Install your macOS wallet with the file sparkplugcoin-qt.dmg.

Open your wallet.

Go back to your terminal and execute the following command to mine your first block:

./mine.sh
