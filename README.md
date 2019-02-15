# blockchain-training-labs

MANDATORY AND OPTIONAL REQUIREMENTS
USING CHAIN CODE BASED 
NODE.JS APPLICATION


EDWARD CLEDERA ABLES
BLOCKCHAIN CADET



SYSTEM SPECIFICATION

            Machine Name:   ECA-DESKTOP
                  Machine Id:   {59088861-CD5B-4364-9DA6-3893A942143E}
        Operating System:   Linux, Ubuntu 18.04.1  LTS
                     Language:   English (Regional Setting: English)
  System Manufacturer:   Dell Inc.
             System Model:   Inspiron 3459 
                           BIOS:   1.8.0 (type: UEFI)
                     Processor:   Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz (4 CPUs), ~2.4GHz
                      Memory:    8192MB RAM
 Available OS Memory:   8052MB RAM
           DirectX Version:   DirectX 12

INSTALLATION SET UP
	Hyperledger Composer is an extensive, open development toolset and framework to make developing blockchain applications easier. Our primary goal is to accelerate time to value, and make it easier to integrate your blockchain applications with the existing business systems. 

Note: Before you begin let us set up first the pre-requisites of Hyperledger Composer to go deeper of  
          the installation of it.

Installing Pre-requisites
The following are prerequisites for installing the required development tools:
    • Operating Systems: Ubuntu Linux 14.04 / 16.04 LTS (both 64-bit)
    • Docker Engine: Version 17.03 or higher
             First, update your existing list of packages:
    • sudo apt update

      Next, install a few prerequisite packages which let apt use packages over HTTPS:
    • sudo apt install apt-transport-https ca-certificates curl software-properties-common
      Then add the GPG key for the official Docker repository to your system:
    • curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
      Add the Docker repository to APT sources:
    • sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
      Next, update the package database with the Docker packages from the newly added repo:
    • sudo apt update
      Make sure you are about to install from the Docker repo instead of the default Ubuntu repo:
    • apt-cache policy docker-ce
       Notice that docker-ce is not installed, but the candidate for installation is from the Docker repository for Ubuntu 18.04 (bionic).
      Finally, install Docker:
    • sudo apt install docker-ce
       Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it's   
       running:
    • sudo systemctl status docker
      The output should be similar to the following, showing that the service is active and running:
      Output
 	docker.service - Docker Application Container Engine
  	  Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
   	     Active: active (running) since Thu 2018-07-05 15:08:39 UTC; 2min 55s ago
   	        Docs: https://docs.docker.com
 	           Main PID: 10096 (dockerd)
    	           Tasks: 16
   		CGroup: /system.slice/docker.service
    		       ├─10096 /usr/bin/dockerd -H fd://
    		       └─10113 docker-containerd --config /var/run/docker/containerd/containerd.toml

    • Docker-Compose: Version 1.8 or higher
    • curl -O https://hyperledger.github.io/composer/latest/prereqs-ubuntu.sh 
    • chmod u+x prereqs-ubuntu.sh
    • ./prereqs-ubuntu.sh
      
    • Node: 8.9 or higher (Note: version 9 and higher is not supported)
            Start by updating the packages list by typing:
    • sudo apt update
      Install nodejs using the apt package manager:
    • sudo apt install nodejs npm
    • Node Package Manager: v5.x
            To be able to download npm packages, you also need to install npm, the Node.js package manager. 
    • sudo apt install npm
            Verify the installation by typing:
    • npm --version
    • Git: 2.9.x or higher
            First we will be installing git on Ubuntu from its standard repository. 
    • ubuntu:~$ sudo apt -y install git
      Once ready you can check for a correct git installation by retrieving git's version:
    • git –version
    • Python: 2.7.x
      Ubuntu 18.04 ships with both Python 3 and Python 2 pre-installed. 
    • sudo apt update
    • sudo apt -y upgrade
The -y flag will confirm that we are agreeing that all items to be installed, but depending on your version of Linux, you may need to confirm additional prompts as your system updates and upgrades.
Once the process is complete, we can check the version of Python 3 that is installed in the system by typing:
    • python3 -V
    • Code Editor: Visual Studio Code
    • Install VSCode by visiting: https://code.visualstudio.com

Note: You should not use su or sudo for the following npm commands.

Installing the Development Environment

Step 1: Install the CLI tools
	There are a few useful CLI tools for Composer developers. The most important one is composer-cli, which contains all the essential operations, so we'll install that first. Next, we'll also pick up generator-hyperledger-composer, composer-rest-server and Yeoman. Those last 3 are not core parts of the development environment, but they'll be useful if you're following the tutorials or developing applications that interact with your Business Network, so we'll get them installed now.

Essential CLI tools:
    • npm install -g composer-cli@0.20

Utility for running a REST Server on your machine to expose your business networks as RESTful APIs:
    • npm install -g composer-rest-server@0.20
Useful utility for generating application assets:
    • npm install -g generator-hyperledger-composer@0.20
       Yeoman is a tool for generating applications, which utilises generator-hyperledger-composer:
    • npm install -g yo

Step 2: Install Playground
	If you've already tried Composer online, you'll have seen the browser app "Playground". You can run this locally on your development machine too, giving you a UI for viewing and demonstrating your business networks.
       Browser app for simple editing and testing Business Networks:
    • npm install -g composer-playground@0.20

Step 3: Set up your IDE
	Whilst the browser app can be used to work on your Business Network code, most users will prefer to work in an IDE. Our favourite is VSCode, because a Composer extension is available.
    • Install VSCode from this URL: https://code.visualstudio.com/download
    • Open VSCode, go to Extensions, then search for and install the Hyperledger Composer extension from the Marketplace.
      
Step 4: Install Hyperledger Fabric
	This step gives you a local Hyperledger Fabric runtime to deploy your business networks to.
In a directory of your choice (we will assume ~/fabric-dev-servers), get the .tar.gz file that contains the tools to install Hyperledger Fabric:
    • mkdir ~/fabric-dev-servers && cd ~/fabric-dev-servers
    • curl -O https://raw.githubusercontent.com/hyperledger/composer-tools/master/packages/fabric-dev-servers/fabric-dev-servers.tar.gz
    • tar -xvf fabric-dev-servers.tar.gz
Use the scripts you just downloaded and extracted to download a local Hyperledger Fabric v1.2 runtime:
    • cd ~/fabric-dev-servers
    • export FABRIC_VERSION=hlfv12
    • ./downloadFabric.sh

Start the web app ("Playground")
To start the web app, run:
    • composer-playground
It will typically open your browser automatically, at the following address: http://localhost:8080/login

CONFIGURATION SET UP
First, we should be able to clone the fabric sample for setting up its environment to build and create a new sample apps. Then, clone also the blockchain training labs for accessing a chain code supply for the said mandatory assignment.  
    • Cloning Repository Fabric Samples
Open Terminal and type 
git clone https://github.com/hyperledger/fabric-samples.git 
    • Cloning Repository Blockchain Training Labs
Open Terminal and type
git clone  https://github.com/khrandm/blockchain-training-labs.git

	Second, In blockchain training labs folder copy the chaincode and supply folder and paste it inside the fabric samples folder to merge the file and easy to configure the mandatory assignments.
    • 
Copy then Paste
	Third, Download the required library for our chaincode and GO language must be installed of it. And type this to terminal.
	go get github.com/golang/protobuf/proto
	go get github.com/hyperledger/fabric/common/attrmgr
	go get github.com/pkg/errors
	go get github.com/hyperledger/fabric/core/chaincode/lib/cid

	Then, Open the fie manager and go to Home/go/src/github.com and copy the all three folders and paste it inside the fabric-samples/chaincode.
	hyperledger
	pkg
	golang
  
	Fourth, Accessing the fabric samples folder and configure the chaincode and install then set up all environments for each project.
    • Install and enroll all its components
Start the said environment project using
./startFabric.sh

Open Terminal in supply folder located in fabric samples 
ls
	On its terminal install the Node Package Manager
		npm install

	Then, enroll the Admin.js using 
		node  enrollAdmin.js
    
	Then, Register its user
		node registerSupplier.js
    
	Then, Register OEM its user
		node registerOEM.js

	Then, Register Bank on its user.
		node registerBank.js
	
	Then, run the said application.
		node app.js
    
	Fifth, Testing and try the application using Postman to see the output of the work and if it is running or not.
    • Creating an Invoice and its attributes.
Open postman and you should see a GET entitled request and change method from GET to POST.
Add URL locahost:3000/invoice below URL you should see Params, Authorization, Headers, Body and click Headers.
Add another key below Content-Type then type user and the value would be the supplier next open the body tab and click the x-www-form-url-encoded

	Then, create an invoice  attributes using POST function  in localhost:3000/invoice the click send 
		invoicenumber:INVOICE001
		billedto:OEM
		invoicedate:02/08/19
		invoiceamount:10000
		itemdescription:KEYBOARD
		goodreceived:False
		ispaid:False
		paidamount:0
		repaid:False
		repaymentamount:0

And it will show a result success.

Then, to view and see the invoice attribute that we create use GET the click send on localhost:3000 it will show the all attribute.

	Then, go to GET localhost:3000 on header add user with value of supplier now hit send to see your invoices in the respond below.

Declaring goodreceived 
	beside POST localhost:3000/invoice click the plus sign
	change the method to PUT and localhost:3000/invoice
	Go to header tab and add user with value of oem

	Next go to body x-www-form-urlencoded add these data
		Invoicenumber           INVOICE001
		goodreceived            True

	Now hit the send and you should see result : success

	Then, Bank will pay the supplier
	Add another request PUT method and localhost:3000/invoice and on header tab add user with value of bank

	now on body tab x-www-form and add these data
		invoicenumber           INVOICE001
		paidamount              9000      

	go to GET localhost:3000 tab then hit send  then check if data is updated
	the invoice will idicate that the isPaid = true and the paidamount will be 9000 


	OEM will pay the bank
	add another request PUT method localhost:3000/invoice

	On header tab add user with value of oem and now on body tab x-www-form then add these data
		invoicenumber           INVOICE001
		repaymentamount         11000
	Go to GET localhost:3000 tab then hit send 
	then check if data is updated

	Lets check invoice audit trail
	add another request GET localhost:3000 and on header add user with value of supplier
now on body x-www-form add invoicenumber with value of INVOICE001

	Then that would be all . Thank You!!!
