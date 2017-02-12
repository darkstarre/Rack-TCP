### Rack-TCP
## Rack server class for CodePlatoon B Platoon

# First, create a file that lets you find your IP address from the command line.

in: ~/username/bin create a file that looks like myip
make it executable with chmod
this will allow you to type in myip from the command line to see your ip address.

# Next we will talk a little bit about Server/Client

## Server
```
# Register your program to accept requests
require 'socket'                        # code is in the standard library
host = 'localhost'                      # serving from your computer
port = 3001                             # to allow multipl programs to serve content, they each get a number called a "port"
server = TCPServer.new host, port       # make the server

# take a request
socket = server.accept                  # waits until you connect
socket.get                              # read a line (this is the same 'gets' method you call on '$stdin')
socket.read 5                           # read 5 characters from the input
socket.print "hello!"                   # write "hello!" back into the socket (this is the same print you call on `$stdout`")
socket.close                            # close the input and output streams

# unregister your programs
server.close ``` 
