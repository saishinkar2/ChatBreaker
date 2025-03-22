# ChatBreaker

This program enables users to report issues related to their problems directly with a server through a Transmission Control Protocol (TCP) connection. 
The user interacts with the system by entering their name, and phone number, and selecting from a list of provided issues.

# How to Use the Program

# Client-Side Interface

# Starting Up the Program
 
  When the program starts, it will prompt the user to enter the following information:
  <BR>
	Name: Your full name.
  <BR>
	Registered Mobile Number: The phone number associated with the system.
  <BR>
Note: - Entering incorrect or false data will make you request VOID. Please enter the correct information.

# Selecting an option for help
Once you have entered your personal information into the program, a list of options will be presented on the screen. Each option will have a number assigned to it. Review the list carefully and identify the issue that most accurately describes your situation. To select it, simply type the number that corresponds to the issue you have chosen. It will not work if any other number is selected other than the corresponding values.
  
1. Depression
2. Getting Differentiated by School
3. Weak in Academics(You May Need to Describe)
4. Suggestion for Abroad Studies.
5. Financial Suggestions
6. Other

<BR>
	Type a number between 1 and 6 to select your issue. (If you choose the other number, the application will be closed, or you may have to try it out again.)

# Receiving Messages

  The program runs a program in the background from the server. You may receive updates from customer support or notifications about being placed in a "waiting room" for further assistance.
  <BR>
  The program will inform you if you are placed in a waiting room and will automatically check the server to check when you are moved into an active session.
	<BR>
  The waiting room has been provided to make it easier for the assisting personnel to assist you and others at a time.

# Sending Messages

 After the connection is established, you can interact with the support team or system by typing messages into the terminal. Simply type your message and press Enter to send it.

# Exiting 

  You can exit the conversation at any time by closing the program or pressing Ctrl and C at the same time.
 
# Client-Side Commands

Using .queue’ command:-

It gives you an estimate of how long the wait time is.
<BR>
It also gives you the count of people ahead of you in the queue. 
<BR>

 # Server-Side Interface 

 # Socket Setup
 
The server uses Python's socket module to set up a communication line. It is assigned a specific IP address and port number, which act like a phone number for students to call. The server waits for incoming client connections and allows them in the order they arrive. Only one client can talk to the server at a time, while any others that try to connect are put in a waiting list until it is their turn.

# Message Handling

Messages are sent and received in a structured format. Each message consists of two parts:
<BR>
2.1 - Header: Contains the length of the message.
<BR>
2.2 - Message Body: The actual data being transmitted.
<BR>
Messages are encoded and decoded, with proper error handling in case of connection or transmission issues.

# Client Management
<BR>
 3.1) Active Client: Only one client can communicate with the server at any given time.
	<BR>	
 3.2) Waiting Room: Clients attempting to connect while the server is busy are placed in a queue. These clients receive a message indicating their position in the queue.
<BR>
3.3) Session Handover: When the active client disconnects, the next client in the queue is promoted to the active session and notified accordingly.

# Multi-threading
The server uses the threading module to manage multiple clients concurrently:
4.1) Accepting Connections: A separate thread runs the function, continuously listening for incoming messages.
 <BR>
 
# Flow of Operations
5.1) Socket Initialization: The server starts and binds to the specified IP and port, listening for client connections. [You may skip this profession] [only for trained & qualified professionals]
<BR>
5.2) Client Connection: When a client connects, the server checks if there is an active client:
	•	If no active client exists, the new client becomes the active client, and the communication session begins.
	•	If an active client is already connected, the new client is placed in the waiting room and receives a message.

# Message Exchange:
The server administrator can send messages directly to the active client via the server console.
<BR>
The active client sends messages which are printed on the server side.

# Client Disconnection:
When the active client disconnects, the next client in the waiting room is moved to the active client position and notified.

------------------------------------------------------------------
# Error Handling
The server is designed to manage various network errors gracefully:
<BR>
	If the connection to a client is lost, the client socket is closed, and the next client in the waiting room is promoted.
 <BR>
	The client must wait if disconnected.
 <BR>
	During message transmission, if an error occurs, the connection with the problematic client is closed, and the client is removed from the queue if necessary.
 <BR>
  This ensures that the server remains operational even in the presence of network issues, keeping the waiting queue and client sessions orderly.
<BR>
  The server may be closed if there is maintenance or if it is not working as expected.

# Multi-client Support
The program allows multiple clients to attempt connection simultaneously. However, only one client can interact with the server at a time, while others are placed in a queue. The administrator can monitor and manage this queue via the “. room” command.
This ensures that clients are served in the order they arrive and allows the server to manage a controlled flow of interactions, preventing overload or chaotic communication between multiple clients at once.
