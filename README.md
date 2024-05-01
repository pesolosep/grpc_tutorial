<hr>

## REFLECTION

>1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?

Perbedaan utama antara metode RPC unary, server streaming, dan bidirectional streaming terletak uk aliran data, berguna ketika server perlu mentransmisikan kumpulan data besar atau pembaruan yang kontinu. Bidirectional streaming memungkinkan baik pada pola komunikasi dan kasus penggunaan yang sesuai. Unary gRPC melibatkan satu permintaan dari klien ke server, diikuti oleh satu respons, membuatnya ideal untuk skenario yang membutuhkan pertukaran data tunggal. Server streaming memungkinkan server untuk mengirimkan beberapa respons ke klien dalam bentklien maupun server untuk mengirimkan beberapa pesan satu sama lain dalam aliran yang kontinu, memfasilitasi komunikasi interaktif secara real-time antara keduanya.

>2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?

Saat mengimplementasikan layanan gRPC di Rust, beberapa pertimbangan keamanan muncul yaitu otentikasi, otorisasi, dan enkripsi data. Mekanisme otentikasi dan otorisasi seperti token OAuth atau JSON Web Tokens (JWT) memastikan verifikasi saling antara klien dan server, memberikan akses hanya kepada klien yang diizinkan. Enkripsi data, biasanya dicapai melalui Transport Layer Security (TLS), melindungi data yang ditransmisikan dari serangan oleh pihak yang tidak diinginkan.

>3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications?

Mengelola streaming bidirectional di Rust gRPC, terutama dalam skenario tutorial (chat service) dapat menimbulkan berbagai tantangan. Bisa terjadi manajemen memori yang cermat untuk mencegah kebocoran memori, implementasi langkah-langkah keamanan data seperti enkripsi dan otentikasi untuk melindungi pesan pribadi, manajemen konkurensi yang efektif untuk menangani pesan dengan benar, penanganan kesalahan yang tangguh untuk mengatasi situasi yang tidak terduga, dan manajemen koneksi yang efisien untuk komunikasi yang lancar antara klien dan server.

>4. What are the advantages and disadvantages of using the tokio_stream::wrappers::ReceiverStream for streaming responses in Rust gRPC services?

Memanfaatkan `tokio_stream::wrappers::ReceiverStream` untuk streaming respons di layanan Rust gRPC menawarkan integrasi dengan Tokio dan fleksibilitas dalam mengelola aliran data dari saluran mpsc, memungkinkan pemrosesan asinkron dan responsif. Namun, mungkin memiliki keterbatasan dalam fungsionalitas bawaan dibandingkan solusi streaming lainnya dan memerlukan manajemen saluran mpsc yang hati-hati untuk menghindari kebocoran memori atau kondisi mati.

>5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?

Untuk menjamin bahwa layanan gRPC di Rust dapat diperluas dan dipelihara dengan mudah, penting untuk memanfaatkan perpustakaan yang tersedia guna mengulang penggunaan dan pemeliharaan kode. Mengadopsi pendekatan desain yang modular, dengan mengorganisir kode ke dalam unit-unit modul yang memiliki tanggung jawab yang terdefinisi dengan baik, akan sangat membantu. Selain itu, memanfaatkan fitur-fitur yang memungkinkan pembuatan antarmuka yang efisien dan dapat digunakan kembali juga akan meningkatkan kualitas keseluruhan layanan.

>6. In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic?

Untuk mengelola proses pembayaran yang kompleks, kita bisa memperbaiki `MyPaymentService` dengan mengubah fungsi `process_payment` menjadi layanan streaming. Ini akan memungkinkan kita untuk mengirimkan data ke klien secara bertahap dan efisien, sehingga memfasilitasi transfer informasi yang lebih rumit.

>7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?

Mengadopsi gRPC sebagai protokol komunikasi meningkatkan arsitektur dan desain keseluruhan sistem terdistribusi dengan mempromosikan modularitas dan efisiensi, memfasilitasi komunikasi yang lebih lancar antara layanan-layanan yang beragam bahkan di berbagai bahasa pemrograman atau platform, sehingga mengurangi hambatan interoperabilitas dan memungkinkan integrasi yang efektif dengan teknologi dan platform lainnya.

>8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?

Menggunakan HTTP/2 sebagai protokol dasar untuk gRPC memiliki keuntungan multiplexing, kompresi header, dan server push yang meningkatkan efisiensi dan kecepatan komunikasi. Namun, kompleksitas implementasi yang lebih tinggi dan dukungan yang terbatas di beberapa server dan klien mungkin menjadi kelemahan dibanding ketika memakai HTTP/1.1 baik dengan WebSocket for REST APIs maupun tidak.

>9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?

REST API dikenal karena kemudahannya dalam penggunaan dengan menggunakan metode HTTP yang umum dan bersifat stateless. Namun, kelemahannya terletak pada kurangnya dukungan untuk komunikasi real-time, sering kali memerlukan polling atau long-polling yang dapat meningkatkan kompleksitas dan latensi. Di sisi lain, gRPC menawarkan fitur streaming dua arah yang memungkinkan klien dan server untuk saling mengirim data secara independen, menjadikannya pilihan yang lebih sesuai untuk kasus penggunaan real-time dan meningkatkan responsivitas. Meskipun lebih kompleks, streaming dua arah yang ditawarkan oleh gRPC dapat memberikan performa yang lebih baik dan keuntungan dalam komunikasi real-time dibandingkan dengan REST API untuk beberapa skenario tertentu.

>10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?

gRPC dan Protocol Buffers memberikan keunggulan dalam hal kompatibilitas dan efisiensi karena strukturnya yang berbasis skema. Di sisi lain, JSON yang digunakan dalam REST API menawarkan fleksibilitas dan kemudahan dalam pembacaan lintas bahasa dan platform, meskipun kadang-kadang dapat mengakibatkan biaya lebih besar. Dalam konteks Indonesia, gRPC lebih cocok digunakan dalam situasi yang membutuhkan tipedata yang ketat.