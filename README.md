<!DOCTYPE html><html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Booking Photo Booth</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f4;
      padding: 20px;
    }
    .container {
      max-width: 500px;
      margin: auto;
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h2 {
      text-align: center;
    }
    input, button {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
    }
    button {
      background: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    button:hover {
      background: #0056b3;
    }
    .result {
      margin-top: 20px;
      background: #e9ffe9;
      padding: 15px;
      border-radius: 5px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Booking Photo Booth</h2>
    <label>Nama</label>
    <input type="text" id="nama" placeholder="Masukkan nama" required /><label>No HP</label>
<input type="number" id="hp" placeholder="08xxxxxxxx" required />

<button onclick="booking()">Ambil Nomor Antrian</button>

<div class="result" id="hasil" style="display:none"></div>

  </div>  <script>
    let antrian = localStorage.getItem('antrian')
      ? parseInt(localStorage.getItem('antrian'))
      : 0;

    function booking() {
      const nama = document.getElementById('nama').value;
      const hp = document.getElementById('hp').value;

      if (nama === '' || hp === '') {
        alert('Lengkapi data terlebih dahulu');
        return;
      }

      antrian++;
      localStorage.setItem('antrian', antrian);

      document.getElementById('hasil').style.display = 'block';
      document.getElementById('hasil').innerHTML = `
        <b>Booking Berhasil!</b><br>
        Nama: ${nama}<br>
        No HP: ${hp}<br>
        <b>Nomor Antrian Anda: ${antrian}</b>
      `;

      document.getElementById('nama').value = '';
      document.getElementById('hp').value = '';
    }
  </script></body>
</html>
