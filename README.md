<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Top Up Game</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(to right, #2c3e50, #4ca1af);
            color: white;
            text-align: center;
            max-width: 1200px;
            margin: 20px auto;
            padding: 0 20px;
            overflow-x: hidden;
        }
        h1 {
            font-size: 40px;
            text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.5);
        }
        h2 {
            font-size: 28px;
            color: #f1c40f;
            margin-top: 40px;
        }
        .price-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }
        .price-item {
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
            width: 220px;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            backdrop-filter: blur(10px);
            animation: float 3s infinite ease-in-out;
        }
        .price-item:hover {
            transform: translateY(-10px) scale(1.05);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.5);
        }
        .whatsapp-link {
            text-decoration: none;
            color: white;
            background: #27ae60;
            padding: 12px 18px;
            border-radius: 8px;
            display: inline-block;
            transition: 0.3s;
        }
        .whatsapp-link:hover {
            background: #219653;
            transform: scale(1.05);
        }
        input {
            width: 90%;
            padding: 8px;
            margin-top: 10px;
            border-radius: 5px;
            border: none;
            text-align: center;
        }
        @keyframes float {
            0% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
            100% { transform: translateY(0); }
        }
    </style>
</head>
<body>

<h1>Top Up Game</h1>

<h2>Free Fire</h2>
<div class="price-container" id="freeFireContainer"></div>

<h2>Mobile Legends</h2>
<div class="price-container" id="mlContainer"></div>

<script>
    const produk = {
        'Free Fire': [
            ['Level Up Pass', 20000], [5, 2000], [15, 5000], [50, 10000], [80, 15000],
            [100, 20000], [140, 24000], [200, 32000], [250, 39000], [300, 45000],[350,50000],[400,58000], [500,76.000], [720,96000],[1000,137000],['Membership Mingguan',35000], ['Membership Bulanan', 95000]
        ],
        'Mobile Legends': [
            [5, 3000], [12, 5000], [28, 13000], [36, 15000], [44, 17000], [74, 25000],[86,28000],[172,54000],[222,65000],[370,108000],[568,157000],['Weekly Diamond Pass',34000]
        ]
    };

    function buatProduk(game, containerId) {
        const container = document.getElementById(containerId);
        produk[game].forEach(([nama, harga]) => {
            let item = document.createElement('div');
            item.className = 'price-item';
            item.innerHTML = `
                <strong>${nama} DM</strong>: Rp. ${harga}
                <input type="text" id="nomorTujuan${game.replace(/\s+/g, '')}${nama}" placeholder="Nomor tujuan">
                <a href="#" onclick="beliProduk('${game}', '${nama}', document.getElementById('nomorTujuan${game.replace(/\s+/g, '')}${nama}').value)" class="whatsapp-link">Beli</a>
            `;
            container.appendChild(item);
        });
    }

    function beliProduk(game, jumlahDM, nomorTujuan) {
        let nomorWhatsApp = '6282245184223';
        let pesan = encodeURIComponent(`Halo, saya ingin membeli ${jumlahDM} DM untuk ${game}. Nomor tujuan: ${nomorTujuan}.`);
        window.open(`https://wa.me/${nomorWhatsApp}?text=${pesan}`, '_blank');
    }

    buatProduk('Free Fire', 'freeFireContainer');
    buatProduk('Mobile Legends', 'mlContainer');
</script>

</body>
</html>
