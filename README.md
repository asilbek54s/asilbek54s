<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>QR Code yaratish</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #a1ffb0;
        }

        .container {
            background-color: #3fbb46;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
        }

        h1 {
            text-align: center;
            margin-bottom: 20px;
            color: white;
        }

        .input-group {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }

        .input-group label {
            width: 100px;
            color: white;
        }

        .input-group input {
            flex-grow: 1;
            padding: 8px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        .button-group {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }

        .btn-generate {
            flex-grow: 1;
            padding: 10px;
            text-align: center;
            background-color: #2196f3;
            color: #fff;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        .btn-generate:hover {
            box-shadow: 0 3px 4px white;
            background-color: #42aaff;
        }
        .btn-download {
            flex-grow: 1;
            padding: 10px;
            text-align: center;
            background-color: #2196f3;
            color: #fff;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            margin-left: 10px;
        }
        .btn-download:hover {
            box-shadow: 0 3px 4px white;
            background-color: #42aaff;
        }
        .qr-code {
            display: flex;
            justify-content: center;
            margin-top: 20px;
        }

        .qr-code img {
            max-width: 200px;
            max-height: 200px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>QR Code yaratish</h1>
        <div class="input-group">
            <input type="text" id="text-input" placeholder="Matn yoki URLni kiriting">
        </div>
        <div class="qr-code" id="qr-code"></div>
        <div class="button-group">
            <button class="btn-generate" onclick="generateQRCode()">QR Code yaratish</button>
            <button class="btn-download" onclick="downloadQRCode()">QR Codeni yuklab olish</button>
        </div>
        <div class="qr-code" id="qr-code"></div>
    </div>

    <script src="https://cdn.rawgit.com/davidshimjs/qrcodejs/gh-pages/qrcode.min.js"></script>
    <script>
        var qr;

        function generateQRCode() {
            var text = document.getElementById("text-input").value;
            var qrCodeDiv = document.getElementById("qr-code");
            qrCodeDiv.innerHTML = "";

            qr = new QRCode(qrCodeDiv, {
                text: text,
                width: 200,
                height: 200
            });
        }

        function downloadQRCode() {
            if (qr) {
                var qrDataURL = qr._el.firstChild.toDataURL("image/png");
                var link = document.createElement("a");
                link.href = qrDataURL;
                link.download = "qrcode.png";
                link.click();
            }
        }
    </script>
</body>
</html>
