- 👋 Hi, I’m mohammed almoutaz
- im intersting to i help you to make your cv
-<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>مولّد السيرة الذاتية</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #f4f4f9;
    }

    .container {
      max-width: 800px;
      margin: 50px auto;
      background: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }

    h1 {
      text-align: center;
      color: #333;
    }

    form {
      display: flex;
      flex-direction: column;
      gap: 15px;
    }

    input, select, textarea, button {
      padding: 10px;
      font-size: 16px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }

    button {
      background-color: #007bff;
      color: white;
      border: none;
      cursor: pointer;
    }

    button:hover {
      background-color: #0056b3;
    }

    .preview {
      margin-top: 30px;
      padding: 20px;
      background: #f9f9f9;
      border: 1px dashed #ccc;
      text-align: center;
    }

    .template1 {
      text-align: left;
      border: 2px solid #007bff;
      padding: 15px;
      background-color: #eef4ff;
    }

    .template2 {
      text-align: center;
      border: 2px solid #28a745;
      padding: 15px;
      background-color: #eaffea;
    }

    h2, h3 {
      margin: 5px 0;
    }

    #downloadButton {
      margin-top: 20px;
      display: none;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>مولّد السيرة الذاتية</h1>
    <form id="cvForm">
      <input type="text" id="name" placeholder="الاسم الكامل" required>
      <input type="text" id="jobTitle" placeholder="المسمى الوظيفي" required>
      <textarea id="experience" rows="4" placeholder="الخبرات العملية" required></textarea>
      <textarea id="skills" rows="4" placeholder="المهارات" required></textarea>
      <select id="template">
        <option value="template1">القالب 1 (تصميم بسيط)</option>
        <option value="template2">القالب 2 (تصميم مركّز)</option>
      </select>
      <button type="button" onclick="generatePreview()">معاينة السيرة الذاتية</button>
    </form>
    <div class="preview" id="cvPreview">
      <p>هنا ستظهر معاينة السيرة الذاتية.</p>
    </div>
    <button id="downloadButton" onclick="downloadCV()">تحميل السيرة الذاتية كصورة</button>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/html2canvas@1.4.1/dist/html2canvas.min.js"></script>
  <script>
    function generatePreview() {
      const name = document.getElementById("name").value;
      const jobTitle = document.getElementById("jobTitle").value;
      const experience = document.getElementById("experience").value;
      const skills = document.getElementById("skills").value;
      const template = document.getElementById("template").value;

      const preview = `
        <div class="${template}">
          <h2>${name}</h2>
          <h3>${jobTitle}</h3>
          <p><strong>الخبرات:</strong> ${experience}</p>
          <p><strong>المهارات:</strong> ${skills}</p>
        </div>
      `;

      document.getElementById("cvPreview").innerHTML = preview;
      document.getElementById("downloadButton").style.display = "block";
    }

    function downloadCV() {
      const cvPreview = document.getElementById("cvPreview");

      html2canvas(cvPreview).then(canvas => {
        const link = document.createElement("a");
        link.download = "CV.png";
        link.href = canvas.toDataURL();
        link.click();
      });
    }
  </script>
</body>
</html>
