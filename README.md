# Mule 4 Client Server Setup to showcase Security Features

## Introduction

A simple client-server setup to showcase the use of Mule 4 Secure Configuration Properties Module, Validation Module and different operations from the Cryptography Module

> **_DISCLAIMER:_** The only purpose of this source code is to showcase the use of different security features in Mule 4, as explained in [this blogpost](https://www.ricston.com/?p=33097&preview=true). **Do not under any circumstance use these applications in a production environment.** The private keys are publically accessible, the public keys are not certified by a Certificate Authority and the author and Ricston Ltd. are not responsible for any problems arising from the use of any part of this source code in a production environment.                  

## Setup

1. Clone this repositry

2. Import both the client and server applications in Anypoint Studio 7.x as "Anypoint Studio project from File System"

3. If you want to change the default client and server application ports (which are 8091 and 8092 respectively), simply change  http.port (client port) and http.server.port (server port) in the client application and change http.port (server port) in the server application from the configuration files located in src/main/resources/config/configuration.yaml.

4. If you want access to the private keys, use the passphrase *RicstonClient* and email *client@ricston.com* for the client's private key and the passphrase *RicstonServer* and email *server@ricston.com* for the server's private key.

5. Set the following two environment variables via Run > Run configurations.. > Environment Tab > New..:
   * *client.secure.properties.key* with value *xcuTsjLBUF8MspmsXbz06wI2TzqZFoSe*
   * *server.secure.properties.key* with value *zCgE0NanJo701CdbPYJCZhELDHNRao5G*

6. Tick the two checkboxes next to the client and server application names in Run > Run configurations.. > General, in order to spin up both applications.

7. Once both client and server applications are successfully deployed, hit the client application with an HTTP POST request with the following body: 

  ```
    {
        "message": "Write any message as a string here"
    }
   ```


8. If everything works correctly, the response should be a JSON file as follows:

   ```
   {
       "signature": <PGP signature of the message as a string>,
       "encryptedMessage": <PGP encrypted message as a string>,
       "decryptedMessage", <The decrypted message sent by the server, which should match exactly the original message>,
       "signatureValidated": true
   } 
   ```
   

