# Understanding publisher and message broker
a. How many data your publisher program will send to the message broker in onerun?

Pada program sebelumnya, publisher_event digunakan selama 5x. Untuk masing-masing pemanggilan method publisher dikirimkan berupa `UserCreatedEventMessage` dengan `user_id` dan `user_name`. Pesan yang dikirimkan adalah sebagai berikut: <br>
    1. User ID: "1", Nama Pengguna: "2206828140-Amir" <br>
    2. User ID: "2", Nama Pengguna: "2206828140-Budi" <br>
    3. User ID: "3", Nama Pengguna: "2206828140-Cica" <br>
    4. User ID: "4", Nama Pengguna: "2206828140-Dira" <br>
    5. User ID: "5", Nama Pengguna: "2206828140-Emir" <br>

b. The url of: `amqp://guest:guest@localhost:5672` is the same as in the subscriber program, what does it mean?

Maksud dari `amqp://guest:guest@localhost:5672` di program *publisher* yang sama dengan di program *subscriber* dalam arsitektur AMQP adalah bahwa kedua program tersebut dikonfigurasi untuk terhubung ke broker pesan AMQP yang sama, yaitu RabbitMQ, yang di-hosting pada mesin lokal. Dalam kasus ini, program *publisher* bertugas mengirimkan pesan ke queue pada RabbitMQ, sementara program *subscriber* akan mengatur *listener* untuk menerima atau mengambil pesan dari queue tersebut.

Ini menunjukkan bahwa keduanya berinteraksi melalui RabbitMQ sebagai titik koordinasi pusat, dimana *publisher* mengirim pesan dan *subscriber* menunggu dan memproses pesan yang diterima. Karena itu, keduanya harus terhubung ke broker yang sama agar komunikasi ini berfungsi dengan efektif.

Lampiran Running RabbitMQ <br>
![Running RabbitMQ](image.png) <br>

Lampiran screen show console <br>
![Sending and processing event](image2.png)<br>

Setelah *publisher* di *run*, maka data-data dari *publisher* yang telah di *hard code* akan dikirim ke message queue. Lalu Subscriber akan menerima data tersebut dari message queue dan menampilkan pesan pada lampiran di atas.

