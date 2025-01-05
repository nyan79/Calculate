# Calculate
Calculate a calories meter
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kalkulator Kebutuhan Kalori dan Protein</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>Kalkulator Kebutuhan Kalori dan Protein</h1>
        <form id="calorieForm">
            <label for="gender">Jenis Kelamin:</label>
            <select id="gender" required>
                <option value="male">Pria</option>
                <option value="female">Wanita</option>
            </select>

            <label for="age">Usia (tahun):</label>
            <input type="number" id="age" required>

            <label for="height">Tinggi Badan (cm):</label>
            <input type="number" id="height" required>

            <label for="weight">Berat Badan (kg):</label>
            <input type="number" id="weight" required>

            <label for="activityLevel">Tingkat Aktivitas:</label>
            <select id="activityLevel" required>
                <option value="sedentary">Sedentary (jarang olahraga)</option>
                <option value="light">Ringan (olahraga 1-3 hari/minggu)</option>
                <option value="moderate">Moderate (olahraga 3-5 hari/minggu)</option>
                <option value="active">Aktif (olahraga 6-7 hari/minggu)</option>
                <option value="veryActive">Sangat Aktif (kerja fisik tinggi)</option>
            </select>

            <button type="submit">Hitung</button>
        </form>

        <div id="result" class="hidden">
            <h2>Hasil Perhitungan:</h2>
            <p><strong>Kebutuhan Kalori Harian:</strong> <span id="calories"></span> kkal</p>
            <p><strong>Kebutuhan Protein Harian:</strong> <span id="protein"></span> gram</p>
        </div>pl
    </div>

    <script src="script.js"></script>
</body>
</html>
