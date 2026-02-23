<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kamera Erişimi</title>
    <style>
        body { font-family: sans-serif; display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100vh; background: #f0f0f0; }
        video { border: 5px solid #333; border-radius: 10px; width: 80%; max-width: 600px; background: #000; }
        h1 { color: #333; }
    </style>
</head>
<body>

    <h1>Kamera Bağlantısı</h1>
    <video id="videoElement" autoplay playsinline></video>

    <script>
        async function kameraBaslat() {
            try {
                // Kamera erişim izni istiyoruz
                const stream = await navigator.mediaDevices.getUserMedia({ video: true });
                
                // İzin verilirse görüntüyü video etiketine aktarıyoruz
                const video = document.querySelector("#videoElement");
                video.srcObject = stream;
                
                console.log("Kamera erişimi sağlandı gardaşım.");
            } catch (err) {
                // Kullanıcı reddederse veya hata oluşursa burası çalışır
                console.error("Hata: " + err);
                alert("Kamera izni verilmedi veya cihaz bulunamadı.");
            }
        }

        // Sayfa yüklendiğinde fonksiyonu çalıştır
        window.onload = kameraBaslat;
    </script>

</body>
</html>
