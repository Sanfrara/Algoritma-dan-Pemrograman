# Algoritma-dan-Pemrograman

Puji dan syukur kami panjatkan ke hadirat Tuhan Yang Maha Esa karena atas rahmat dan karunia-Nya, kami dapat menyusun karya ini yang berjudul "Algoritma dan Pemrograman Berbasis Object-Oriented Programming (OOP)". Buku atau panduan ini disusun sebagai referensi untuk membantu pembaca, khususnya mahasiswa dan praktisi pemula, memahami konsep dasar algoritma serta penerapan pemrograman berorientasi objek. Dalam era digital yang serba cepat ini, penguasaan OOP menjadi salah satu keterampilan yang sangat penting untuk membangun perangkat lunak yang modular, efisien, dan dapat dikembangkan secara berkelanjutan.

Dalam penyusunan karya ini, kami berupaya menghadirkan materi yang sistematis, mulai dari konsep algoritma dasar hingga implementasi prinsip OOP seperti enkapsulasi, pewarisan, dan polimorfisme menggunakan berbagai bahasa pemrograman populer. Setiap pembahasan dilengkapi dengan contoh kode, ilustrasi, dan latihan soal untuk mempermudah pembaca memahami dan mempraktikkan konsep yang dipelajari. Harapan kami, panduan ini tidak hanya menjadi media pembelajaran, tetapi juga mampu membangkitkan semangat inovasi dan eksplorasi dalam pengembangan perangkat lunak berbasis OOP.

Kami menyadari bahwa karya ini masih jauh dari sempurna. Oleh karena itu, kami mengundang pembaca untuk memberikan masukan dan kritik yang membangun untuk pengembangan karya ini di masa mendatang. Semoga karya ini dapat memberikan manfaat bagi para pembaca dalam memperdalam pemahaman mereka tentang algoritma dan pemrograman berorientasi objek.

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
