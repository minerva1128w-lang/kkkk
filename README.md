<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pengumuman Hasil Seleksi OSIS 2025/2026</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: linear-gradient(to bottom, #eff6ff, #ffffff);
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
    }
    header {
      text-align: center;
      margin-bottom: 20px;
    }
    h1 {
      color: #1d4ed8;
      margin-bottom: 10px;
    }
    .card {
      background: white;
      border-radius: 15px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      padding: 20px;
      max-width: 400px;
      width: 100%;
    }
    .card label {
      display: block;
      margin-bottom: 5px;
      font-weight: bold;
      color: #374151;
    }
    .card input {
      width: 100%;
      padding: 10px;
      border-radius: 10px;
      border: 1px solid #d1d5db;
      margin-bottom: 15px;
    }
    .btn {
      background: #2563eb;
      color: white;
      padding: 10px;
      border: none;
      border-radius: 10px;
      width: 100%;
      cursor: pointer;
      font-size: 16px;
    }
    .btn:hover {
      background: #1d4ed8;
    }
  </style>
</head>
<body>
  <header>
    <h1>Pengumuman Hasil Seleksi OSIS 2025/2026</h1>
    <p>Silakan masukkan nama dan nomor absen Anda untuk melihat hasil seleksi.</p>
  </header>

  <div class="card">
    <label for="nama">Nama Lengkap</label>
    <input type="text" id="nama" placeholder="Contoh: RAKADHYTA RAFFAEL">

    <label for="absen">Nomor Absen</label>
    <input type="text" id="absen" placeholder="Contoh: 01">

    <button class="btn" onclick="cariHasil()">Lihat Hasil</button>
  </div>

  <script>
    const peserta = [
      { nama: "AZIZATUL MUNAWAROH", absen: "01", status: "tidak lulus" },
      { nama: "AMEERA NAURA SYIFA", absen: "02", status: "lulus" },
      { nama: "MUHAMMAD RAMADAN WIDYANTARA", absen: "03", status: "tidak lulus" },
      { nama: "DESINTA SYIVA MAHARANI", absen: "04", status: "tidak lulus" },
      { nama: "ALIF YUSUF SATRIYO", absen: "05", status: "lulus" },
      // ... semua peserta lainnya
    ];

    function cariHasil() {
      const nama = document.getElementById("nama").value.trim().toLowerCase();
      const absen = document.getElementById("absen").value.trim();
      const data = peserta.find(
        (p) => p.nama.toLowerCase() === nama && p.absen === absen
      );

      if (data) {
        if (data.status === "lulus") {
          window.location.href = "lulus.html";
        } else {
          window.location.href = "tidak_lulus.html";
        }
      } else {
        window.location.href = "tidak_ditemukan.html";
      }
    }
  </script>
</body>
</html>
