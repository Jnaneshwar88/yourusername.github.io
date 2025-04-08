<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>YouTube Thumbnail Downloader</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            text-align: center;
        }
        .container {
            background: #f9f9f9;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        button {
            background: #ff0000;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background: #cc0000;
        }
        #thumbnail-container {
            margin: 20px 0;
        }
        #thumbnail {
            max-width: 100%;
            border: 1px solid #ddd;
        }
        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>YouTube Thumbnail Downloader</h1>
        <p>Get high-quality thumbnails from any YouTube video</p>
        
        <input type="text" id="video-url" placeholder="Paste YouTube video URL here...">
        <button onclick="fetchThumbnail()">Get Thumbnail</button>
        
        <div id="thumbnail-container" class="hidden">
            <img id="thumbnail" src="" alt="YouTube Thumbnail">
            <br>
            <button onclick="downloadThumbnail()">Download Thumbnail</button>
        </div>
    </div>

    <script>
        function fetchThumbnail() {
            const videoUrl = document.getElementById('video-url').value.trim();
            const videoId = extractVideoId(videoUrl);
            
            if (!videoId) {
                alert('Please enter a valid YouTube URL');
                return;
            }
            
            const thumbnailUrl = `https://img.youtube.com/vi/${videoId}/maxresdefault.jpg`;
            const thumbnailImg = document.getElementById('thumbnail');
            
            thumbnailImg.onload = function() {
                document.getElementById('thumbnail-container').classList.remove('hidden');
            };
            
            thumbnailImg.onerror = function() {
                // Fallback to high quality if maxres doesn't exist
                thumbnailImg.src = `https://img.youtube.com/vi/${videoId}/hqdefault.jpg`;
            };
            
            thumbnailImg.src = thumbnailUrl;
        }
        
        function extractVideoId(url) {
            const regExp = /^.*(youtu.be\/|v\/|u\/\w\/|embed\/|watch\?v=|&v=)([^#&?]*).*/;
            const match = url.match(regExp);
            return (match && match[2].length === 11) ? match[2] : null;
        }
        
        function downloadThumbnail() {
            const thumbnail = document.getElementById('thumbnail');
            const link = document.createElement('a');
            link.href = thumbnail.src;
            link.download = 'youtube-thumbnail.jpg';
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }
    </script>
</body>
</html>
