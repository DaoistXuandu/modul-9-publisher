# Reflection
a. How much data your publisher program will send to the message broker in one run?

In one run, my program will send 5 messages to the message broker. Each message is a UserCreatedEventMessage containing:

user_id (String)
user_name (String)
So, total messages sent: 5 Each goes to the same topic/queue: "user_created".

b. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?

The publisher and the subscriber are both: Using the same RabbitMQ server (located at localhost, which is your own computer), Using the same credentials (username = guest, password = guest), Connecting through port 5672, the default port for AMQP.

Because the URLs are the same, the subscriber will receive all messages the publisher sends to the "user_created" queue.

# Running RabbitMQ as message broker.
[Gambar 1](./static/G1.png)