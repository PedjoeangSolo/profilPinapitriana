<?php
$error = '';
$download_url = '';
$media_type = ''; // 'image' atau 'video'

if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $pinterest_url = filter_input(INPUT_POST, 'url', FILTER_VALIDATE_URL);

    if (!$pinterest_url) {
        $error = 'URL tidak valid. Silakan masukkan URL Pinterest yang benar.';
    } else {
        // Mengambil konten HTML dari URL Pinterest
        $options = [
            'http' => [
                'method' => "GET",
                'header' => "User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36\r\n"
            ]
        ];
        $context = stream_context_create($options);
        $html = @file_get_contents($pinterest_url, false, $context);

        if ($html === FALSE) {
            $error = 'Gagal mengambil data dari Pinterest. Pastikan link benar dan coba lagi.';
        } else {
            // 1. Coba cari tag Video (Pinterest menyimpan link video MP4 di tag video/script)
            if (preg_match('/"video_list".*?"url":"(https:\/\/v1\.pinimg\.com\/videos\/.*?\.mp4)"/', $html, $matches)) {
                // Bersihkan karakter escape jika ada
                $download_url = stripslashes($matches[1]);
                $media_type = 'video';
            }
            // 2. Jika bukan video, cari gambar dengan resolusi tertinggi (biasanya originals)
            elseif (preg_match('/"https:\/\/i\.pinimg\.com\/originals\/.*?\.jpg"/', $html, $matches) || 
                    preg_match('/"https:\/\/i\.pinimg\.com\/736x\/.*?\.jpg"/', $html, $matches)) {
                $download_url = trim($matches[0], '"');
                $media_type = 'image';
            } else {
                $error = 'Tidak dapat menemukan media di link tersebut. Pinterest mungkin sedang memperbarui sistem mereka.';
            }
        }
    }
}
?>

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pinterest Downloader</title>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #f7f7f7; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; }
        .container { background: white; padding: 30px; border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.1); width: 100%; max-width: 500px; text-align: center; }
        h2 { color: #bd081c; margin-bottom: 20px; }
        input[type="url"] { width: 100%; padding: 12px; margin: 10px 0; border: 1px solid #ccc; border-radius: 6px; box-sizing: border-box; }
        button { background-color: #bd081c; color: white; border: none; padding: 12px 20px; border-radius: 6px; cursor: pointer; width: 100%; font-size: 16px; font-weight: bold; }
        button:hover { background-color: #ad071a; }
        .error { color: red; margin-top: 15px; font-size: 14px; }
        .result { margin-top: 25px; padding: 15px; background: #f0f0f0; border-radius: 8px; }
        .btn-download { display: inline-block; background-color: #25d366; color: white; padding: 10px 20px; text-decoration: none; border-radius: 6px; font-weight: bold; margin-top: 10px; }
        .preview { max-width: 100%; max-height: 250px; border-radius: 6px; margin-top: 10px; }
    </style>
</head>
<body>

<div class="container">
    <h2>Pinterest Downloader</h2>
    <form method="POST" action="">
        <input type="url" name="url" placeholder="Tempel link Pinterest di sini (Foto/Video)" required value="<?php echo isset($_POST['url']) ? htmlspecialchars($_POST['url']) : ''; ?>">
        <button type="submit">Ambil Media</button>
    </form>

    <?php if ($error): ?>
        <div class="error"><?php echo $error; ?></div>
    <?php endif; ?>

    <?php if ($download_url): ?>
        <div class="result">
            <h3>Media Berhasil Ditemukan!</h3>
            
            <?php if ($media_type === 'video'): ?>
                <video class="preview" src="<?php echo $download_url; ?>" controls></video>
            <?php else: ?>
                <img class="preview" src="<?php echo $download_url; ?>" alt="Preview">
            <?php endif; ?>
            
            <br>
            <a href="<?php echo $download_url; ?>" target="_blank" download class="btn-download">
                Download <?php echo ucfirst($media_type); ?>
            </a>
        </div>
    <?php endif; ?>
</div>

</body>
</html>
