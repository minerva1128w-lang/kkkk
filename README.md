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
    header img {
      width: 120px;
      margin-bottom: 15px;
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
    .result {
      margin-top: 20px;
      padding: 20px;
      border-radius: 15px;
      text-align: center;
      font-weight: bold;
    }
    .lulus {
      background: #ecfdf5;
      border: 1px solid #6ee7b7;
      color: #047857;
    }
    .tidak-lulus {
      background: #fef2f2;
      border: 1px solid #fca5a5;
      color: #b91c1c;
    }
  </style>
</head>
<body>
  <header>
    <img src="logo-smagur-brigata.png" alt="Logo OSIS">
    <h1>Pengumuman Hasil Seleksi OSIS 2025/2026</h1>
    <p>Silakan masukkan nama dan nomor absen Anda untuk melihat hasil seleksi.</p>
  </header>

  <div class="card">
    <label for="nama">Nama Lengkap</label>
    <input type="text" id="nama" placeholder="Contoh: RAKADHYTA RAFFAEL">

    <label for="absen">Nomor Absen</label>
    <input type="text" id="absen" placeholder="Contoh: 01">

    <button class="btn" onclick="cariHasil()">Lihat Hasil</button>
    <div id="hasil"></div>
  </div>

  <script>
    // Semua peserta dari Excel ditambahkan di sini
    const peserta = [
            { nama: "AZIZATUL MUNAWAROH", absen: "01", status: "tidak lulus" },
            { nama: "AMEERA NAURA SYIFA", absen: "02", status: "lulus" },
            { nama: "MUHAMMAD RAMADAN WIDYANTARA", absen: "03", status: "tidak lulus" },
            { nama: "DESINTA SYIVA MAHARANI", absen: "04", status: "tidak lulus" },
            { nama: "ALIF YUSUF SATRIYO", absen: "05", status: "lulus" },
            { nama: "KEISHA ASKASYA", absen: "06", status: "tidak lulus" },
            { nama: "NAJWA KHAIRA WILDA", absen: "07", status: "tidak lulus" },
            { nama: "RANGGA PANJI YUDA", absen: "08", status: "tidak lulus" },
            { nama: "JOHN YABES SITANGGANG", absen: "09", status: "tidak lulus" },
            { nama: "VIEN NADYA NAFASA PUTRI", absen: "10", status: "tidak lulus" },
            { nama: "SITI FADHILATUR ROHMA", absen: "11", status: "tidak lulus" },
            { nama: "MARISA ERLINDA NURDIN", absen: "12", status: "tidak lulus" },
            { nama: "MOCH DHIRGAM PUTRA ALAMSYAH", absen: "13", status: "lulus" },
            { nama: "RAHMA SHOBIHA RAMADHANI", absen: "14", status: "tidak lulus" },
            { nama: "AMANDA IKHWANUR FITRY", absen: "15", status: "tidak lulus" },
            { nama: "MUHAMAD LUKMANNUL HAKIM", absen: "16", status: "tidak lulus" },
            { nama: "ADHAM HILMI GRANDISSON", absen: "17", status: "lulus" },
            { nama: "FADHOL FAISAL ALI", absen: "18", status: "tidak lulus" },
            { nama: "HEDYON FARUQ ACHMADY", absen: "19", status: "lulus" },
            { nama: "RAYHANAH APSARI GHINALIA", absen: "20", status: "tidak lulus" },
            { nama: "MEIDA AYU PUSPITA", absen: "21", status: "tidak lulus" },
            { nama: "AANISAH ANARIESNAWATI", absen: "22", status: "tidak lulus" },
            { nama: "FITRIA WANODYA SITENGSU", absen: "23", status: "tidak lulus" },
            { nama: "KIRANA AYUNING NASTITI", absen: "24", status: "lulus" },
            { nama: "REFANO ARDIANSYAH", absen: "25", status: "lulus" },
            { nama: "AURA RAHMA JATMIKO", absen: "26", status: "tidak lulus" },
            { nama: "JUNITA DWI PRASETIA", absen: "27", status: "lulus" },
            { nama: "AQISHA MARTHA NURFAJRINA", absen: "28", status: "lulus" },
            { nama: "ELYANA ERSA NUR ROHMAH", absen: "29", status: "tidak lulus" },
            { nama: "MILA DWI AGUSTIN", absen: "30", status: "tidak lulus" },
            { nama: "BALQIS DURRATUL HIKMAH", absen: "31", status: "tidak lulus" },
            { nama: "ALVIONA LATASYA PRATAMA", absen: "32", status: "tidak lulus" },
            { nama: "RIZKIA PRADITA SARI", absen: "33", status: "tidak lulus" },
            { nama: "AHMAD ZAWAWI", absen: "34", status: "tidak lulus" },
            { nama: "DIRA ANDRA SARI", absen: "35", status: "tidak lulus" },
            { nama: "PUTRI ILLA MADANI", absen: "36", status: "tidak lulus" },
            { nama: "FRISKA AULIA PUTRI", absen: "37", status: "tidak lulus" },
            { nama: "YUNIA LINDA NUR ALFIANI", absen: "38", status: "lulus" },
            { nama: "PANDU DWI KURNIAWAN", absen: "39", status: "lulus" },
            { nama: "DEVIANA HUSNA", absen: "40", status: "lulus" },
            { nama: "DUWI NUR SYAMSIYAH", absen: "41", status: "lulus" },
            { nama: "LAYLA NUR AZIZAH", absen: "42", status: "lulus" },
            { nama: "FIKHA KHOIRUN NISA", absen: "43", status: "lulus" },
            { nama: "NATHANIA NAUROH PRABAWATI", absen: "44", status: "tidak lulus" },
            { nama: "AFRISTA WIJAYANTI", absen: "45", status: "tidak lulus" },
            { nama: "KAYYISA ELMA ELIEFIA", absen: "46", status: "tidak lulus" },
            { nama: "ANISA NUR KHOLIFAH", absen: "47", status: "lulus" },
            { nama: "ASTYNA AGATHA ARUMNINGTIYAS", absen: "48", status: "tidak lulus" },
            { nama: "ZAHRA ALIFATUN NABILA", absen: "49", status: "tidak lulus" },
            { nama: "DZAKIY MUSYADAD SURYO SAPUTRA", absen: "50", status: "lulus" },
            { nama: "ELVARETTA NISRINA UFAIROH", absen: "51", status: "lulus" },
            { nama: "YEPVI AGUSTINA RAHAYU", absen: "52", status: "tidak lulus" },
            { nama: "ARINI AULIA RAHMADANI", absen: "53", status: "tidak lulus" },
            { nama: "SASKIA PUTRI BILGHIS", absen: "54", status: "tidak lulus" },
            { nama: "MOCH ZAKI DHIYA NUGRAHA", absen: "55", status: "tidak lulus" },
            { nama: "VERLYTA RAMADHANI SUGIHARTO", absen: "56", status: "tidak lulus" },
            { nama: "DETRIS AYU DEA ARDINDA", absen: "57", status: "tidak lulus" },
            { nama: "RISMA RAHAJENG", absen: "58", status: "tidak lulus" },
            { nama: "ANGGREK AL RAHMA KIRANI", absen: "59", status: "lulus" },
            { nama: "ANNISA YULIAN ZAHROTUSSITA", absen: "60", status: "lulus" },
            { nama: "ALVINA OKTAVIA PUTRI", absen: "61", status: "lulus" },
            { nama: "BABY SEKAR ARUM SARAS WATI", absen: "62", status: "tidak lulus" },
            { nama: "FARANNISA KAMILA", absen: "63", status: "tidak lulus" },
            { nama: "WIDYA DWI PURNAMASARI", absen: "64", status: "lulus" },
            { nama: "MUHAMMAD FARRELINO RAMADHAN", absen: "65", status: "lulus" },
            { nama: "SANDY PUTRA PRATAMA", absen: "66", status: "lulus" },
            { nama: "ADITYA YUDHA FIRMANSYAH", absen: "67", status: "tidak lulus" },
            { nama: "ZONE DAHFIN IVADA", absen: "68", status: "lulus" },
            { nama: "AFWA ALFA SALSABILA", absen: "69", status: "lulus" },
            { nama: "PRETTY ARESTY NAIMATUS SINTIYAS", absen: "70", status: "lulus" },
            { nama: "VERREN MARETHA DWI VAMA", absen: "71", status: "tidak lulus" },
            { nama: "GALIH AKBAR GUSTIAR", absen: "72", status: "lulus" },
            { nama: "ELYANA ERSA NUR ROHMAH", absen: "73", status: "tidak lulus" },
            { nama: "TATA REDITA AYU MEYLISA", absen: "74", status: "lulus" },
            { nama: "KEYLA FIORENTINA ALDIRA YUANDRA", absen: "75", status: "lulus" },
            { nama: "AMIRA TATA STIANINGRUM", absen: "76", status: "lulus" },
            { nama: "KEVIN APRILEO", absen: "77", status: "lulus" },
            { nama: "KARTIKA MAWARNI NORYATMA", absen: "78", status: "tidak lulus" },
            { nama: "AULIA AYUNINGTYAS", absen: "79", status: "tidak lulus" },
            { nama: "MOHAMMAD ANSORRY", absen: "80", status: "tidak lulus" },
            { nama: "MOH. ANGEL KRISNA BHAKTI", absen: "81", status: "lulus" },
            { nama: "ACHMAD THAHA METWALLY", absen: "82", status: "lulus" }
        ];

    function cariHasil() {
      const nama = document.getElementById("nama").value.trim().toLowerCase();
      const absen = document.getElementById("absen").value.trim();
      const hasilDiv = document.getElementById("hasil");
      hasilDiv.innerHTML = "";

      const data = peserta.find(
        (p) => p.nama.toLowerCase() === nama && p.absen === absen
      );

      if (data) {
        if (data.status === "lulus") {
          hasilDiv.innerHTML = `<div class="result lulus">Selamat! Anda dinyatakan <b>LULUS</b> seleksi penerimaan 2025.</div>`;
        } else {
          hasilDiv.innerHTML = `<div class="result tidak-lulus">Terima kasih. Anda <b>belum berhasil</b> lolos seleksi tahun ini.</div>`;
        }
      } else {
        hasilDiv.innerHTML = `<div class="result tidak-lulus">Data tidak ditemukan. Periksa kembali nama dan nomor absen.</div>`;
      }
    }
  </script>
</body>
</html>
