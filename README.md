### Rack-TCP
## Rack server class for CodePlatoon B Platoon

# First, create a file that lets you find your IP address from the command line.

<li>in: ~/username/bin create a file that looks like myip</br>
<li>make it executable with chmod</br>
<li>this will allow you to type in myip from the command line to see your ip address. Basically, talking across the network

# Next we will talk a little bit about Server/Client

## Server
# The server waits for requests and sends responses
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
server.close
```

## Client
## The client opens a socket to the server, sends a request, and reads a response
```
require = 'socket'                      # code is in the standard library
host = 'localhost'                      # you could also put "google.com here and then print an http request
port = 3001                             # protip: default port for internet servers is 80

socket = TCPSocket.new host, port       # connect
socket.puts "hellow!\nworld"            # same as printing to $stdout
socket.gets                             # same as reading from $stdin
socket.close                            # disconnect
```
## Example HTTP Request
### Here, we're going to format the strings we send in a format known as HTTP. </br>When we connect to Google, we'll request a search for "ruby",</br> This is what your browser sends and recieves if you click https://www.google.com/search?q=ruby.
```
require 'socket'

# Connect to Google on the default internet port
socket = TCPSocket.new 'google.com', 80

# Send an HTTP request
socket.print "Get /search?q=ruby HTTP/1.1\r\n"  # Path of a search
socket.print "\r\n"                             # No headers

# Read the response
socket.gets                                     # => "HTTP/1.1 200 OK\r\n"
loop do
  line = socket.gets
  # => "Date: Mon, 07 Mar 2016 14:39:59 GMT\r\n"
  #    ,"Expires: -1\r\n"
  #    ,"Cache-Control: private, max-age=0\r\n"
  #    ,"P3P: CP=\"This is not a P3P policy! See https://www.google.com/support/accounts/answer/151657?hl=en for more info.\"\r\n"
  #    ,"Server: gws\r\n"
  #    ,"X-XSS-Protection: 1; mode=block\r\n"
  #    ,"X-Frame-Options: SAMEORIGIN\r\n"
  #    ,"Set-Cookie: NID=77=0Xmp6k5XNFcFC8gMcUWo5KTh4vmDUvjDvo7QpSdPvL-ozSfLKhU-MOSr65rvP6IhvSltmgbvr-PJquKJtvy4e7NX6HiBMyWn-jr0IHkfem0vc-JXDGrgCqlbXFuTlk1etEjAXgYuy1BEQg; expires=Tue, 06-Sep-2016 14:39:59 GMT; path=/; domain=.google.com; HttpOnly\r\n"
  #    ,"Accept-Ranges: none\r\n"
  #    ,"Vary: Accept-Encoding\r\n"
  #    ,"Transfer-Encoding: chunked\r\n"
  #    ,"\r\n"
  break if line == "\r\n"
end

socket.read 200 # => "8000\r\n<!doctype html><html< itemscope=\"\" itemtype=\"http://schema.org/SearchResultsPage\" lang=\"en\"><head><meta content=\"text/html; charset=UTF-8\" http-equiv=\"Content-Type\"><meta content=\"/images/brandin"

# End the request
socket.close # => nil
```
 

