# Mule 4 Client Server Setup to showcase Security Features

## Introduction

A simple client-server setup to showcase the use of Mule 4 Secure Configuration Properties Module, Validation Module and different operations from the Cryptography Module

## Setup

1. Clone this repositry

2. Import both the client and server applications in Anypoint Studio 7.x as "Anypoint Studio project from File System"

3. If you want to change the default client and server application ports (which are 8091 and 8092 respectively), simply change  http.port (client port) and http.server.port (server port) in the client application and change http.port (server port) in the server application from the configuration files located in src/main/resources/config/configuration.yaml.

4. Set the following two environment variables via Run > Run configurations.. > Environment Tab > New..:
  i. *client.secure.properties.key* with value *xcuTsjLBUF8MspmsXbz06wI2TzqZFoSe*
  ii. *server.secure.properties.key* with value *zCgE0NanJo701CdbPYJCZhELDHNRao5G*

5. Tick the two checkboxes next to the client and server application names in Run > Run configurations.. > General, in order to spin up both applications.

6. Once both client and server applications are successfully deployed, hit the client application with an HTTP POST request with the following body: 

  ```
    {
        "message": "Write any message as a string here"
    }
   ```


7. If everything works correctly, the response should be a JSON file as follows:

   ```
   {
       "signature": <PGP signature of the message as a string>,
       "encryptedMessage": <PGP encrypted message as a string>,
       "decryptedMessage", <The decrypted message sent by the server, which should match exactly the original message>,
       "signatureValidated": true
   } 
   ```
