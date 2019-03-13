Author:         Masroor Hussain Syed
Class:          CPSC 418
UCID:           30023900

Files:
    1) Client.java
    2) CryptoUtilities.java
    3) Server.java
    4) ServerThread.java

Compiling:
1) run cmd javac *.java

Running:
1) First run the server with java Server <portnum> <debug>
2) run the client with java Client <server hostname> <portnum> <debug>

Testing:
The program was test on the linux server in the lab. No bugs are Known.

Program Description.
This program is the same as assignment 2 excpet now there is no pre-agreed key for the encryption
and decryption. 
The following changes were made to the profs. solution for assignment 2.

- Server.java
    This program acts as a server and manages connections to the client
- ServerThread.java
    - The server first finds a safe prime and a primitive root of that prime using the methods 
      disscussed in class.
    - Now with this prime and the primitive root of this prime, the serverThread and client generate a 
      common key used for encryption and decryption using diffie-helman key exchange algorithm. 
    
    This program performs the following cryptographic operations on the message from the client:
    -  decrypt the file with its digest appended using AES-128-CBC and a randomly generated key,
       that was recieved from the client, check for Integrity and send an ack to client
    -  using SHA1 as the message authentication procedure
    -  CBC as the mode of operation of your encryption and decryption algorithm.

- Client.java
   - The client gets the the safe prime and the primitive root of that prime.
   - Then using diffie-helman key exchange algorithm, generates the same key as the serverThread.
    
    This program performs the following cryptographic operations on the input file:
    -  encrypts the file with its digest appended using AES-128-CBC and a randomly generated key, and
       sends it to the server
    -  using SHA1 as the message authentication procedure
    -  CBC as the mode of operation of your encryption and decryption algorithm.

- CryptoUtilities.java
    Contains useful utility functions for the assignemet-provided on d2l.
