<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Stock Details (21 Sep 2025)</title>
  <style>
    * { box-sizing: border-box; }

    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: #f5f7fa;
      color: #2c3e50;
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }

    header {
      background: linear-gradient(90deg, #0f2027, #203a43, #2c5364);
      color: #ffffff;
      padding: 1.5rem;
      text-align: center;
      font-size: 2rem;
      font-weight: 600;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
      letter-spacing: 0.8px;
    }

    .container {
      display: flex;
      flex: 1;
    }

    .sidebar {
      background-color: #1e272e;
      color: #ffffff;
      width: 250px;
      padding: 1.2rem;
      display: flex;
      flex-direction: column;
      gap: 0.6rem;
    }

    .sidebar button {
      background: transparent;
      border: none;
      color: #dcdde1;
      padding: 0.8rem 1rem;
      width: 100%;
      text-align: left;
      font-size: 1rem;
      cursor: pointer;
      border-left: 4px solid transparent;
      border-radius: 4px;
      transition: all 0.3s ease;
    }

    .sidebar button:hover,
    .sidebar button.active {
      background: #0abde3;
      color: #ffffff;
      border-left: 4px solid #00cec9;
      font-weight: bold;
    }

    .content {
      flex: 1;
      padding: 2rem;
      background: #f5f7fa;
      overflow-y: auto;
    }

    .location-title {
      font-size: 1.6rem;
      font-weight: bold;
      margin: 0 0 1.5rem;
      position: relative;
      padding-bottom: 0.6rem;
    }
    .location-title::after {
      content: "";
      position: absolute;
      left: 0;
      bottom: 0;
      width: 100%;
      height: 6px;
      border-radius: 3px;
    }
    .location-title.akluj::after { background: #6c5ce7; }     /* Purple */
    .location-title.jamner::after { background: #0984e3; }   /* Blue */
    .location-title.savda::after { background: #00b894; }    /* Green */
    .location-title.shirpur::after { background: #e17055; }  /* Orange */

    .section-title {
      font-size: 1.3rem;
      margin: 1.5rem 0 0.5rem;
      color: #34495e;
      border-bottom: 2px solid #dcdde1;
      padding-bottom: 0.4rem;
    }

    .card-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 1rem;
      margin-top: 1rem;
    }

    .card {
      background: #ffffff;
      border-left: 6px solid #3498db;
      border-radius: 6px;
      padding: 1rem;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.06);
      transition: transform 0.2s ease;
    }

    .card:hover { transform: translateY(-3px); }

    .card h4 {
      margin: 0;
      font-size: 1rem;
      font-weight: 600;
      color: #2c3e50;
    }

    .card p {
      margin: 0.4rem 0 0;
      font-size: 1.2rem;
      font-weight: bold;
      color: #2f3542;
    }
  </style>
</head>
<body>
  <header>Stock Details (21 Sep 2025)</header>
  <div class="container">
    <div class="sidebar">
      <button onclick="showStock('akluj')" id="btn-akluj" class="active">1. Akluj</button>
      <button onclick="showStock('jamner')" id="btn-jamner">2. Jamner</button>
      <button onclick="showStock('savda')" id="btn-savda">3. Savda</button>
      <button onclick="showStock('shirpur')" id="btn-shirpur">4. Shirpur Chopada</button>
    </div>
    <div class="content" id="stockContent"></div>
  </div>

  <script>
    const createCards = (items) => {
      return items.map(item => `
        <div class="card">
          <h4>${item.name}</h4>
          <p>${item.qty}</p>
        </div>
      `).join('');
    };

    const stockData = {
      akluj: {
        balance: [
          { name: "Roshana Box (Nos)", qty: "4059 nos" },
          { name: "Laibaah Box", qty: "7115 nos" },
          { name: "Haniya Box", qty: "0 nos" },
          { name: "Vaccum Bag 13kg", qty: "907.23 KG" },
          { name: "Vaccum Bag 7kg", qty: "170.682 KG" },
          { name: "PE Form 1.5 MM (Nos)", qty: "60718 nos" },
          { name: "Sachets (Nos)", qty: "9859 nos" },
          { name: "Fevicol (kg)", qty: "40 KG" },
          { name: "Germination Paper (kg)", qty: "387.18 KG" },
          { name: "Bavistin", qty: "0 KG" },
          { name: "Truti (kg)", qty: "220 KG" },
          { name: "Bleaching Powder (g)", qty: "24.3 KG" },
          { name: "Rubber (kg)", qty: "29.5 KG" },
          { name: "Roshana Sticker (Nos)", qty: "349744 nos" }
        ]
      },

      jamner: {
        balance: [
          { name: "Roshana Box (Nos)", qty: "7265 nos" },
          { name: "Vaccum Bag 13kg", qty: "2034.93 KG" },
          { name: "PE Form 1.5 MM (Nos)", qty: "163291 nos" },
          { name: "Sachets (Nos)", qty: "26111 nos" },
          { name: "Fevicol (kg)", qty: "244.5 KG" },
          { name: "Germination Paper (kg)", qty: "1209.8 KG" },
          { name: "Fungicide (kg)", qty: "13 KG" },
          { name: "Truti (kg)", qty: "497.8 KG" },
          { name: "Bleaching Powder (g)", qty: "6.3 KG" },
          { name: "Rubber (kg)", qty: "19 KG" },
          { name: "Roshana Sticker (Nos)", qty: "747486 nos" }
        ]
      },
      savda: {
        balance: [
          { name: "King Brown Box (Nos)", qty: "2300" },
          { name: "Bandhan Premium", qty: "1500" },
          { name: "Alaa White Box (Nos)", qty: "500" },
          { name: "Roshana Box (Nos)", qty: "0" },
          { name: "Laibaah Box (Nos)", qty: "350" },
          { name: "Haniya Box (Nos)", qty: "800" },
          { name: "Shabad Box (Nos)", qty: "280" },
          { name: "Vaccum Bag 13kg", qty: "1720" },
          { name: "PE Form 1.5 MM (Nos)", qty: "0" },
          { name: "Sachets (Nos)", qty: "0" },
          { name: "Fevicol (kg)", qty: "0" },
          { name: "Germination Paper (kg)", qty: "850" },
          { name: "Fungicide (kg)", qty: "46" },
          { name: "Truti (kg)", qty: "0" },
          { name: "Bleaching Powder (g)", qty: "0" },
          { name: "Rubber (kg)", qty: "0" },
          { name: "King Sticker (Nos)", qty: "56000" },
          { name: "Alaa Sticker (Nos)", qty: "4650000" },
          { name: "Roshana Sticker (Nos)", qty: "1610000" },
          { name: "Other Sticker", qty: "2520000" }
        ]
      },

      shirpur: {
        balance: [
          { name: "Roshana Box (Nos)", qty: "3307 nos" },
          { name: "Vaccum Bag 13kg", qty: "306.743 KG" },
          { name: "PE Form 1.5 MM (Nos)", qty: "22691 nos" },
          { name: "Sachets (Nos)", qty: "7409 nos" },
          { name: "Fevicol (kg)", qty: "75 KG" },
          { name: "Germination Paper (kg)", qty: "78.16 KG" },
          { name: "Fungicide (kg)", qty: "7 KG" },
          { name: "Truti (kg)", qty: "40 KG" },
          { name: "Bleaching Powder (g)", qty: "2.7 G" },
          { name: "Rubber (kg)", qty: "2.6 KG" },
          { name: "Roshana Sticker (Nos)", qty: "624764" }
        ]
      }
    };

    function showStock(area) {
      document.querySelectorAll(".sidebar button").forEach(btn => btn.classList.remove("active"));
      document.getElementById(`btn-${area}`).classList.add("active");

      const data = stockData[area];
      let html = `<div class="location-title ${area}">${area.charAt(0).toUpperCase() + area.slice(1)} Stock Details (21 Sep 2025)</div>`;

      if (data.inward) {
        html += `<div class="section-title">Inward</div><div class="card-grid">${createCards(data.inward)}</div>`;
      }
      if (data.outward) {
        html += `<div class="section-title">Outward</div><div class="card-grid">${createCards(data.outward)}</div>`;
      }
      if (data.balance) {
        html += `<div class="section-title">Balance</div><div class="card-grid">${createCards(data.balance)}</div>`;
      }

      document.getElementById("stockContent").innerHTML = html;
    }

    showStock("akluj");
  </script>
</body>
</html>
