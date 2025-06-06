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
![Gambar 1](./static/G1.png)

# Sending and processing event.
![Gambar 2](./static/G2.png)

# Monitoring chart based on publisher.
![Gambar 3](./static/G3.png)

The spike shows a rapid increase in messages published to the `user_created` queue. Each time the publisher is run, it sends multiple events to RabbitMQ, which causes the spike seen on the chart.

# Simulation slow subscriber
![Gambar 4](./static/G4.png)

In my machine, the total number of messages in the queue was 15. This happened because I ran the publisher 4 times consecutively, and each time it sent 5 events. Since the subscriber processes messages slowly (one-by-one), they get queued up. The spike in queue length shows that the producer can generate messages faster than the consumer can handle them because of the delay of 1 second, thus generate the spike in queue length

# Reflection and Running at least three subscribers
![Gambar 5](./static/G5.png)

As can seen because now there is three subscriber the response are processing in paraller thus lowering the time it takes to process it's of each publisher response