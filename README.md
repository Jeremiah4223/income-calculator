# income-calculator
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Income Calculator Suite</title>
  <meta name="description" content="Free calculators to estimate online income from websites, YouTube, affiliate marketing, and SaaS." />

  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f6f8;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 800px;
      margin: 40px auto;
      background: #fff;
      padding: 24px;
      border-radius: 10px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.08);
    }
    h1 {
      margin-bottom: 5px;
    }
    p {
      color: #555;
    }
    .tabs {
      display: flex;
      gap: 10px;
      margin: 20px 0;
      flex-wrap: wrap;
    }
    .tab {
      padding: 10px 14px;
      border-radius: 6px;
      background: #e5e7eb;
      cursor: pointer;
      font-weight: bold;
    }
    .tab.active {
      background: #2563eb;
      color: white;
    }
    .calc {
      display: none;
    }
    .calc.active {
      display: block;
    }
    label {
      display: block;
      margin-top: 12px;
      font-weight: bold;
    }
    input {
      width: 100%;
      padding: 10px;
      margin-top: 6px;
      border-radius: 6px;
      border: 1px solid #ccc;
      font-size: 16px;
    }
    button {
      margin-top: 18px;
      width: 100%;
      padding: 12px;
      background: #2563eb;
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      cursor: pointer;
    }
    .results {
      margin-top: 20px;
      background: #f1f5f9;
      padding: 15px;
      border-radius: 8px;
      font-size: 16px;
    }
    footer {
      margin-top: 30px;
      font-size: 14px;
      text-align: center;
      color: #555;
    }
  </style>
</head>

<body>
  <div class="container">
    <h1>Income Calculator Suite</h1>
    <p>Estimate earnings from different online income models.</p>

    <div class="tabs">
      <div class="tab active" onclick="showCalc('website', this)">Website</div>
      <div class="tab" onclick="showCalc('youtube', this)">YouTube</div>
      <div class="tab" onclick="showCalc('affiliate', this)">Affiliate</div>
      <div class="tab" onclick="showCalc('saas', this)">SaaS</div>
    </div>

    <!-- WEBSITE CALCULATOR -->
    <div id="website" class="calc active">
      <label>Monthly Visitors</label>
      <input id="w_visitors" type="number" placeholder="e.g. 5000">

      <label>Conversion Rate (%)</label>
      <input id="w_conv" type="number" placeholder="e.g. 2">

      <label>Revenue Per Conversion ($)</label>
      <input id="w_rev" type="number" placeholder="e.g. 25">

      <button onclick="calcWebsite()">Calculate</button>
      <div class="results" id="w_out"></div>
    </div>

    <!-- YOUTUBE CALCULATOR -->
    <div id="youtube" class="calc">
      <label>Monthly Views</label>
      <input id="y_views" type="number" placeholder="e.g. 100000">

      <label>RPM ($ per 1,000 views)</label>
      <input id="y_rpm" type="number" placeholder="e.g. 4">

      <button onclick="calcYouTube()">Calculate</button>
      <div class="results" id="y_out"></div>
    </div>

    <!-- AFFILIATE CALCULATOR -->
    <div id="affiliate" class="calc">
      <label>Monthly Clicks</label>
      <input id="a_clicks" type="number" placeholder="e.g. 1000">

      <label>Conversion Rate (%)</label>
      <input id="a_conv" type="number" placeholder="e.g. 3">

      <label>Commission Per Sale ($)</label>
      <input id="a_comm" type="number" placeholder="e.g. 50">

      <button onclick="calcAffiliate()">Calculate</button>
      <div class="results" id="a_out"></div>
    </div>

    <!-- SAAS CALCULATOR -->
    <div id="saas" class="calc">
      <label>Number of Customers</label>
      <input id="s_cust" type="number" placeholder="e.g. 25">

      <label>Monthly Price ($)</label>
      <input id="s_price" type="number" placeholder="e.g. 29">

      <button onclick="calcSaaS()">Calculate</button>
      <div class="results" id="s_out"></div>
    </div>

    <footer>
      Monetize with affiliate tools, ads, or premium features.
    </footer>
  </div>

  <script>
    function showCalc(id, el) {
      document.querySelectorAll('.calc').forEach(c => c.classList.remove('active'));
      document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
      document.getElementById(id).classList.add('active');
      el.classList.add('active');
    }

    function calcWebsite() {
      const m = w_visitors.value * (w_conv.value / 100) * w_rev.value;
      w_out.innerHTML = `Monthly: $${m.toFixed(2)}<br>Yearly: $${(m * 12).toFixed(2)}`;
    }

    function calcYouTube() {
      const m = (y_views.value / 1000) * y_rpm.value;
      y_out.innerHTML = `Monthly: $${m.toFixed(2)}<br>Yearly: $${(m * 12).toFixed(2)}`;
    }

    function calcAffiliate() {
      const m = a_clicks.value * (a_conv.value / 100) * a_comm.value;
      a_out.innerHTML = `Monthly: $${m.toFixed(2)}<br>Yearly: $${(m * 12).toFixed(2)}`;
    }

    function calcSaaS() {
      const m = s_cust.value * s_price.value;
      s_out.innerHTML = `Monthly Recurring Revenue: $${m.toFixed(2)}<br>Annual: $${(m * 12).toFixed(2)}`;
    }
  </script>
</body>
</html>
