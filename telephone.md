We're going to pass messages through all the students!

Arrange yourselves in a circle so that the person you're sending messages to is on your left,
and that you're receiving messages from is on your right.

Take a moment to write down on paper "I am a *client* of [person to your left],
I am a *server* of [person to your right]". Contemplate their spatial proximity,
and their responsibility of a client you are the server to, or a server you are the client to.

Take a look at the [tcp sockets](https://github.com/CodePlatoon/curriculum/blob/master/phase1/tcp_sockets.md)
example. How many variables are there going to be to get connected? What are you going to name them?
Now start your server on the ip you previously found, give your ip and port to your client,
ask your server for their ip and port. Coordinate with the people around you so this goes smoothly:

* accept your client's socket into the variable you named after them,
* connect to the server, saving the socket into the variable you named after them..

Make sure the person to your right can send you messages.
Make sure the person to your left can receive your messages.


1. Read a message from the person before you, print it to `$stdout`,
   then send it to the person right you. We should all see the message,
   and it should pop up on my screen!
2. Same thing, but prepend your name before printing.
   What will the output look like on my screen?
3. Same thing, but instead of prepending your name, append it.
4. Same thing but both prepend and append your name!
5. This time only PREPEND your name, and pass the message you receive to the next person.
   But instead of only passing it, we'll allow them to send a message back.
   So read from the next person, and THEN APPEND your name and send it back to the person before you!
6. Contemplate!!
