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

# Menambahkan Data

```
INSERT INTO data_barang (kategori, nama, gambar, harga_beli, harga_jual, stok)
VALUES ('Elektronik', 'HP Samsung Android', 'hp_samsung.jpg', 2000000, 2400000, 5),
('Elektronik', 'HP Xiaomi Android', 'hp_xiaomi.jpg', 1000000, 1400000, 5),
('Elektronik', 'HP OPPO Android', 'hp_oppo.jpg', 1800000, 2300000, 5);
```

![5](https://user-images.githubusercontent.com/56244029/120239316-370ef500-c288-11eb-83b6-d9b019114327.png)

# Membuat Program CRUD
Buat folder lab8_php_database pada root directory web server (d:\xampp\htdocs)

![9](https://user-images.githubusercontent.com/56244029/120239453-83f2cb80-c288-11eb-9c30-99d34005f874.png)

Kemudian untuk mengakses direktory tersebut pada web server dengan mengakses URL:
http://localhost/lab8_php_database/

![10](https://user-images.githubusercontent.com/56244029/120239500-9ff66d00-c288-11eb-9caa-fc8116790242.png)

# Membuat file koneksi database
Buat file baru dengan nama koneksi.php
```
<?php
$host = "localhost";
$user = "root";
$pass = "";
$db = "latihan1";
$conn = mysqli_connect($host, $user, $pass, $db);
if ($conn == false)
{
echo "Koneksi ke server gagal.";
die();
} #else echo "Koneksi berhasil";
?>
```
Buka melalui browser untuk menguji koneksi database (untuk menyampilkan pesan
koneksi berhasil, uncomment pada perintah echo “koneksi berhasil”;

![11](https://user-images.githubusercontent.com/56244029/120239990-b81abc00-c289-11eb-8628-d9055d168643.png)

# Membuat file index untuk menampilkan data (Read)
Buat file baru dengan nama index.php
```
<?php
include("koneksi.php");

// query untuk menampilkan data
$sql = 'SELECT * FROM data_barang';
$result = mysqli_query($conn, $sql);

?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link href="style.css" rel="stylesheet" type="text/css" />
    <title>Data Barang</title>
</head>
<body>
    <div class="container">
        <h1>Data Barang</h1>
        <div class="main">
            <table>
            <tr>
                <th>Gambar</th>
                <th>Nama Barang</th>
                <th>Katagori</th>
                <th>Harga Jual</th>
                <th>Harga Beli</th>
                <th>Stok</th>
                <th>Aksi</th>
            </tr>
            <?php if($result): ?>
            <?php while($row = mysqli_fetch_array($result)): ?>
            <tr>
                <td><img src="gambar/<?= $row['gambar'];?>" alt="<?=
$row['nama'];?>"></td>
                <td><?= $row['nama'];?></td>
                <td><?= $row['kategori'];?></td>
                <td><?= $row['harga_beli'];?></td>
                <td><?= $row['harga_jual'];?></td>
                <td><?= $row['stok'];?></td>
                <td><?= $row['id_barang'];?></td>
            </tr>
            <?php endwhile; else: ?>
            <tr>
                <td colspan="7">Belum ada data</td>
            </tr>
            <?php endif; ?>
            </table>
        </div>
    </div>
</body>
</html>
```

