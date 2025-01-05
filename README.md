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
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
}

.container {
    width: 80%;
    max-width: 600px;
    margin: 50px auto;
    padding: 20px;
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
}

form {
    display: flex;
    flex-direction: column;
}

label {
    margin-top: 10px;
}

input, select {
    padding: 8px;
    margin-top: 5px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    padding: 10px;
    margin-top: 20px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #45a049;
}

#result {
    margin-top: 30px;
    padding: 20px;
    background-color: #e7f7e7;
    border-radius: 8px;
    display: none;
}

.hidden {
    display: none;
}
document.getElementById('calorieForm').addEventListener('submit', function(event) {
    event.preventDefault();

    // Mendapatkan nilai input dari form
    const gender = document.getElementById('gender').value;
    const age = parseInt(document.getElementById('age').value);
    const height = parseInt(document.getElementById('height').value);
    const weight = parseInt(document.getElementById('weight').value);
    const activityLevel = document.getElementById('activityLevel').value;

    // Menghitung Basal Metabolic Rate (BMR) menggunakan rumus Mifflin-St Jeor
    let bmr;
    if (gender === 'male') {
        bmr = 10 * weight + 6.25 * height - 5 * age + 5; // Pria
    } else {
        bmr = 10 * weight + 6.25 * height - 5 * age - 161; // Wanita
    }

    // Faktor aktivitas
    let activityFactor;
    switch (activityLevel) {
        case 'sedentary': activityFactor = 1.2; break;
        case 'light': activityFactor = 1.375; break;
        case 'moderate': activityFactor = 1.55; break;
        case 'active': activityFactor = 1.725; break;
        case 'veryActive': activityFactor = 1.9; break;
    }

    // Menghitung total kebutuhan kalori
    const totalCalories = bmr * activityFactor;

    // Kebutuhan protein (secara umum 1 gram protein per kg berat badan)
    const totalProtein = weight;

    // Menampilkan hasil
    document.getElementById('calories').textContent = totalCalories.toFixed(2);
    document.getElementById('protein').textContent = totalProtein;

    // Menampilkan div hasil
    document.getElementById('result').style.display = 'block';
});
