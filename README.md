# Algoritma-dan-Pemrograman

Puji dan syukur kami panjatkan ke hadirat Tuhan Yang Maha Esa karena atas rahmat dan karunia-Nya, kami dapat menyusun karya ini yang berjudul "Algoritma dan Pemrograman Berbasis Object-Oriented Programming (OOP)". Buku atau panduan ini disusun sebagai referensi untuk membantu pembaca, khususnya mahasiswa dan praktisi pemula, memahami konsep dasar algoritma serta penerapan pemrograman berorientasi objek. Dalam era digital yang serba cepat ini, penguasaan OOP menjadi salah satu keterampilan yang sangat penting untuk membangun perangkat lunak yang modular, efisien, dan dapat dikembangkan secara berkelanjutan.

Dalam penyusunan karya ini, kami berupaya menghadirkan materi yang sistematis, mulai dari konsep algoritma dasar hingga implementasi prinsip OOP seperti enkapsulasi, pewarisan, dan polimorfisme menggunakan berbagai bahasa pemrograman populer. Setiap pembahasan dilengkapi dengan contoh kode, ilustrasi, dan latihan soal untuk mempermudah pembaca memahami dan mempraktikkan konsep yang dipelajari. Harapan kami, panduan ini tidak hanya menjadi media pembelajaran, tetapi juga mampu membangkitkan semangat inovasi dan eksplorasi dalam pengembangan perangkat lunak berbasis OOP.

Kami menyadari bahwa karya ini masih jauh dari sempurna. Oleh karena itu, kami mengundang pembaca untuk memberikan masukan dan kritik yang membangun untuk pengembangan karya ini di masa mendatang. Semoga karya ini dapat memberikan manfaat bagi para pembaca dalam memperdalam pemahaman mereka tentang algoritma dan pemrograman berorientasi objek.

**buku.php**
```php
<?php
class Buku
{
    protected $conn;

    public function __construct()
    {
        $this->connectDB();
    }

    private function connectDB()
    {
        $host = "localhost";
        $database = "dbperpus";
        $username = "root";
        $password = "";

        $this->conn = new mysqli($host, $username, $password, $database);
        if ($this->conn->error) {
            die("Koneksi dabatase MySQL gagal: " . $this->conn->error);
        }
    }

    public function tampilSemuaBuku()
    {
        $data = mysqli_query(
            $this->conn,
            "SELECT * FROM buku"
        );
        $hasil = [];
        while ($row = mysqli_fetch_assoc($data)) {
            $hasil[] = $row;
        }
        return $hasil;
    }
}

?>
```

**loker_buku.php**
```php
<?php

include_once 'buku.php';
class LokerBuku extends Buku
{
    public function tampilDataBuku($loker_buku)
    {
        $hasil = [];
        $data = mysqli_query(
            $this->conn,
            "SELECT * FROM buku
             WHERE loker_buku='" . $loker_buku . "'"
        );
        while ($row = mysqli_fetch_assoc($data)) {
            $hasil[] = $row;
        }
        return $hasil;
    }
}

?>
```

**dashboard.php**
```php

<!DOCTYPE html>
<html lang="en">
<head>
  <title>Bootstrap Example</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
</head>
<body>

<div class="container">
  <center><h2>Sistem Perpustakaan</h2></center>
  <ul class="nav nav-pills nav-justified">
    <li class="active"><a  href="index.php">Beranda</a></li>
    <li ><a  href="tampil_buku.php">Daftar Buku</a></li>
    <li><a  href="tampil_loker_buku.php">Daftar Loker</a></li>
  </ul>

  <div class="tab-content">
    <div id="home" class="tab-pane fade in active">
    
    </div>
    <div id="menu1" class="tab-pane fade">
      <h3>Tampil Buku</h3>
    </div>
    <div id="menu2" class="tab-pane fade">
      <h3>Tampil Loker</h3>
    </div>
    
  </div>

  <h2>Selamat Datang!</h2>
  <p>Semua judul buku lengkap ada disini, silahkan mencacri judul yang anda inginkan!</p>
</body>
</html>
```

**tampil_buku.php**
```php
<?php
include_once 'buku.php';
?>

<!DOCTYPE html>
<html lang="en">
<head>
  <title>Bootstrap Example</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
</head>
<body>

<div class="container">
  <h2>Sistem Perpustakaan</h2>
  <ul class="nav nav-pills nav-justified">
    <li ><a  href="dashboard.php">Beranda</a></li>
    <li class="active"><a  href="tampil_buku.php">Tampil Buku</a></li>
    <li><a  href="tampil_loker_buku.php">Tampil Loker</a></li>
  </ul>

  <div class="tab-content">
    <div id="home" class="tab-pane fade in active">
    
    </div>
    <div id="menu1" class="tab-pane fade">
      <h3>Tampil Buku</h3>
    </div>
    <div id="menu2" class="tab-pane fade">
      <h3>Tampil Loker</h3>
    </div>
    
  </div>

  <?php
    $buku = new Buku();
    ?>
      <h2>Data Buku</h2>
      <div class='container text-center mb-4'>
              <div class='horizontal-line'>
                  <!-- <span class='text-opacity bg-light text-dark p-2'>Menampilkan Seluruh Data Buku</span> -->
              </div>
            </div>
      <?php
      $data_buku = $buku->tampilSemuaBuku();
      if ($data_buku) {
      ?>
          <table class='table table-striped'>
                  <thead>
                      <tr>
                          <th>Loker Buku</th>
                          <th>Judul Buku</th>
                          <th>Nama Pengarang</th>
                          <th>Tahun Terbit</th>
                          <th>Penerbit</th>
                      </tr>
                  </thead>
                  <tbody>
                    <?php
                    foreach ($data_buku as $row) {
                    ?>
                    <tr>
                      <td><?=$row['loker_buku']?></td>
                      <td><?=$row['judul_buku']?></td>
                      <td><?=$row['nama_pengarang']?></td>
                      <td><?=$row['tahun_terbit']?></td>
                      <td><?=$row['penerbit']?></td>
                    </tr>
                    <?php
          }
          ?>
          </tbody>
          </table>
          <?php
      } else {
        ?>
          <p>Data buku tidak ditemukan.</p>
      <?php
        }
        ?>
</div>
</body>
</html>

</body>
</html>
```

**tampil_loker_buku**
```php
<?php
include_once 'loker_buku.php';
?>
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Bootstrap Example</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
</head>
<body>

<div class="container">
  <h2>Sistem Perpustakaan</h2>
  <ul class="nav nav-pills nav-justified">
    <li ><a  href="dashboard.php">Beranda</a></li>
    <li><a  href="tampil_buku.php">Tampil Buku</a></li>
    <li class="active"><a  href="tampil_loker_buku.php">Tampil Loker</a></li>
  </ul>

  <div class="tab-content">
    <div id="home" class="tab-pane fade in active">
    
    </div>
    <div id="menu1" class="tab-pane fade">
      <h3>Tampil Buku</h3>
    </div>
    <div id="menu2" class="tab-pane fade">
      <h3>Tampil Loker</h3>
    </div>
    
  </div>


<table id='table-buku-resep' class='table table-striped'hover {background-color: blue;}>
                <thead>
                    <tr >
                        <th>Loker Buku</th>
                        <th>Judul Buku</th>
                        <th>Nama Pengarang</th>
                        <th>Tahun Terbit</th>
                        <th>Penerbit</th>
                    </tr>
                </thead>
                <tbody>

                 
                <?php
    $loker_buku = new LokerBuku();
    ?>
      <h2>Data Buku</h2>
      <div class='container text-center mb-4'>
              <div class='horizontal-line'>
                  <!-- <span class='text-opacity bg-light text-dark p-2'>Menampilkan Seluruh Data Buku</span> -->
              </div>
            </div>
      <?php
      $data_buku_resep = $loker_buku->tampilDataBuku("Buku Resep Masakan");
      if ($data_buku_resep) {
      ?>
          <table class='table table-striped'>
                  <thead>
                      <tr>
                          <th>Loker Buku</th>
                          <th>Judul Buku</th>
                          <th>Nama Pengarang</th>
                          <th>Tahun Terbit</th>
                          <th>Penerbit</th>
                      </tr>
                  </thead>
                  <tbody>
                    <?php
                    foreach ($data_buku_resep as $row) {
                    ?>
                    <tr>
                      <td><?=$row['loker_buku']?></td>
                      <td><?=$row['judul_buku']?></td>
                      <td><?=$row['nama_pengarang']?></td>
                      <td><?=$row['tahun_terbit']?></td>
                      <td><?=$row['penerbit']?></td>
                    </tr>
                    <?php
          }
          ?>
          </tbody>
          </table>
          <?php
      } else {
        ?>
          <p>Data buku tidak ditemukan.</p>
      <?php
        }
        ?>
</body>
</html>
```

**tampil_buku.php**
```php
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Bootstrap Example</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.6.2/dist/css/bootstrap.min.css">
  <script src="https://cdn.jsdelivr.net/npm/jquery@3.7.1/dist/jquery.slim.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.1/dist/umd/popper.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@4.6.2/dist/js/bootstrap.bundle.min.js"></script>
</head>
<body>

<?php
include_once 'buku.php';

function tampilSemuaBuku() {
    $buku = new Buku();
    $data_buku = $buku->tampilSemuaBuku();
    // echo "<h2 class='text-center'>Data Buku</h2>";
    // echo "<div class='container text-center mb-4'>
    //         <div class='horizontal-line'>
    //             <span class='text-opacity bg-light text-dark p-2'>Menampilkan Seluruh Data Buku</span>
    //         </div>
    //       </div>";
    if ($data_buku) {
        foreach ($data_buku as $row):
            echo "<tr>
            <td>" . htmlspecialchars($row['loker_buku']) . "</td>
           <td>" . htmlspecialchars($row['judul_buku']) . "</td>
           <td>" . htmlspecialchars($row['nama_pengarang']) . "</td>
            <td>" . htmlspecialchars($row['tahun_terbit']) . "</td>
           <td>" . htmlspecialchars($row['penerbit']) . "</td>
            </tr>";
        endforeach;
        echo "</tbody></table>";
    } else {
        echo "<p>Data buku tidak ditemukan.</p>";
    }
}
?> 
<div class="container">
  <h2>Sistem Perpustakaan</h2>
 
  <!-- Nav tabs -->
  <ul class="nav nav-tabs" role="tablist">
    <li class="nav-item">
      <a class="nav-link " href="halaman.php">Home</a>
    </li>
    <li class="nav-item">
      <a class="nav-link active"  href="tampil_buku.php">Data Buku</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="tampil_loker_buku.php">Loker Buku</a>
    </li>
  </ul>

<table id='table-data-buku' class='table-border'>
                <thead>
                    <tr>
                        <th>Loker Buku</th>
                        <th>Judul Buku</th>
                        <th>Nama Pengarang</th>
                        <th>Tahun Terbit</th>
                        <th>Penerbit</th>
                    </tr>
                </thead>
                <tbody>
</div>
   
</body>
</html>
```

**tampil_loker_buku.php**
```php
<!DOCTYPE html>
<html lang="en">
<h<head>
  <title>Bootstrap Example</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.6.2/dist/css/bootstrap.min.css">
  <script src="https://cdn.jsdelivr.net/npm/jquery@3.7.1/dist/jquery.slim.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.1/dist/umd/popper.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@4.6.2/dist/js/bootstrap.bundle.min.js"></script>
</head>
<body>
<div class="container">
  <h2>Sistem Perpustakaan</h2>
 
  <!-- Nav tabs -->
  <ul class="nav nav-tabs" role="tablist">
    <li class="nav-item">
      <a class="nav-link " href="halaman.php">Home</a>
    </li>
    <li class="nav-item">
      <a class="nav-link "  href="tampil_buku.php">Data Buku</a>
    </li>
    <li class="nav-item">
      <a class="nav-link active" href="tampil_loker_buku.php">Loker Buku</a>
    </li>
  </ul>

<table id='table-data-buku' class='table table-striped'>
                <thead>
                    <tr>
                        <th>Loker Buku</th>
                        <th>Judul Buku</th>
                        <th>Nama Pengarang</th>
                        <th>Tahun Terbit</th>
                        <th>Penerbit</th>
                    </tr>
                </thead>
                <tbody>
</div>

<?php
include_once 'loker_buku.php';

function tampilLokerBuku($loker) {
    $loker_buku = new LokerBuku();
    $data_buku_resep = $loker_buku->tampilDataBuku($loker);
    echo "<h2 class='text-center'>.:: Buku Resep Masakan ::.</h2>";
    echo "<div class='container text-center mb-4'>
            <div class='horizontal-line'>
                <span class='text-opacity bg-light text-dark p-2'>
                    Menampilkan Data Buku dengan \"Loker Buku = $loker\"
                </span>
            </div>
          </div>";
    if ($data_buku_resep) {
        echo "<table id='table-buku-resep' class='table table-striped'>
                <thead>
                    <tr>
                        <th>Loker Buku</th>
                        <th>Judul Buku</th>
                        <th>Nama Pengarang</th>
                        <th>Tahun Terbit</th>
                        <th>Penerbit</th>
                    </tr>
                </thead>
                <tbody>";
        foreach ($data_buku_resep as $row) {
            echo "<tr>
                    <td>{$row['loker_buku']}</td>
                    <td>{$row['judul_buku']}</td>
                    <td>{$row['nama_pengarang']}</td>
                    <td>{$row['tahun_terbit']}</td>
                    <td>{$row['penerbit']}</td>
                  </tr>";
        }
        echo "</tbody></table>";
    } else {
        echo "<p>Data Buku Resep Makanan tidak ditemukan.</p>";
    }
}
?>
</html>
```
