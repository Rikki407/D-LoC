# D-LoC
Hyperledger Fabric Blockchain solution generates decentralized letters of credit for fast transactions, records all events that happen on a port to cross-check and calculate demurrage claims digitally between parties involved.
Digital demurrage claims calculations make transactions faster by enforcing trust via self-executing contracts that lie on the blockchain, thereby reducing the time in dispute resolution and immensely lowers the time taken between transaction.



# Steps To setup or Integrate Hyperledger Fabric
## 1. Install the CLI tools
### 1. Essential CLI tools:
```
npm install -g composer-cli
```
### 2. Utility for running a REST Server on your machine to expose your business networks as RESTful APIs:
```
npm install -g composer-rest-server
```
### 3. Useful utility for generating application assets:
```
npm install -g generator-hyperledger-composer
```
### 4. Yeoman is a tool for generating applications, which utilises generator-hyperledger-composer:
```
npm install -g yo
```
## 2. Install playground or use online  [Composer playground](https://composer-playground.mybluemix.net)
Browser app for simple editing and testing Business Networks:
```
npm install -g composer-playground
```
## 3. Install Hyperledger Fabric
This step gives you a local Hyperledger Fabric runtime to deploy your business networks to.
### 1. In a directory of your choice (we will assume ~/fabric-tools), get the .tar.gz file that contains the tools to install Hyperledger Fabric:
```
mkdir ~/fabric-tools && cd ~/fabric-tools

curl -O https://raw.githubusercontent.com/hyperledger/composer-tools/master/packages/fabric-dev-servers/fabric-dev-servers.tar.gz
tar -xvf fabric-dev-servers.tar.gz
```
### 2. Use the scripts you just downloaded and extracted to download a local Hyperledger Fabric runtime:
```
cd ~/fabric-tools
./downloadFabric.sh
```
## 4. Create a BNA file using YEOMAN framework
```
yo hyperledger-composer:businessnetwork
```

## Prerequisities
* Python 2.7
* Nodejs and npm with node version 8.11.1
* Docker Engine: Version 17.03 or higher



# Steps to run D-LoC
## 1. Run shell scripts from fabric tools
### 1. Run Fabric netwok
```
cd fabric-tools
./startFabric.sh
```
### 2. create a PeerAdminCard
```
./createPeerAdminCard.sh
```
## 2. Install node packages
```
npm install
```
## 3. Create the BNA archive
```
composer archive create  --sourceType dir --sourceName ../
```
## 4. Install a network using archive file
```
composer network install -a ./flipflop@0.0.7.bna -c PeerAdmin@hlfv1
```

## 5. Start a network 
```
composer network start -c PeerAdmin@hlfv1 -n flipflop -V 0.0.7 -A admin -S adminpw
```

## 6. Import the card generated in above step
```
composer card import -f admin@flipflop.card
```
## 7. Final step
```
node app.js
```



