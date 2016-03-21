C Language
==

## GCC Compiler

### Upgrade

```sh
    root@edison:~# opkg upgrade packagegroup-core-buildessential
```

### Socket Implementation, Server

    root@edison:~# nano socketserver.c

```C
#include <stdio.h>
#include <stdlib.h>

#include <netdb.h>
#include <netinet/in.h>

#include <string.h>

int main( int argc, char *argv[] ) {
   int sockfd, newsockfd, portno, clilen;
   char buffer[256];
   struct sockaddr_in serv_addr, cli_addr;
   int  n;
   
   /* First call to socket() function */
   sockfd = socket(AF_INET, SOCK_STREAM, 0);
   
   if (sockfd < 0) {
      perror("ERROR opening socket");
      exit(1);
   }
   
   /* Initialize socket structure */
   bzero((char *) &serv_addr, sizeof(serv_addr));
   portno = 5001;
   
   serv_addr.sin_family = AF_INET;
   serv_addr.sin_addr.s_addr = INADDR_ANY;
   serv_addr.sin_port = htons(portno);
   
   /* Now bind the host address using bind() call.*/
   if (bind(sockfd, (struct sockaddr *) &serv_addr, sizeof(serv_addr)) < 0) {
      perror("ERROR on binding");
      exit(1);
   }
      
   /* Now start listening for the clients, here process will
      * go in sleep mode and will wait for the incoming connection
   */
   
   listen(sockfd,5);
   clilen = sizeof(cli_addr);
   
   /* Accept actual connection from the client */
   newsockfd = accept(sockfd, (struct sockaddr *)&cli_addr, &clilen);
	
   if (newsockfd < 0) {
      perror("ERROR on accept");
      exit(1);
   }
   
   /* If connection is established then start communicating */
   bzero(buffer,256);
   n = read( newsockfd,buffer,255 );
   
   if (n < 0) {
      perror("ERROR reading from socket");
      exit(1);
   }
   
   printf("I am the Server, here is the message: %s\n",buffer);
   
   /* Write a response to the client */
   n = write(newsockfd,"I got your message",18);
   
   if (n < 0) {
      perror("ERROR writing to socket");
      exit(1);
   }
      
   return 0;
}
```
    
    root@edison:~# gcc socketserver.c -o socketserver

### Socket Implementation, Client

```C
#include <stdio.h>
#include <stdlib.h>

#include <netdb.h>
#include <netinet/in.h>

#include <string.h>

int main(int argc, char *argv[]) {
   int sockfd, portno, n;
   struct sockaddr_in serv_addr;
   struct hostent *server;
   
   char buffer[256];
   
   if (argc < 3) {
      fprintf(stderr,"usage %s hostname port\n", argv[0]);
      exit(0);
   }
	
   portno = atoi(argv[2]);
   
   /* Create a socket point */
   sockfd = socket(AF_INET, SOCK_STREAM, 0);
   
   if (sockfd < 0) {
      perror("ERROR opening socket");
      exit(1);
   }
	
   server = gethostbyname(argv[1]);
   
   if (server == NULL) {
      fprintf(stderr,"ERROR, no such host\n");
      exit(0);
   }
   
   bzero((char *) &serv_addr, sizeof(serv_addr));
   serv_addr.sin_family = AF_INET;
   bcopy((char *)server->h_addr, (char *)&serv_addr.sin_addr.s_addr, server->h_length);
   serv_addr.sin_port = htons(portno);
   
   /* Now connect to the server */
   if (connect(sockfd, (struct sockaddr*)&serv_addr, sizeof(serv_addr)) < 0) {
      perror("ERROR connecting");
      exit(1);
   }
   
   /* Now ask for a message from the user, this message
    * will be read by server
    */
	
   printf("Please enter the message: ");
   bzero(buffer,256);
   fgets(buffer,255,stdin);
   
   /* Send message to the server */
   n = write(sockfd, buffer, strlen(buffer));
   
   if (n < 0) {
      perror("ERROR writing to socket");
      exit(1);
   }
   
   /* Now read server response */
   bzero(buffer,256);
   n = read(sockfd, buffer, 255);
   
   if (n < 0) {
      perror("ERROR reading from socket");
      exit(1);
   }
	
   printf("I am the Client, message sent: %s\n",buffer);
   return 0;
}
```

```sh
    root@edison:~# gcc socketclient.c -o socketclient
```

### Socket Implementation, Test

```sh
    root@edison:~# ./socketserver &
    root@edison:~# ./socketclient 192.168.1.74 5001
```

## Native Compilation, G++ Compiler

```sh
    root@edison:~# g++
    g++: fatal error: no input files
    compilation terminated.
```

## Flask

> Flask is a microframework for Python based on Werkzeug, Jinja 2 and good intentions.

- [Flask Homepage](http://flask.pocoo.org/)

```sh
    root@edison:~# pip install Flask
    root@edison:~# apt-get install python-flask
    root@edison:~# nano myflask.py 
```

```Python
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello World!"

if __name__ == "__main__":
    app.run(host='0.0.0.0', port=5000, debug=True, threaded=True)
```

```sh
    root@edison:~# python myflask.py
    * Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
    * Restarting with stat
    192.168.1.73 - - [18/Oct/2015 16:34:56] "GET / HTTP/1.1" 200 -
    192.168.1.73 - - [18/Oct/2015 16:34:56] "GET /favicon.ico HTTP/1.1" 404 -
    192.168.1.73 - - [18/Oct/2015 16:34:56] "GET /favicon.ico HTTP/1.1" 404 -
```

## Others

```sh
    root@edison:~# journalctl 
    root@edison:~# cat /etc/modprobe.d/bcm4334x.conf 
    options bcm4334x firmware_path=/etc/firmware/fw_bcmdhd.bin nvram_path=/etc/firmware/bcmdhd.cal op_mode=4
    root@edison:~# cat /etc/modprobe.d/g_multi.conf  
    options g_multi file=/dev/mmcblk0p9 stall=0 idVendor=0x8087 idProduct=0x0A9E iProduct=Edison iManufacturer=Intel
```

## Links

- [Intel® Edison Native Application Guide](http://www.intel.com/support/edison/sb/CS-035382.htm)
- http://dev.ardupilot.com/wiki/edison-for-drones/
- https://github.com/catmaker/chippy
- https://github.com/MakersTeam/Edison
- https://github.com/tokoro10g/galileo-makefile
- https://software.intel.com/en-us/articles/opencv-300-ipp-tbb-enabled-on-yocto-with-intel-edison
- http://flask.pocoo.org/

