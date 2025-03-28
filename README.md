<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>بطاقة معايدة - UPS</title>
<style>
  @font-face {
    font-family: 'ArbFONTS-GE_SS_TWO_MEDIUM';
    src: url('fonts/ArbFONTS-GE_SS_TWO_MEDIUM.otf') format('opentype');
  }

  body {
    font-family: 'ArbFONTS-GE_SS_TWO_MEDIUM', Arial, sans-serif;
    background-color: #f0f0f0;
    color: #333;
    text-align: center;
  }
  h2 {
    color: #00b1e1;
  }
  #preview {
    margin: 0 auto;
    text-align: center;
  }
  #preview img {
    max-width: 80%; /* تم تغيير هذه القيمة لتصغير الصورة */
    height: auto;
  }
  #preview span {
    position: absolute;
    font-size: 36px;
    color: #00b1e1;
    background-color: rgba(255, 255, 255, 0.7);
    padding: 10px 20px;
    border-radius: 10px;
    top: 672px;
    left: 50%;
    transform: translateX(-50%);
  }
  .button-container {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 10px;
    margin-bottom: 20px;
  }
  button {
    background-color: #00b1e1;
    color: white;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
    border-radius: 5px;
    flex: 1;
    max-width: 200px;
  }
  button:hover {
    background-color: #0089b7;
  }
  input[type="text"] {
    padding: 10px;
    border-radius: 5px;
    border: 1px solid #ddd;
    flex: 1;
    max-width: 200px;
  }
</style>
</head>
<body>
  <h2>بطاقة معايدة - UPS</h2>
  <div class="button-container">
    <select id="imageSelect">
      <option value="template/EID1.png"> 1 بطاقة معايدة </option>
            <option value="template/EID2.png"> 2 بطاقة معايدة </option>

    </select>
    <input type="text" id="nameInput" placeholder="اكتب اسمك">
    <button onclick="previewImage()">تأكيد الاسم</button>
    <button onclick="downloadImage()">حمل بطاقتك</button>
  </div>
  <br><br>
  <div id="preview"></div>
  
  <script>
    function previewImage() {
      var selectedImage = document.getElementById("imageSelect").value;
      var name = document.getElementById("nameInput").value;
      var previewDiv = document.getElementById("preview");

      var img = new Image();
      img.onload = function() {
        var canvas = document.createElement("canvas");
        var ctx = canvas.getContext("2d");

        // تعيين عرض وارتفاع الـ Canvas
        canvas.width = img.naturalWidth;
        canvas.height = img.naturalHeight;

        // رسم الصورة على الـ Canvas
        ctx.drawImage(img, 0, 0);

        // تحديد موضع النص على الصورة (أفقيًا في المنتصف)
        var textX = canvas.width / 2; // الموضع الأفقي في المنتصف
        var textY = 1418; // المسافة من الأعلى بالبكسل

        // تحديد المحاذاة دائمًا إلى المنتصف
        ctx.textAlign = "center"; // النص في المنتصف

        // إضافة النص إلى الصورة
        ctx.font = "40px 'ArbFONTS-GE_SS_TWO_MEDIUM'";
        ctx.fillStyle = "#000000";
        ctx.fillText(name, textX, textY);

        // إضافة الصورة إلى المعاينة
        previewDiv.innerHTML = '';
        previewDiv.appendChild(canvas);
      };
      img.src = selectedImage;
    }

    function downloadImage() {
      var selectedImage = document.getElementById("imageSelect").value;
      var name = document.getElementById("nameInput").value;
      var previewDiv = document.getElementById("preview");

      var img = new Image();
      img.onload = function() {
        var canvas = document.createElement("canvas");
        var ctx = canvas.getContext("2d");

        // تعيين عرض وارتفاع الـ Canvas
        canvas.width = img.naturalWidth;
        canvas.height = img.naturalHeight;

        // رسم الصورة على الـ Canvas
        ctx.drawImage(img, 0, 0);

        // تحديد موضع النص على الصورة (أفقيًا في المنتصف)
        var textX = canvas.width / 2; // الموضع الأفقي في المنتصف
        var textY = 1418; // المسافة من الأعلى بالبكسل

        // تحديد المحاذاة دائمًا إلى المنتصف
        ctx.textAlign = "center"; // النص في المنتصف

        // إضافة النص إلى الصورة
        ctx.font = "40px 'ArbFONTS-GE_SS_TWO_MEDIUM'";
        ctx.fillStyle = "#000000";
        ctx.fillText(name, textX, textY);

        // تحويل الصورة والنص إلى بيانات URL
        var dataURL = canvas.toDataURL("image/png");

        // إنشاء رابط التنزيل
        var downloadLink = document.createElement("a");
        downloadLink.download = "edited_image.png";
        downloadLink.href = dataURL;
        downloadLink.click();
      };
      img.src = selectedImage;
    }
  </script>
  <footer>
    <p style="font-size: 1.0em;">Programmed by Ahmed Helmy</p>
  </footer>
</body>
</html>
