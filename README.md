<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Essay Upload</title>
    <style>
        body {
            font-family: "Times New Roman", serif;
            margin: 40px auto;
            max-width: 800px;
            line-height: 1.8;
            padding: 20px;
            text-align: center;
        }
        .content-area {
            width: 100%;
            min-height: 300px;
            border: 1px solid #ccc;
            padding: 20px;
            text-align: left;
        }
        .image-container {
            margin-top: 20px;
        }
        .image-container img {
            max-width: 100%;
            height: auto;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <div class="content-area" contenteditable="true">
        <p>Start writing or insert an image here...</p>
    </div>
    <br>
    <input type="file" id="imageUpload" accept="image/*" multiple>
    <div class="image-container" id="imagePreview"></div>
    
    <script>
        document.getElementById('imageUpload').addEventListener('change', function(event) {
            const preview = document.getElementById('imagePreview');
            preview.innerHTML = '';
            Array.from(event.target.files).forEach(file => {
                const reader = new FileReader();
                reader.onload = function(e) {
                    const img = document.createElement('img');
                    img.src = e.target.result;
                    document.querySelector('.content-area').appendChild(img);
                }
                reader.readAsDataURL(file);
            });
        });
    </script>
</body>
</html>
