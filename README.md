# MCollective-Cluster

ActiveMQ Cluster Setup as middleware for MCollective

There are two connectors ActiveMQ and RabbitMQ that could be used as middleware for MCollective client server communication.
And out of which ActiveMQ is best supported though you can use RabbitMQ too.

The thing to focus on here is single instance of ActiveMQ supports around 800 MCollective servers which will suffice the need of most of the organisations. But for larger number servers you will need to setup cluster of ActiveMQ servers depending on the number of clients you are having.

And its very easy to setup. 

#activemq1.xml
It is the main file where you mention how will it distribute the messages among different queues of other activemq instances.

#activemq2.xml
And you just need to replicate activemq2.xml on rest of the activemq instances as much you want.

Also I have included the security check here to restrict only mcollective client to trigger commands to servers and not vice versa by creating 2 users- mcollective & admin, so that you can secure you production environment and control everything from one machine.

#client.cfg
It communicates with the activemq connector as admin user to control all the commands.

#server.cfg
It communicates with the activemq connector as mcollective user just to respond to commands and not to initiate from it.
