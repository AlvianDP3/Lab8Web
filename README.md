# Langkah-langkah Praktikum
# Persiapan
Untuk memulai membuat aplikasi CRUD sederhana, yang perlu disiapkan adalah
database server menggunakan MySQL. Pastikan MySQL Server sudah dapat dijalankan
melalui XAMPP.

# Menjalankan MySQL Server
Untuk menjalankan MySQL Server dari menu XAMPP Contol.

![1](https://user-images.githubusercontent.com/56244029/120057466-77465b80-c06d-11eb-98f6-3622cdea8442.jpg)

# Mengakses MySQL Client menggunakan PHP MyAdmin
Pastikan webserver Apache dan MySQL server sudah dijalankan. Kemudian buka
melalui browser: http://localhost/phpmyadmin/

# Membuat Database: Studi Kasus Data Barang

![2](https://user-images.githubusercontent.com/56244029/120057493-c2606e80-c06d-11eb-97e0-ac8ab5d9335b.png)

# Hasil

![3](https://user-images.githubusercontent.com/56244029/120057531-06537380-c06e-11eb-87ae-d89a522fe354.png)

# Membuat Database
```
CREATE DATABASE latihan1;
```

# Membuat Tabel
```
CREATE TABLE data_barang (
		    id_barang int(10) auto_increment Primary Key,
		    kategori varchar(30),
		    nama varchar(30),
		    gambar varchar(100),
		    harga_beli decimal(10,0),
		    harga_jual decimal(10,0),
		    stok int(4)
);
```

![4](https://user-images.githubusercontent.com/56244029/120057610-8548ac00-c06e-11eb-9448-05468ec8480a.png)


