# website menghitung BMI

<html lang="id">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Kalkulator BMI</title>
    <style>
      body {
        font-family: Arial, sans-serif;
        background: linear-gradient(to right, #74ebd5, #acb6e5);
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
      }
      .container {
        background: #fff;
        padding: 2rem;
        border-radius: 15px;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
        max-width: 400px;
        width: 100%;
      }
      h2 {
        text-align: center;
        margin-bottom: 1rem;
      }
      label {
        display: block;
        margin-top: 1rem;
      }
      input {
        width: 100%;
        padding: 0.5rem;
        margin-top: 0.5rem;
        border-radius: 8px;
        border: 1px solid #ccc;
      }
      button {
        margin-top: 1.5rem;
        width: 100%;
        padding: 0.7rem;
        background-color: #4caf50;
        color: white;
        border: none;
        border-radius: 8px;
        font-size: 1rem;
        cursor: pointer;
      }
      button:hover {
        background-color: #45a049;
      }
      .result {
        margin-top: 1.5rem;
        padding: 1rem;
        background-color: #f9f9f9;
        border-radius: 8px;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <h2>Kalkulator BMI</h2>
      <label for="nama">Nama Anda:</label>
      <input
        type="text"
        id="nama"
        name="nama"
        placeholder="Masukkan nama anda"
      />
      <label for="beratBadan">Berat Badan (kg):</label>
      <input
        type="number"
        id="beratBadan"
        name="beratBadan"
        step="0.1"
        placeholder="Masukkan berat badan"
      />
      <label for="tinggiBadan">Tinggi Badan (m):</label>
      <input
        type="number"
        id="tinggiBadan"
        name="tinggiBadan"
        step="0.01"
        placeholder="Masukkan tinggi badan"
      />
      <button type="button" onclick="hitungBMI()">Hitung BMI</button>
      <div id="output" class="result"></div>
    </div>
    <script>
      function hitungBMI() {
        const nama = document.getElementById("nama").value;
        const beratBadan = parseFloat(
          document.getElementById("beratBadan").value
        );
        const tinggiBadan = parseFloat(
          document.getElementById("tinggiBadan").value
        );
        const output = document.getElementById("output");

        if (
          !nama ||
          isNaN(beratBadan) ||
          isNaN(tinggiBadan) ||
          tinggiBadan === 0
        ) {
          output.innerHTML =
            '<span style="color:red;">Silakan isi semua data dengan benar !</span>';
          return;
        }

        const bmi = beratBadan / (tinggiBadan * tinggiBadan);
        let pesan = `Hai ${nama}, BMI anda ialah: ${bmi.toFixed(2)}<br>`;

        switch (true) {
          case bmi < 18.5:
            pesan +=
              "Berat badan anda kurang.<br>Saya sarankan anda menaikkan berat badan.";
            break;
          case bmi >= 18.5 && bmi <= 24.9:
            pesan +=
              "Berat badan anda ideal.<br>Pertahankan berat badan dan jaga pola hidup anda.";
            break;
          case bmi >= 25 && bmi <= 29.9:
            pesan +=
              "Berat badan anda berlebih.<br>Saya sarankan anda menurunkan berat badan.";
            break;
          case bmi >= 30:
            pesan += "Berat badan anda sudah obesitas.<br>Saya sarankan anda";
            break;
        }

        output.innerHTML = pesan;
      }
    </script>
  </body>
</html>
