# test-blood-cell 
<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AI วิเคราะห์ผลเลือด</title>
  <style>
    body {
      font-family: sans-serif;
      max-width: 600px;
      margin: auto;
      padding: 20px;
      background: #f9f9f9;
    }
    input {
      width: 100%;
      padding: 8px;
      margin-bottom: 10px;
    }
    button {
      padding: 10px 15px;
      background-color: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
    }
    .result {
      margin-top: 20px;
      background: #fff;
      padding: 15px;
      border-radius: 8px;
      border: 1px solid #ccc;
    }
  </style>
</head>
<body>

  <h2>AI วิเคราะห์ผลเลือดจากปลายนิ้ว</h2>

  <label>ระดับน้ำตาลในเลือด (Glucose)</label>
  <input type="number" id="glucose" placeholder="เช่น 110">

  <label>ฮีโมโกลบิน (Hemoglobin)</label>
  <input type="number" id="hemoglobin" placeholder="เช่น 13.5">

  <label>SpO2 (เปอร์เซ็นต์ออกซิเจนในเลือด)</label>
  <input type="number" id="spo2" placeholder="เช่น 98">

  <label>ความดัน Systolic</label>
  <input type="number" id="systolic" placeholder="เช่น 120">

  <label>ความดัน Diastolic</label>
  <input type="number" id="diastolic" placeholder="เช่น 80">

  <label>คอเลสเตอรอล (Cholesterol)</label>
  <input type="number" id="cholesterol" placeholder="เช่น 180">

  <button onclick="analyze()">วิเคราะห์</button>

  <div class="result" id="result"></div>

  <script>
    function analyze() {
      const glucose = parseFloat(document.getElementById('glucose').value);
      const hemoglobin = parseFloat(document.getElementById('hemoglobin').value);
      const spo2 = parseFloat(document.getElementById('spo2').value);
      const systolic = parseFloat(document.getElementById('systolic').value);
      const diastolic = parseFloat(document.getElementById('diastolic').value);
      const cholesterol = parseFloat(document.getElementById('cholesterol').value);

      let risks = [];

      if (glucose > 126) risks.push("⚠️ น้ำตาลในเลือดสูง (เสี่ยงเบาหวาน)");
      if (hemoglobin < 12) risks.push("⚠️ ฮีโมโกลบินต่ำ (เสี่ยงโลหิตจาง)");
      if (spo2 < 95) risks.push("⚠️ ค่า SpO2 ต่ำ (เสี่ยงภาวะพร่องออกซิเจน)");
      if (systolic > 140 || diastolic > 90) risks.push("⚠️ ความดันสูง");
      if (cholesterol > 200) risks.push("⚠️ คอเลสเตอรอลสูง");

      const resultDiv = document.getElementById('result');
      if (risks.length === 0) {
        resultDiv.innerHTML = "<strong>✅ ไม่พบความเสี่ยงที่ชัดเจน</strong>";
      } else {
        resultDiv.innerHTML = `<strong>ผลการวิเคราะห์:</strong><ul>${risks.map(r => `<li>${r}</li>`).join('')}</ul>`;
      }
    }
  </script>

</body>
</html>
