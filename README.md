## Tutorial 9 Adpro - Subscriber
---
1. What is ampq?
AMQP atau Advanced Message Queuing Protocol adalah protokol komunikasi berbasis pesan yang dirancang untuk mentransfer data antar sistem yang tersebar (terdistribusi).
Protokol ini sering dimanfaatkan dalam sistem message queue seperti RabbitMQ untuk menjamin pertukaran pesan yang andal, terstruktur, dan memungkinkan pemisahan peran
antara pengirim (producer) dan penerima (consumer) dalam arsitektur sistem.

2. What does it mean? guest:guest@localhost:5672 , what is the first guest, and what
is the second guest, and what is localhost:5672 is for?
'guest' pertama adalah username untuk login ke RabbitMQ server dimana 'guest' adalah username default yang dibuat oleh RabbitMQ. 'guest' kedua adalah password untuk login yang
merupakan default password juga. Sementara localhost:5672 adalah server address dan server port dimana localhost adalah tempat RabbitMQ run di browser serta
5672 adalah default port dari RabbitMQ
