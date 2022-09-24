# Tugas 4

## Link to 👉 [Heroku](https://pbp-tugas2-alvaro.herokuapp.com/) 👈

### Soal

#### 1. Apa kegunaan `{% csrf_token %}` pada elemen `<form>`? Apa yang terjadi apabila tidak ada potongan kode tersebut pada elemen `<form>`? <br>
Kegunaan dari `{% csrf_token %}` adalah untuk mencegah serangan pada website kita. Sehingga orang yang tidak mempunyai token tidak dapat melakukan operasi pada object-object yang ada. **CSRF Token** adalah nilai yang bersifat unik, rahasia, dan tidak dapat di prediksi. **CSRF Token** sangat berguna untuk melindung aplikasi kita dari serangan-serangan yang tidak diinginkan artinya penyerang harus memberikan token yang valid untuk meminta request yang valid. Tanpa **CSRF Token** Browser tidak dapat membuat cookie yang bersifat aman dan tidak bisa memberikan authorisasi terhadap akun kita. Contohnya seseorang dapat menipu website kita untuk melakukan suatu aksi seakan seorang user malakukan aksi tersebut. Dengan **CSRF Token** semua bisa teratasi dengan baik dan benar. 

#### 2. Apakah kita dapat membuat elemen <form> secara manual (tanpa menggunakan generator seperti {{ form.as_table }})? Jelaskan secara gambaran besar bagaimana cara membuat <form> secara manual. <br>
Tentu saja kita bisa membuat elemen secara manual tanpa menggunakan generator. Namun apabila kita membuat form kita sendiri akan menyulitkan developer. Seperti yang kita pelajari pada awal-awal minggu di PBP, lebih baik untuk tidak menyulitkan developer, kita bisa saja menggunakan form yang telah disediakan oleh Django itu sendiri. Django memiliki banyak sekali method yang sangat berguna untuk mempermudahkan pekerjaan developer Django. Tanpa generator table, Template Django tidak dapat mengetahui bagaimana cara merender HTML Output. Walaupun kita bisa melihat hasil, namun tidak akan menjadi indah. Saya membuat form saya sendiri dalam mengerjakan `create-task`. Terlihat bahwa akan lebih sulit untuk membuat form sendiri walaupun sudah ada method. 

Saya memberikan gambaran diatas bagaimana kita bisa form bekerja, dan akan saya jelaskan bagaimana form bekerja secara manual. Gambar tersebut saya dapatkan dari [website ini](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms). Apabila kita membuat form secara manual banyak sekali step yang harus dilakukan. Pertama browser harus request page dari form yang ada lalu dari request tersebut form akan diupdate. Setelah diupdate maka form tersebut akan dikirimkan ke URL untuk divalidate datanya apabila belum. Apabila data valid maka browser akan menredirect kita ke URL yang success. Namun apabila gagal, maka Django akan memberikan pesan bahwa data tersebut gagal. 

Oleh karena itu apabila kita membuat form secara manual maka kita harus mengimplementasikan segala sesuatu tersebut. Apabila kita memakai generator maka tugas kita akan jauh lebih cepat diselesaikan. 

#### 3. Jelaskan proses alur data dari submisi yang dilakukan oleh pengguna melalui HTML form, penyimpanan data pada database, hingga munculnya data yang telah disimpan pada template HTML. <br>

Awal-awal user diperintahkan untuk mengisi form yang ada pada saat kita submit maka website tersebut akan meyuruh data untuk di **POST**. Melalui post ini data akan diolah di `views.py` melalui bantuan `urls.py`. Setelah data ini diolah maka kita akan memastikan terlebih dahulu apakah data tersebut sesuai dengan model/form yang diinginkan. Apabila valid/sesuai. Apabila sesuai maka kita save form tersebut ke data base kita dan kemudian kita mengarahkan data tersebut melalui context yang diberikan di `view.py`. Melalui context ini kita bisa menggunakan data untuk dikeluarkan dalam bentuk HTML sesuai dengan template yang kita inginkan. Apabila context tersebut valid dan sudah di save maka HTML dapat melakukan looping untuk mengakses data yang kita miliki tersebut. 

#### 4. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas. <br>

Awal-awal saya membuka virtual environment saya terlebih dahulu berdasarkan `env\Scripts\activate`. Setelah terbuka saya lalu melakukan `python manage.py startapp todolist` untuk membuat aplikasi baru pada project django kita. Setelah itu saya ubah url seperti tugas-tugas sebelumnya. Lalu saya buat semuah model bernama **Task** untuk memberikan schema kepada database kita. Lalu saya menggunakan kode pada lab 3 untuk membuat fungsi login, register, dan logout. Saya memuat user, tabel, dan button yang diinginkan. Lalu saya membuat file baru bernama `forms.py` untuk memudahkan saya validate data yang dinginkan, setelah valid saya save data tersebut ke database kita. Namun user dan date tidak ada dalam input type sehingga saya harus memasukkan user instance secara manual dan menambahkan auto add pada field model di `models.py` saya. Saya menggunakan method **forms.Model** untuk memberikan metaclass agar model dapat digunakan dengan baik. Lalu saya perbaiki routing saya agar sesuai dengan tugas. Kemudian saya buka heroku dan membuat dummy data. Saya juga mengerjakan bonus dengan membuat fungsi baru yaitu **change_task_status** agar melakukan proses PUT (Update). Lalu saya membuat fungsi lagi bernama **delete_task** untuk mendelete data sedsuai dengan pk (primary key) yang saya dapat dari context pada HMTL. Lalu saya mengerjakan readme ini :D.  