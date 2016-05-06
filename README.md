# CS460_Botnet
For our project, we built a p2p botnet. To run you need to install dependencies. You can do this with pip install kademlia which should also install twisted. The botnet needs an existing kademlia network to bootstrap off of, this can be done by running server.tac in the examples folder. Then you can use commander.py to connect and take in commands to send to bots. Botnet.py is the bot that will take and execute commands. 3 needed parts are server.tac, commander.py, and botnet.py.

Step 1: twistd -noy server.tac
step 2: python commander.py [bootstrap ip] [bootstrap port] [commander port]
Step 3: python botnet.py [bootstrap ip] [bootstrap port] [bot port]

We've built a number of example scripts that a bot could run, but this could be modified to make the bot do anything we want. The main idea behind our botnet is that everything is performed through the DHT. By using the DHT for communication, a bot never has to know who its commander is, which protects the botmaster.

botnet.py spawns a p2p node that will communicate with other nodes. Using python kademlia library

keylogger.py - takes in an argument for a logging directory and will create log files in that folder. Each log file will be named based off the window that key was recording from. This makes it easier to interprete what program was using what keystrokes.

ddos.py - Takes in two arguments (hostname and port) and will establish 4 connections to the target in seperate threads. Each connection will then spam 1 million GET requests to the target address in an attempt to overload the server.

upload.py
Use: python upload.py [host] [port] [filepath]
Requires requests library. Can be installed from: pip install requests
Uploads the file at filepath to target server using multipart/form-data Post request

download.py
Use: python download.py [host] [port] [filepath]
GET requests file from target server

fileserver.py
Use: python fileserver.py [port]
Simple HTTPServer to handle GET/download requests and POST/upload requests. GET requests pull files from the filehost directory. Upload request files get stored in /filedump/[client_ip] directory.
