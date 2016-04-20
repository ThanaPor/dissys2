-------------------------------------------------------------------------------------------------
TABLE OF CONTENTS
-------------------------------------------------------------------------------------------------

1. Introduction
2. Installing Node.js
3. Installing MongoDB
4. Configuring MongoDB
5. Running MongoDB
6. Intalling the Dependencies
7. Starting your Node.js Server (i.e. "server.js")
8. Troubleshooting



-------------------------------------------------------------------------------------------------
1. INTRODUCTION
-------------------------------------------------------------------------------------------------

Each tutorial comes with a complete set of project files that covers everything up until the end of the lesson, including the code from previous tutorials.

For the first installation, you'll need to:

* download and extract the .zip file
* save and rename the project folder to your hard drive (for convenience, I recommend your desktop)
* install and configure Node.js
* install and configure MongoDB
* install the required node modules

The above steps will only need to be performed once. For subsequent tutorial downloads, simply drag and drop the "Client" and "Server" files into your existing project folder, and when prompted, choose to overwrite the existing files.



-------------------------------------------------------------------------------------------------
2. INSTALLING NODE.JS
-------------------------------------------------------------------------------------------------

1. Go to www.nodejs.org/download/
2. Click on the correct tab for your development platform
3. Follow the installation prompts



-------------------------------------------------------------------------------------------------
3. INSTALLING MONGODB
-------------------------------------------------------------------------------------------------

1. Go to www.mongodb.org/downloads
2. Click the correct tab for your development platform
3. Click "run", and follow the prompts
4. When the "installation type" screen comes up, choose "custom"
5. Change the target path name to "C:\MongoDB" to install to your root directory



-------------------------------------------------------------------------------------------------
4. CONFIGURING MONGODB
-------------------------------------------------------------------------------------------------



ADD DATA FOLDERS
----------------

1. Open File Exploror
2. Navigate to the MongoDB folder you created during the installation process
3. Add three subfolders: (1) "data", (2) "conf", and (3) "log"
4. Open the "data" folder and add a sub-folder named "db"



CREATE A CONFIGURATION FILE
---------------------------

1. Open your text editor and enter the following code:

    # mongodb.conf

    # point mongodb to the data directory
    dbpath=C:\mongodb\data\db

    # tell it where to log messages
    logpath=C:\mongodb\log\mongodb.log
    logappend=true

    # only run on localhost
    bind_ip = 127.0.0.1                                                             

    port = 27017
    rest = true

2. Save the file as "mongodb.conf" in your "conf" folder.



ADD MONGODB AS A SERVICE
------------------------

1. Open your Command Prompt as an adiministrator.
2. Navigate to "C:\MongoDB\bin"
3. Enter the following command:

    mongod.exe —install —config C:\MongoDB\conf\mongodb.conf —logpath C:\MongoDB\log\mongodb.log
    
NOTE: If the service doesn't start automatically, you can manually start it by typing "net start MongoDB".



-------------------------------------------------------------------------------------------------
5. RUNNING MONGODB
-------------------------------------------------------------------------------------------------

To start MongoDB:

1. Open Command Prompt
2. Navigate to "C:\MongoDB\bin"
3. Type "mongo.exe" to start 



-------------------------------------------------------------------------------------------------
6. INSTALLING THE DEPENDENCIES
-------------------------------------------------------------------------------------------------
	
To make your application run, you'll need to install the necessary APIs to your project folder.

1. Open your Command Prompt
2. Navigate to your renamed project folder
3. Type "npm install socket.io" to install the Socket.IO API
4. When this completes, type "npm install mongodb" to install the MongoDB API



-------------------------------------------------------------------------------------------------
7. STARTING YOUR NODE.JS SERVER
-------------------------------------------------------------------------------------------------

1. Navigate to the "Server" file inside your renamed project folder.
2. Type "node server.js"



-------------------------------------------------------------------------------------------------
8. TROUBLESHOOTING
-------------------------------------------------------------------------------------------------

NOTE: If you get an error message saying “Failed to load c++ bson extension, using pure JS version”, you can fix this by taking the following steps:

1. Navigate to the “index.js” file in your "node_modules" folder. You can find this file in the following directory in your File Explorer:

    MyFirstNodeApp\node_modules\mongodb\node_modules\mongodb-core\node_modules\bson\node_modules\
    bson-ext\ext\index.js

2. Open this file in a text editor.
3. Locate all the "require" statements in the catch block containing a path to 'bson', and change them from the longer file path to "require('bson');"
4. Save the changes, restart your Command Prompt, and follow the instructions in the "Starting Your Node.js Server" section.
