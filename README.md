## 1. Jumlah Data yang Dikirim Publisher dalam Satu Run

Berdasarkan kode yang diberikan, program Publisher akan mengirimkan lima pesan ke message broker dalam sekali run. Setiap pemanggilan fungsi `p.publish_event` akan mengirim satu pesan, dan dalam program tersebut, fungsi ini dipanggil lima kali. Setiap pesan yang dikirim adalah instance dari `UserCreatedEventMessage` dengan nilai `user_id` dan `user_name` yang berbeda.

## 2. Arti dari URL "amqp://guest:guest@localhost:5672"

URL `amqp://guest:guest@localhost:5672` digunakan untuk menyambungkan program ke sebuah message broker yang menggunakan protokol AMQP. Fakta bahwa URL yang sama digunakan baik di program Publisher maupun Subscriber berarti kedua program akan terhubung ke message broker yang sama.

Rincian dari URL tersebut:

- `guest:guest` adalah nama pengguna dan kata sandi yang digunakan untuk autentikasi ke message broker.
- `localhost` berarti message broker berjalan pada mesin yang sama dengan program yang terhubung.
- `5672` adalah nomor port di mana message broker mendengarkan koneksi AMQP (5672 adalah port default untuk RabbitMQ).

Dengan demikian, baik Publisher maupun Subscriber akan berinteraksi dengan message broker/server yang sama, kemungkinan besar menggunakan antrian pesan yang sama untuk mengirim dan menerima pesan.

# Running RabbitMQ as message broker.
![Alt text](image/ss1.png)

# Sending and processing event.
![Alt text](image/ss2.png)
![Alt text](image/ss3.png)
![Alt text](image/ss4.png)
Publisher mengirim pesan ke RabbitMQ, dan Subscriber mengambil dan memproses pesan-pesan tersebut, sebagaimana yang terlihat di konsol. Ini menunjukkan bagaimana Publisher dan Subscriber berinteraksi menggunakan RabbitMQ sebagai perantara pesan dengan fungsionalitas dasar.

# Monitoring chart based on publisher.
![Alt text](image/ss5.png)
Dengan memperhatikan peningkatan pada grafik RabbitMQ saat melakukan operasi penerbitan berulang, kita dapat secara visual melihat bagaimana aktivitas penerbitan memengaruhi antrian pesan di RabbitMQ. Ini memberikan gambaran yang jelas tentang bagaimana pesan antri dan diproses menggunakan RabbitMQ, yang sangat berguna untuk memahami mekanisme antrian pesan dan pemrosesan dalam konteks RabbitMQ.