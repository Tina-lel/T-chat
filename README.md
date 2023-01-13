# T-chat
T-chat is a end to end encrypted chat, supporting multiple clients and chat history, using socat's openssl features written entirely in bash.

Dependencies:
-
bash

socat

Ussage:
-
```
git clone https://github.com/Tina-lel/T-chat
```
## server:

```
cd T-chat/server/
```
```
chmod +x *
```

open up "config" in a text editor and choose a port number to replace "1234" and "1235", and optionally forward these ports in your gateways configuration page, to communicate outside of your internal network

```
./server
```

see "Commands" for a list of valid commands

#### generating SSL stuff and running the server:

make sure that when asked for "common name" you enter your host name/ip (for example: 192.168.1.69)
```
gen
```
the files where generated in (script location)/ssl, i guess you should be carefull with them
```
start
```
if everything went fine, and the server didn't return any errors, you can test the connection with a client

## client:

```
cd T-chat/client/
```
```
chmod +x *
```

open up "config" in a text editor and change the "NAME" var. next edit the "HOST", "PORT" and "IPORT" variable, to point to a machine running the "server" script, on the same ports

```
./client
```

see "Commands" for a list of valid commands

#### acquiring the servers SSL certificate and connecting to the server:

copy the servers SSL certificate (found in <script location>/ssl/server.crt on the server side) to the client, move it to <script location>/ssl/, and rename it to the same thing you entered in the $HOST variable in the client config just with a .crt at the end

then, on the client, run:

```
connect
```
if the server was running, and everything went fine, you should now see a blank screen, with a blinking cursor.

in order to chat hit "CTRL+C" and type something, then press enter. for a help message type "!help" and "!exit" to disconnect and exit

Commands:
-

### server:

help: this message

start: start the server

stop: kill the server

gen: generate SSL files

exit: exit the script

### client:

help: this message

connect: connects you to the server
