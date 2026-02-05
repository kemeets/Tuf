<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galeri Foto - Jual Foto</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background-color: #f5f5f5;
        }

        header {
            background-color: #333;
            color: white;
            padding: 20px;
            text-align: center;
        }

        .container {
            max-width: 1200px;
            margin: 30px auto;
            padding: 0 20px;
        }

        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }

        .photo-card {
            background: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            transition: transform 0.3s;
        }

        .photo-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 4px 12px rgba(0,0,0,0.2);
        }

        .photo-card img {
            width: 100%;
            height: 250px;
            object-fit: cover;
        }

        .photo-info {
            padding: 15px;
        }

        .photo-title {
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 10px;
        }

        .photo-price {
            color: #e74c3c;
            font-size: 20px;
            font-weight: bold;
            margin-bottom: 10px;
        }

        .buy-button {
            background-color: #3498db;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
            transition: background-color 0.3s;
        }

        .buy-button:hover {
            background-color: #2980b9;
        }

        .search-bar {
            text-align: center;
            margin: 20px 0;
        }

        .search-bar input {
            padding: 10px;
            width: 300px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <header>
        <h1>🖼️ Galeri Foto Premium</h1>
        <p>Koleksi foto berkualitas tinggi untuk kebutuhan Anda</p>
    </header>

    <div class="container">
        <div class="search-bar">
            <input type="text" id="searchInput" placeholder="Cari foto...">
        </div>

        <div class="gallery" id="gallery">
            <!-- Foto akan ditampilkan di sini -->
        </div>
    </div>

    <script>
        // Data foto (contoh)
        const photos = [
            {
                id: 1,
                title: "Pemandangan Gunung",
                price: 150000,
                image: "https://via.placeholder.com/300x250/4CAF50/ffffff?text=Gunung",
                description: "Foto pemandangan gunung yang indah"
            },
            {
                id: 2,
                title: "Pantai Sunset",
                price: 200000,
                image: "https://via.placeholder.com/300x250/FF9800/ffffff?text=Pantai",
                description: "Momen sunset di pantai"
            },
            {
                id: 3,
                title: "Kota Malam",
                price: 175000,
                image: "https://via.placeholder.com/300x250/2196F3/ffffff?text=Kota",
                description: "Pemandangan kota di malam hari"
            },
            {
                id: 4,
                title: "Hutan Tropis",
                price: 180000,
                image: "https://via.placeholder.com/300x250/8BC34A/ffffff?text=Hutan",
                description: "Keindahan hutan tropis"
            },
            {
                id: 5,
                title: "Danau Tenang",
                price: 160000,
                image: "https://via.placeholder.com/300x250/00BCD4/ffffff?text=Danau",
                description: "Danau dengan air yang jernih"
            },
            {
                id: 6,
                title: "Bunga Sakura",
                price: 190000,
                image: "https://via.placeholder.com/300x250/E91E63/ffffff?text=Sakura",
                description: "Bunga sakura yang mekar"
            }
        ];

        // Fungsi untuk menampilkan foto
        function displayPhotos(photoList) {
            const gallery = document.getElementById('gallery');
            gallery.innerHTML = '';

            photoList.forEach(photo => {
                const card = document.createElement('div');
                card.className = 'photo-card';
                card.innerHTML = `
                    <img src="${photo.image}" alt="${photo.title}">
                    <div class="photo-info">
                        <div class="photo-title">${photo.title}</div>
                        <div class="photo-price">Rp ${photo.price.toLocaleString('id-ID')}</div>
                        <button class="buy-button" onclick="buyPhoto(${photo.id})">Beli Sekarang</button>
                    </div>
                `;
                gallery.appendChild(card);
            });
        }

        // Fungsi untuk membeli foto
        function buyPhoto(id) {
            const photo = photos.find(p => p.id === id);
            alert(`Terima kasih! Anda akan membeli:\n${photo.title}\nHarga: Rp ${photo.price.toLocaleString('id-ID')}\n\nSilakan lanjutkan ke pembayaran.`);
            // Di sini Anda bisa menambahkan integrasi payment gateway
        }

        // Fungsi pencarian
        document.getElementById('searchInput').addEventListener('input', function(e) {
            const searchTerm = e.target.value.toLowerCase();
            const filtered = photos.filter(photo => 
                photo.title.toLowerCase().includes(searchTerm)
            );
            displayPhotos(filtered);
        });

        // Tampilkan foto saat halaman dimuat
        displayPhotos(photos);
    </script>
</body>
</html>
