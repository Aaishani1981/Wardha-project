<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Plan Your Journey — Demo</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg:#0f1724;
      --card:#fff;
      --muted:#6b7280;
      --accent1:#ff7a18;
      --accent2:#46c35f;
      --glass: rgba(255,255,255,0.06);
      --radius:14px;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family:Inter,system-ui,-apple-system,"Segoe UI",Roboto,"Helvetica Neue",Arial;
      background:linear-gradient(180deg,#071023 0%, #061327 100%);
      color:#0b1220;
      min-height:100vh;
      display:flex;
      align-items:flex-start;
      justify-content:center;
      padding:28px;
    }

    .site {
      width:1100px;
      max-width:96%;
      background:linear-gradient(180deg,#f6f7f9 0%, #ffffff 100%);
      border-radius:18px;
      box-shadow:0 10px 30px rgba(2,6,23,0.25);
      overflow:hidden;
      display:grid;
      grid-template-columns: 380px 1fr;
      gap:0;
    }

    /* left column - route planner + mini map */
    .left {
      padding:22px;
      background:linear-gradient(180deg,#fff 0%, #fffefb 100%);
      border-right:6px solid rgba(0,0,0,0.03);
      display:flex;
      flex-direction:column;
      gap:18px;
    }

    .brand {
      display:flex;
      align-items:center;
      gap:10px;
      margin-bottom:6px;
    }
    .logo {
      width:44px;height:44px;border-radius:10px;
      background:linear-gradient(135deg,var(--accent1),#ffbd45);
      display:flex;align-items:center;justify-content:center;
      color:white;font-weight:700;
      box-shadow:0 6px 18px rgba(255,122,24,0.16);
    }
    .brand h1{font-size:16px;margin:0}
    .brand p{margin:0;font-size:12px;color:var(--muted)}

    .card {
      background:var(--card);
      border-radius:12px;
      padding:16px;
      box-shadow:0 6px 18px rgba(9,30,63,0.05);
    }

    .route-form label{display:block;font-size:13px;color:var(--muted);margin-bottom:6px}
    .route-form input[type="text"], .route-form select, .route-form input[type="datetime-local"]{
      width:100%;padding:10px 12px;border-radius:8px;border:1px solid #e6e9ee;font-size:14px;
      background:#fbfdff;
    }
    .route-form .two{
      display:flex;gap:10px;
    }
    .find-btn{
      display:inline-block;margin-top:12px;background:linear-gradient(90deg,var(--accent1),#ffb14a);
      color:white;padding:10px 14px;border-radius:10px;border:none;font-weight:600;
      cursor:pointer;box-shadow:0 8px 20px rgba(255,122,24,0.15);
    }

    .mini-map{
      margin-top:6px;
      border-radius:10px;
      overflow:hidden;
      border:1px solid #eef2f6;
    }
    .mini-map img{display:block;width:100%;height:auto;max-height:240px;object-fit:cover}

    /* right column - hero + big map */
    .right {
      position:relative;
      display:flex;
      flex-direction:column;
      min-height:480px;
    }

    .hero {
      padding:28px 30px;
      background:linear-gradient(90deg,var(--accent1),#ffb04a 30%, #75d06a 100%);
      color:white;
      display:flex;
      align-items:center;
      gap:16px;
      min-height:150px;
    }
    .hero h2{margin:0;font-size:28px;letter-spacing:0.2px}
    .hero p{margin:4px 0 0;font-size:14px;opacity:0.95}

    .big-map {
      flex:1;
      padding:20px;
      background:linear-gradient(180deg,#f7fbf8 0%, #ffffff 100%);
      display:flex;
      gap:18px;
      align-items:stretch;
    }

    .map-panel{
      background:var(--card);
      border-radius:12px;
      flex:1;
      padding:12px;
      display:flex;
      align-items:center;
      justify-content:center;
      overflow:hidden;
      box-shadow:0 8px 30px rgba(9,30,63,0.06);
    }

    .map-panel img{
      width:100%;
      height:100%;
      object-fit:cover;
      border-radius:8px;
      display:block;
    }

    /* right narrow sidebar inside right column (optional) */
    .side-actions{
      width:160px;
      display:flex;
      flex-direction:column;
      gap:10px;
    }
    .pill{
      background:white;padding:10px;border-radius:10px;text-align:center;font-weight:600;
      box-shadow:0 6px 18px rgba(12,30,60,0.05);
    }

    footer{
      padding:12px 18px;color:var(--muted);
      font-size:13px;background:transparent;text-align:center;
    }

    /* responsive */
    @media(max-width:980px){
      .site{grid-template-columns:1fr; padding-bottom:0}
      .left{order:2}
      .right{order:1}
      .hero{min-height:110px}
      .side-actions{display:none}
    }
  </style>
</head>
<body>
  <div class="site" role="main">
    <!-- LEFT -->
    <aside class="left" aria-label="Route planner">
      <div class="brand">
        <div class="logo">WM</div>
        <div>
          <h1>WardhaMetroFlow</h1>
          <p>Find your fastest route</p>
        </div>
      </div>

      <div class="card route-form" aria-hidden="false">
        <label for="from">From</label>
        <input id="from" type="text" placeholder="Market Square" value="Market Square">

        <label for="to" style="margin-top:12px">To</label>
        <input id="to" type="text" placeholder="Civil Hospital" value="Civil Hospital">

        <div class="two" style="margin-top:12px">
          <div style="flex:1">
            <label for="depart">Departure</label>
            <input id="depart" type="datetime-local" value="">
          </div>
          <div style="flex:1">
            <label for="mode">Mode</label>
            <select id="mode">
              <option>Fastest</option>
              <option>Fewest transfers</option>
              <option>Walking friendly</option>
            </select>
          </div>
        </div>

        <button class="find-btn" onclick="alert('Demo: no live routing in this static page')">Find Route</button>
      </div>

      <div class="card mini-map">
        <!-- put a smaller / schematic map here -->
        <img src="map-zoom.jpg" alt="Schematic / small map image">
      </div>

      <div style="font-size:13px;color:var(--muted);margin-top:auto">
        Tip: Replace the two images (map.jpg and map-zoom.jpg) with your photos to get the same look.
      </div>
    </aside>

    <!-- RIGHT -->
    <section class="right" aria-label="Main content">
      <div class="hero">
        <div style="flex:1">
          <h2>Plan Your Journey</h2>
          <p>Find the fastest route to your destination with AI-powered suggestions</p>
        </div>
        <div class="side-actions" aria-hidden="true">
          <div class="pill">Passenger</div>
          <div class="pill">Admin</div>
        </div>
      </div>

      <div class="big-map">
        <div class="map-panel">
          <!-- the large map image from your screenshot -->
          <img src="map.jpg" alt="Large map image showing stations and routes">
        </div>
      </div>
    </section>

  </div>

  <footer>
    © Demo — Replace images and tweak colors to match your screenshots.
  </footer>

  <!-- Optional: small JS to allow replacing images quickly by dragging file to page -->
  <script>
    // quick helper: drag an image file onto the big map to preview local file.
    const mapPanel = document.querySelector('.map-panel img');
    document.addEventListener('dragover', e => e.preventDefault());
    document.addEventListener('drop', async (e) => {
      e.preventDefault();
      const f = e.dataTransfer.files?.[0];
      if (!f) return;
      if (!f.type.startsWith('image/')) { alert('Drop an image file'); return; }
      const url = URL.createObjectURL(f);
      mapPanel.src = url;
      // note: not persistent between reloads
    });
  </script>
</body>
</html>
