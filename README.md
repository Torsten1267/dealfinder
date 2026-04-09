!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DealFinder – Beste Preise täglich</title>
<style>
  *{margin:0;padding:0;box-sizing:border-box}
  body{font-family:-apple-system,BlinkMacSystemFont,'SF Pro Display','Segoe UI',sans-serif;background:#f5f5f7;color:#1d1d1f;min-height:100vh}
  nav{background:rgba(245,245,247,0.85);backdrop-filter:blur(20px);border-bottom:1px solid rgba(0,0,0,0.08);padding:0 24px;height:52px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:100}
  .nav-logo{font-size:18px;font-weight:600;letter-spacing:-0.3px;color:#1d1d1f}
  .nav-links{display:flex;gap:24px;list-style:none}
  .nav-links a{font-size:13px;color:#1d1d1f;text-decoration:none;opacity:0.8}
  .nav-links a:hover{opacity:1}
  .affiliate-bar{background:#0071e3;color:#fff;text-align:center;padding:8px 16px;font-size:12px}
  .affiliate-bar a{color:#fff;text-decoration:underline}
  .hero{text-align:center;padding:80px 24px 60px;background:linear-gradient(180deg,#fff 0%,#f5f5f7 100%)}
  .hero-tag{font-size:13px;color:#0071e3;font-weight:500;letter-spacing:0.3px;margin-bottom:16px}
  .hero h1{font-size:clamp(36px,6vw,64px);font-weight:700;letter-spacing:-1.5px;line-height:1.07;color:#1d1d1f;max-width:800px;margin:0 auto 20px}
  .hero p{font-size:19px;color:#6e6e73;max-width:500px;margin:0 auto 36px;line-height:1.5}
  .search-bar{max-width:640px;margin:48px auto 0;background:#fff;border-radius:16px;padding:6px 6px 6px 20px;display:flex;align-items:center;gap:8px;box-shadow:0 2px 20px rgba(0,0,0,0.08);border:1px solid rgba(0,0,0,0.06)}
  .search-bar input{flex:1;border:none;outline:none;font-size:16px;color:#1d1d1f;background:transparent}
  .search-bar input::placeholder{color:#aeaeb2}
  .search-bar button{background:#0071e3;color:#fff;border:none;padding:10px 20px;border-radius:12px;font-size:15px;cursor:pointer;font-weight:500;white-space:nowrap}
  .section{padding:60px 24px;max-width:1100px;margin:0 auto}
  .section-label{font-size:12px;font-weight:600;letter-spacing:0.5px;color:#0071e3;text-transform:uppercase;margin-bottom:8px}
  .section-title{font-size:clamp(24px,4vw,40px);font-weight:700;letter-spacing:-0.5px;margin-bottom:8px;color:#1d1d1f}
  .section-sub{font-size:17px;color:#6e6e73;margin-bottom:40px}
  .categories{display:flex;gap:10px;flex-wrap:wrap;margin-bottom:36px}
  .cat-pill{padding:8px 18px;border-radius:20px;border:1px solid rgba(0,0,0,0.12);background:#fff;font-size:14px;cursor:pointer;color:#1d1d1f;transition:all 0.15s}
  .cat-pill:hover,.cat-pill.active{background:#0071e3;color:#fff;border-color:#0071e3}
  .deals-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(240px,1fr));gap:16px}
  .deal-card{background:#fff;border-radius:18px;overflow:hidden;border:1px solid rgba(0,0,0,0.06);transition:transform 0.2s,box-shadow 0.2s}
  .deal-card:hover{transform:translateY(-4px);box-shadow:0 12px 40px rgba(0,0,0,0.12)}
  .deal-img{width:100%;height:180px;background:#f5f5f7;display:flex;align-items:center;justify-content:center;font-size:48px;position:relative}
  .deal-badge{position:absolute;top:12px;left:12px;color:#fff;font-size:11px;font-weight:600;padding:4px 10px;border-radius:20px}
  .deal-badge.sale{background:#ff3b30}
  .deal-badge.aff{background:#34c759}
  .deal-info{padding:16px}
  .deal-info h3{font-size:15px;font-weight:600;margin-bottom:4px;color:#1d1d1f}
  .deal-info .shop{font-size:12px;color:#6e6e73;margin-bottom:10px}
  .price-row{display:flex;align-items:baseline;gap:8px;margin-bottom:12px}
  .price-now{font-size:20px;font-weight:700;color:#1d1d1f}
  .price-old{font-size:13px;color:#aeaeb2;text-decoration:line-through}
  .price-save{font-size:12px;color:#34c759;font-weight:600}
  .deal-actions{display:flex;gap:8px}
  .btn-deal{flex:1;background:#0071e3;color:#fff;border:none;padding:10px;border-radius:10px;font-size:13px;font-weight:600;cursor:pointer;text-decoration:none;display:flex;align-items:center;justify-content:center;gap:4px}
  .btn-deal:hover{background:#005bbf}
  .btn-pin{background:#e60023;border:none;padding:10px 12px;border-radius:10px;cursor:pointer;color:#fff;font-size:13px;font-weight:600}
  .btn-pin:hover{background:#c0001d}
  .no-results{text-align:center;padding:40px;color:#6e6e73;font-size:16px;display:none}
  .features{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:16px}
  .feat-card{background:#fff;border-radius:18px;padding:28px 24px;border:1px solid rgba(0,0,0,0.06)}
  .feat-icon{font-size:28px;margin-bottom:14px}
  .feat-card h3{font-size:16px;font-weight:600;margin-bottom:8px;color:#1d1d1f}
  .feat-card p{font-size:14px;color:#6e6e73;line-height:1.5}
  footer{background:#f5f5f7;border-top:1px solid rgba(0,0,0,0.1);padding:40px 24px;text-align:center;color:#6e6e73;font-size:13px}
  .footer-links{margin-bottom:12px;display:flex;flex-wrap:wrap;justify-content:center;gap:4px}
  .footer-links a{color:#6e6e73;margin:0 12px;text-decoration:none}
  .footer-links a:hover{color:#0071e3}
  .footer-aff{font-size:12px;color:#aeaeb2;max-width:600px;margin:12px auto 0;line-height:1.6}
  @media(max-width:640px){.nav-links{display:none}.hero{padding:60px 16px 40px}.section{padding:40px 16px}}
</style>
</head>
<body>

<div class="affiliate-bar">
  Diese Seite enthält Affiliate-Links. Bei einem Kauf erhalte ich eine kleine Provision – für dich entstehen keine Mehrkosten. <a href="#footer-aff">Mehr erfahren</a>
</div>

<nav>
  <div class="nav-logo">DealFinder</div>
  <ul class="nav-links">
    <li><a href="#deals">Deals</a></li>
    <li><a href="#kategorien">Kategorien</a></li>
    <li><a href="https://pinterest.com" target="_blank">Pinterest</a></li>
    <li><a href="#ueber-uns">Über uns</a></li>
  </ul>
</nav>

<div class="hero">
  <div class="hero-tag">Täglich aktualisierte Deals</div>
  <h1>Die besten Preise.<br>Einfach gefunden.</h1>
  <p>Günstigste Artikel aus dem Netz – kuratiert, verglichen und direkt verlinkt.</p>
  <div class="search-bar">
    <input type="text" id="search-input" placeholder="Artikel suchen – z. B. Kopfhörer, Sneaker, Kaffeemaschine …" oninput="searchDeals()">
    <button onclick="searchDeals()">Suchen</button>
  </div>
</div>

<div class="section" id="deals">
  <div class="section-label">Top Deals heute</div>
  <div class="section-title">Günstig. Geprüft. Sofort.</div>
  <p class="section-sub">Die besten Affiliate-Angebote – täglich aktualisiert.</p>

  <div class="categories" id="kategorien">
    <div class="cat-pill active" onclick="filterCat('alle',this)">Alle</div>
    <div class="cat-pill" onclick="filterCat('elektronik',this)">Elektronik</div>
    <div class="cat-pill" onclick="filterCat('mode',this)">Mode</div>
    <div class="cat-pill" onclick="filterCat('haushalt',this)">Haushalt</div>
    <div class="cat-pill" onclick="filterCat('sport',this)">Sport</div>
    <div class="cat-pill" onclick="filterCat('beauty',this)">Beauty</div>
  </div>

  <div class="deals-grid" id="deals-grid"></div>
  <p class="no-results" id="no-results">Keine Produkte gefunden. Versuche einen anderen Suchbegriff.</p>
</div>

<div class="section" id="ueber-uns">
  <div class="section-label">Warum DealFinder?</div>
  <div class="section-title">Alles an einem Ort.</div>
  <div class="features">
    <div class="feat-card"><div class="feat-icon">🔍</div><h3>Automatische Preissuche</h3><p>Wir durchsuchen täglich tausende Shops und zeigen nur echte Tiefstpreise.</p></div>
    <div class="feat-card"><div class="feat-icon">📌</div><h3>Pinterest Integration</h3><p>Jeden Deal direkt auf deinen Pinterest-Board pinnen – teilen mit einem Klick.</p></div>
    <div class="feat-card"><div class="feat-icon">💰</div><h3>Immer kostenlos</h3><p>Für dich entstehen keine Mehrkosten. Wir verdienen eine kleine Provision vom Händler.</p></div>
    <div class="feat-card"><div class="feat-icon">🔒</div><h3>Geprüfte Händler</h3><p>Nur seriöse Shops wie Amazon, Zalando, Otto & Co. Sicher einkaufen.</p></div>
  </div>
</div>

<footer>
  <div class="footer-links">
    <a href="#">Impressum</a>
    <a href="#">Datenschutz</a>
    <a href="#">AGB</a>
    <a href="#">Kontakt</a>
    <a href="https://pinterest.com" target="_blank">Pinterest</a>
  </div>
  <p>© 2026 DealFinder · Alle Preise ohne Gewähr · Preise können sich ändern</p>
  <p class="footer-aff" id="footer-aff">
    <strong>Affiliate-Hinweis:</strong> Diese Website enthält Affiliate-Links zu Amazon, Zalando, Otto und weiteren Shops. Wenn du über einen dieser Links einkaufst, erhalte ich eine kleine Provision – für dich entstehen dabei keine zusätzlichen Kosten. Als Amazon-Partner verdiene ich an qualifizierten Käufen.
  </p>
</footer>

<script>
const products = [
  { title:'Sony WH-1000XM5 Kopfhörer', shop:'Amazon', priceNow:'279,00', priceOld:'349,00', save:'-70 €', emoji:'🎧', badge:'-20%', badgeClass:'sale', cat:'elektronik', url:'https://www.amazon.de/dp/B09XS7JWHH?tag=DEIN-TAG-21', pin:'Sony WH-1000XM5 – Nur 279€ statt 349€!' },
  { title:'Nike Air Max 270', shop:'Zalando', priceNow:'89,95', priceOld:'129,95', save:'-40 €', emoji:'👟', badge:'Zalando', badgeClass:'aff', cat:'mode', url:'https://www.zalando.de', pin:'Nike Air Max 270 – Jetzt nur 89,95€ bei Zalando!' },
  { title:'Philips Kaffeemaschine 3000', shop:'Amazon', priceNow:'149,00', priceOld:'229,00', save:'-80 €', emoji:'☕', badge:'-35%', badgeClass:'sale', cat:'haushalt', url:'https://www.amazon.de/s?k=philips+kaffeemaschine&tag=DEIN-TAG-21', pin:'Philips Kaffeemaschine – 149€ statt 229€!' },
  { title:'Apple AirPods Pro 2', shop:'Amazon', priceNow:'199,00', priceOld:'279,00', save:'-80 €', emoji:'🎵', badge:'-29%', badgeClass:'sale', cat:'elektronik', url:'https://www.amazon.de/s?k=airpods+pro+2&tag=DEIN-TAG-21', pin:'Apple AirPods Pro 2 – Nur 199€!' },
  { title:'Adidas Ultraboost 22', shop:'Zalando', priceNow:'99,95', priceOld:'179,95', save:'-80 €', emoji:'🏃', badge:'Zalando', badgeClass:'aff', cat:'sport', url:'https://www.zalando.de', pin:'Adidas Ultraboost 22 – 99,95€ statt 179,95€!' },
  { title:'Oral-B iO Series 8', shop:'Amazon', priceNow:'79,99', priceOld:'149,99', save:'-70 €', emoji:'🪥', badge:'-47%', badgeClass:'sale', cat:'beauty', url:'https://www.amazon.de/s?k=oral-b+io+series+8&tag=DEIN-TAG-21', pin:'Oral-B iO Series 8 – Nur 79,99€!' },
  { title:'Samsung 4K Smart TV 55"', shop:'Amazon', priceNow:'449,00', priceOld:'699,00', save:'-250 €', emoji:'📺', badge:'-36%', badgeClass:'sale', cat:'elektronik', url:'https://www.amazon.de/s?k=samsung+4k+tv+55&tag=DEIN-TAG-21', pin:'Samsung 4K TV 55" – 449€ statt 699€!' },
  { title:"Levi's 501 Original Jeans", shop:'Zalando', priceNow:'59,95', priceOld:'99,95', save:'-40 €', emoji:'👖', badge:'Zalando', badgeClass:'aff', cat:'mode', url:'https://www.zalando.de', pin:"Levi's 501 Jeans – Nur 59,95€ bei Zalando!" }
];

function renderCards(list) {
  const grid = document.getElementById('deals-grid');
  const none = document.getElementById('no-results');
  grid.innerHTML = '';
  if (!list.length) { none.style.display='block'; return; }
  none.style.display = 'none';
  list.forEach(p => {
    grid.innerHTML += `
      <div class="deal-card">
        <div class="deal-img">${p.emoji}<span class="deal-badge ${p.badgeClass}">${p.badge}</span></div>
        <div class="deal-info">
          <h3>${p.title}</h3>
          <div class="shop">via ${p.shop}</div>
          <div class="price-row">
            <span class="price-now">${p.priceNow} €</span>
            <span class="price-old">${p.priceOld} €</span>
            <span class="price-save">${p.save}</span>
          </div>
          <div class="deal-actions">
            <a class="btn-deal" href="${p.url}" target="_blank" rel="noopener sponsored">Zum Deal ↗</a>
            <button class="btn-pin" onclick="pinProduct('${p.pin}','${p.url}')">❤ Pin</button>
          </div>
        </div>
      </div>`;
  });
}

function searchDeals() {
  const q = document.getElementById('search-input').value.toLowerCase().trim();
  document.querySelectorAll('.cat-pill').forEach(p => p.classList.remove('active'));
  document.querySelector('.cat-pill').classList.add('active');
  renderCards(q ? products.filter(p => p.title.toLowerCase().includes(q) || p.shop.toLowerCase().includes(q)) : products);
}

function filterCat(cat, el) {
  document.querySelectorAll('.cat-pill').forEach(p => p.classList.remove('active'));
  el.classList.add('active');
  document.getElementById('search-input').value = '';
  renderCards(cat === 'alle' ? products : products.filter(p => p.cat === cat));
}

function pinProduct(desc, url) {
  const base = 'https://pinterest.com/pin/create/button/';
  const params = new URLSearchParams({ url: url, description: desc });
  const win = window.open(base + '?' + params, 'pinterest', 'width=750,height=550');
  if (!win) window.location.href = base + '?' + params;
}

renderCards(products);
</script>
</body>
</html>
