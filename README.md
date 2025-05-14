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

---
### Simulate Slow Subscriber
![image](https://github.com/user-attachments/assets/6c60684f-c4eb-49e2-9944-f860bd50c9ad)
Queued message yang terlihat di RabbitMQ saya mencapai ~11 messages. Hal ini terjadi karena saya menjalankan 3x cargo run secara bersamaan sementara terdapat thread sleep `thread::sleep(ten_millis);` yang menyebabkan thread akan tidur selama beberapa milisecond sebelum mengirimkan pesan yang lain. Kira kira akan ada sebanyak (N-1) * K messages yang queued dimana N adalah jumlah run dan K adalah jumlah message.

### Simulate Many Subscribers
![image](https://github.com/user-attachments/assets/4282f9e6-f3d1-4b5c-a920-dff115c1a28d)

---

![image](https://github.com/user-attachments/assets/5392cdf4-00ef-4e6e-8692-ef41edfd8ee5)

Penurunan chart yang queued messages adalah karena publisher mengirim data lebih cepat daripada yang subscriber bisa proses. Karena adanya delay lewat thread sleep, lonjakan message terjadi sehingga queued message bisa melonjak naik. Namun seiring berjalannya waktu, message dapat diproses dan chart kembali turun. 

Beberapa hal yang dapat diimprove adalah dengan mengganti `println!` dengan Logging, ditambahnya error handling contohnya pada `publish_event` ketika fungsi tersebut gagal mengirimkan pesan ke subscriber. Dapat digunakan message parallelism dengan menggunakan `thread::spawn` atau async handler. 
