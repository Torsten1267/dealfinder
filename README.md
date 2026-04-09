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
  .nav-logo{font-size:18px;font-weight:600;letter-spacing:-0.3px}
  .nav-links{display:flex;gap:24px;list-style:none}
  .nav-links a{font-size:13px;color:#1d1d1f;text-decoration:none;opacity:0.8}
  .nav-links a:hover{opacity:1}
  .aff-bar{background:#0071e3;color:#fff;text-align:center;padding:8px 16px;font-size:12px}
  .aff-bar a{color:#fff;text-decoration:underline}
  .hero{text-align:center;padding:80px 24px 60px;background:linear-gradient(180deg,#fff 0%,#f5f5f7 100%)}
  .hero-tag{font-size:13px;color:#0071e3;font-weight:500;letter-spacing:0.3px;margin-bottom:16px}
  .hero h1{font-size:clamp(36px,6vw,64px);font-weight:700;letter-spacing:-1.5px;line-height:1.07;max-width:800px;margin:0 auto 20px}
  .hero p{font-size:19px;color:#6e6e73;max-width:500px;margin:0 auto 36px;line-height:1.5}
  .search-bar{max-width:640px;margin:0 auto;background:#fff;border-radius:16px;padding:6px 6px 6px 20px;display:flex;align-items:center;gap:8px;box-shadow:0 2px 20px rgba(0,0,0,0.08);border:1px solid rgba(0,0,0,0.06)}
  .search-bar input{flex:1;border:none;outline:none;font-size:16px;background:transparent}
  .search-bar button{background:#0071e3;color:#fff;border:none;padding:10px 20px;border-radius:12px;font-size:15px;cursor:pointer;font-weight:500}
  .shop-logos{display:flex;gap:12px;justify-content:center;flex-wrap:wrap;padding:32px 24px 0}
  .shop-pill{background:#fff;border:1px solid rgba(0,0,0,0.08);border-radius:20px;padding:8px 18px;font-size:13px;font-weight:600;cursor:pointer;transition:all 0.15s;color:#1d1d1f}
  .shop-pill:hover,.shop-pill.active{background:#0071e3;color:#fff;border-color:#0071e3}
  .section{padding:48px 24px;max-width:1200px;margin:0 auto}
  .section-header{display:flex;align-items:baseline;justify-content:space-between;margin-bottom:8px}
  .section-label{font-size:12px;font-weight:600;letter-spacing:0.5px;color:#0071e3;text-transform:uppercase}
  .section-title{font-size:clamp(22px,4vw,36px);font-weight:700;letter-spacing:-0.5px;margin-bottom:6px}
  .section-sub{font-size:16px;color:#6e6e73;margin-bottom:28px}
  .categories{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:28px}
  .cat-pill{padding:7px 16px;border-radius:20px;border:1px solid rgba(0,0,0,0.12);background:#fff;font-size:13px;cursor:pointer;color:#1d1d1f;transition:all 0.15s}
  .cat-pill:hover,.cat-pill.active{background:#0071e3;color:#fff;border-color:#0071e3}
  .deals-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:14px}
  .deal-card{background:#fff;border-radius:18px;overflow:hidden;border:1px solid rgba(0,0,0,0.06);transition:transform 0.2s,box-shadow 0.2s;cursor:pointer}
  .deal-card:hover{transform:translateY(-4px);box-shadow:0 12px 40px rgba(0,0,0,0.1)}
  .deal-img{width:100%;height:160px;background:#f5f5f7;display:flex;align-items:center;justify-content:center;font-size:44px;position:relative}
  .deal-badge{position:absolute;top:10px;left:10px;color:#fff;font-size:11px;font-weight:600;padding:3px 9px;border-radius:20px}
  .badge-sale{background:#ff3b30}
  .badge-aff{background:#34c759}
  .badge-hot{background:#ff9f0a}
  .shop-tag{position:absolute;top:10px;right:10px;background:rgba(0,0,0,0.5);color:#fff;font-size:10px;font-weight:600;padding:3px 8px;border-radius:10px}
  .deal-info{padding:14px}
  .deal-info h3{font-size:14px;font-weight:600;margin-bottom:3px;color:#1d1d1f;line-height:1.3}
  .deal-info .cat-tag{font-size:11px;color:#aeaeb2;margin-bottom:8px}
  .price-row{display:flex;align-items:baseline;gap:6px;margin-bottom:10px}
  .price-now{font-size:18px;font-weight:700}
  .price-old{font-size:12px;color:#aeaeb2;text-decoration:line-through}
  .price-save{font-size:11px;color:#34c759;font-weight:600}
  .deal-actions{display:flex;gap:6px}
  .btn-deal{flex:1;background:#0071e3;color:#fff;border:none;padding:9px;border-radius:10px;font-size:12px;font-weight:600;cursor:pointer;text-decoration:none;display:flex;align-items:center;justify-content:center;transition:background 0.15s}
  .btn-deal:hover{background:#005bbf}
  .btn-pin{background:#e60023;border:none;padding:9px 11px;border-radius:10px;cursor:pointer;color:#fff;font-size:12px;font-weight:600}
  .no-results{text-align:center;padding:60px;color:#6e6e73;font-size:16px;display:none}
  .stats{display:grid;grid-template-columns:repeat(auto-fit,minmax(160px,1fr));gap:12px;margin:0 24px 40px;max-width:1200px;margin-left:auto;margin-right:auto}
  .stat{background:#fff;border-radius:14px;padding:20px;text-align:center;border:1px solid rgba(0,0,0,0.06)}
  .stat .snum{font-size:28px;font-weight:700;color:#0071e3;margin-bottom:4px}
  .stat .slabel{font-size:13px;color:#6e6e73}
  footer{background:#f5f5f7;border-top:1px solid rgba(0,0,0,0.1);padding:40px 24px;text-align:center;color:#6e6e73;font-size:13px}
  .footer-links{margin-bottom:12px;display:flex;flex-wrap:wrap;justify-content:center}
  .footer-links a{color:#6e6e73;margin:0 10px;text-decoration:none}
  .footer-links a:hover{color:#0071e3}
  .footer-aff{font-size:12px;color:#aeaeb2;max-width:600px;margin:12px auto 0;line-height:1.6}
  @media(max-width:640px){.nav-links{display:none}.hero{padding:50px 16px 32px}.section{padding:32px 16px}}
</style>
</head>
<body>

<div class="aff-bar">
  Diese Seite enthält Affiliate-Links. Bei einem Kauf erhalte ich eine kleine Provision – für dich entstehen keine Mehrkosten. <a href="#footer-aff">Mehr erfahren</a>
</div>

<nav>
  <div class="nav-logo">DealFinder</div>
  <ul class="nav-links">
    <li><a href="#deals">Deals</a></li>
    <li><a href="#cats">Kategorien</a></li>
    <li><a href="https://pinterest.com" target="_blank">Pinterest</a></li>
    <li><a href="#footer-aff">Über uns</a></li>
  </ul>
</nav>

<div class="hero">
  <div class="hero-tag">Täglich aktualisierte Deals aus 6 Shops</div>
  <h1>Die besten Preise.<br>Einfach gefunden.</h1>
  <p>Amazon, Zalando, Otto, MediaMarkt, Douglas & About You – alle Deals an einem Ort.</p>
  <div class="search-bar">
    <input type="text" id="search-input" placeholder="Suche nach Produkten, Shops oder Kategorien …" oninput="doSearch()">
    <button onclick="doSearch()">Suchen</button>
  </div>
</div>

<div class="shop-logos">
  <div class="shop-pill active" onclick="filterShop('alle',this)">Alle Shops</div>
  <div class="shop-pill" onclick="filterShop('amazon',this)">Amazon</div>
  <div class="shop-pill" onclick="filterShop('zalando',this)">Zalando</div>
  <div class="shop-pill" onclick="filterShop('otto',this)">Otto</div>
  <div class="shop-pill" onclick="filterShop('mediamarkt',this)">MediaMarkt</div>
  <div class="shop-pill" onclick="filterShop('douglas',this)">Douglas</div>
  <div class="shop-pill" onclick="filterShop('aboutyou',this)">About You</div>
</div>

<div class="stats">
  <div class="stat"><div class="snum" id="stat-products">48</div><div class="slabel">Aktuelle Deals</div></div>
  <div class="stat"><div class="snum">6</div><div class="slabel">Partner-Shops</div></div>
  <div class="stat"><div class="snum">täglich</div><div class="slabel">Aktualisierung</div></div>
  <div class="stat"><div class="snum">0 €</div><div class="slabel">Mehrkosten für dich</div></div>
</div>

<div class="section" id="deals">
  <div class="section-label">Top Deals heute</div>
  <div class="section-title">Günstig. Geprüft. Sofort.</div>
  <p class="section-sub">Alle Deals direkt beim Händler kaufen – sicher & versandkostenfrei.</p>
  <div class="categories" id="cats">
    <div class="cat-pill active" onclick="filterCat('alle',this)">Alle</div>
    <div class="cat-pill" onclick="filterCat('elektronik',this)">Elektronik</div>
    <div class="cat-pill" onclick="filterCat('mode',this)">Mode</div>
    <div class="cat-pill" onclick="filterCat('haushalt',this)">Haushalt</div>
    <div class="cat-pill" onclick="filterCat('sport',this)">Sport</div>
    <div class="cat-pill" onclick="filterCat('beauty',this)">Beauty</div>
    <div class="cat-pill" onclick="filterCat('gaming',this)">Gaming</div>
    <div class="cat-pill" onclick="filterCat('outdoor',this)">Outdoor</div>
  </div>
  <div class="deals-grid" id="deals-grid"></div>
  <p class="no-results" id="no-results">Keine Produkte gefunden.</p>
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
    <strong>Affiliate-Hinweis:</strong> Diese Website enthält Affiliate-Links zu Amazon, Zalando, Otto, MediaMarkt, Douglas und About You. Wenn du über einen dieser Links einkaufst, erhalte ich eine kleine Provision – für dich entstehen keine zusätzlichen Kosten. Als Amazon-Partner verdiene ich an qualifizierten Käufen.
  </p>
</footer>

<script>
const T = '84690381578-21';
const A = (asin) => `https://www.amazon.de/dp/${asin}?tag=${T}`;
const AS = (q) => `https://www.amazon.de/s?k=${encodeURIComponent(q)}&tag=${T}`;
const Z = (path) => `https://www.zalando.de/${path}`;
const OT = (q) => `https://www.otto.de/suche/${encodeURIComponent(q)}/`;
const MM = (q) => `https://www.mediamarkt.de/de/search.html?query=${encodeURIComponent(q)}`;
const DG = (q) => `https://www.douglas.de/de/search?q=${encodeURIComponent(q)}`;
const AY = (q) => `https://www.aboutyou.de/search?term=${encodeURIComponent(q)}`;

const products = [
  // AMAZON – ELEKTRONIK
  {title:'Sony WH-1000XM5',shop:'amazon',shopLabel:'Amazon',priceNow:'279,00',priceOld:'349,00',save:'-70€',emoji:'🎧',badge:'-20%',badgeClass:'badge-sale',cat:'elektronik',url:A('B09XS7JWHH'),pin:'Sony WH-1000XM5 – Nur 279€!'},
  {title:'Apple AirPods Pro 2',shop:'amazon',shopLabel:'Amazon',priceNow:'199,00',priceOld:'279,00',save:'-80€',emoji:'🎵',badge:'-29%',badgeClass:'badge-sale',cat:'elektronik',url:A('B0BDHX8Z63'),pin:'Apple AirPods Pro 2 – Nur 199€!'},
  {title:'Samsung 4K Smart TV 55"',shop:'amazon',shopLabel:'Amazon',priceNow:'449,00',priceOld:'699,00',save:'-250€',emoji:'📺',badge:'-36%',badgeClass:'badge-sale',cat:'elektronik',url:AS('samsung 4k tv 55 zoll'),pin:'Samsung 4K TV 55" – 449€!'},
  {title:'iPad 10. Generation',shop:'amazon',shopLabel:'Amazon',priceNow:'379,00',priceOld:'449,00',save:'-70€',emoji:'📱',badge:'-16%',badgeClass:'badge-sale',cat:'elektronik',url:AS('apple ipad 10 generation'),pin:'Apple iPad 10. Gen – 379€!'},
  {title:'Kindle Paperwhite',shop:'amazon',shopLabel:'Amazon',priceNow:'109,99',priceOld:'149,99',save:'-40€',emoji:'📖',badge:'-27%',badgeClass:'badge-sale',cat:'elektronik',url:A('B08N36XNTT'),pin:'Kindle Paperwhite – Nur 109,99€!'},
  {title:'Echo Dot 5. Generation',shop:'amazon',shopLabel:'Amazon',priceNow:'29,99',priceOld:'54,99',save:'-25€',emoji:'🔊',badge:'-45%',badgeClass:'badge-hot',cat:'elektronik',url:AS('echo dot 5 generation'),pin:'Echo Dot 5 – Nur 29,99€!'},
  {title:'Fire TV Stick 4K',shop:'amazon',shopLabel:'Amazon',priceNow:'29,99',priceOld:'59,99',save:'-30€',emoji:'📡',badge:'-50%',badgeClass:'badge-hot',cat:'elektronik',url:AS('fire tv stick 4k'),pin:'Fire TV Stick 4K – Nur 29,99€!'},
  {title:'Logitech MX Master 3S',shop:'amazon',shopLabel:'Amazon',priceNow:'79,99',priceOld:'109,99',save:'-30€',emoji:'🖱️',badge:'-27%',badgeClass:'badge-sale',cat:'elektronik',url:AS('logitech mx master 3s'),pin:'Logitech MX Master 3S – 79,99€!'},

  // AMAZON – HAUSHALT
  {title:'Philips Kaffeemaschine 3200',shop:'amazon',shopLabel:'Amazon',priceNow:'299,00',priceOld:'449,00',save:'-150€',emoji:'☕',badge:'-33%',badgeClass:'badge-sale',cat:'haushalt',url:AS('philips kaffeemaschine 3200'),pin:'Philips Kaffeemaschine – 299€!'},
  {title:'Dyson V15 Detect Staubsauger',shop:'amazon',shopLabel:'Amazon',priceNow:'499,00',priceOld:'699,00',save:'-200€',emoji:'🌀',badge:'-29%',badgeClass:'badge-sale',cat:'haushalt',url:AS('dyson v15 detect'),pin:'Dyson V15 Detect – 499€!'},
  {title:'Instant Pot Duo 7-in-1',shop:'amazon',shopLabel:'Amazon',priceNow:'69,99',priceOld:'99,99',save:'-30€',emoji:'🍲',badge:'-30%',badgeClass:'badge-sale',cat:'haushalt',url:AS('instant pot duo 7in1'),pin:'Instant Pot Duo – Nur 69,99€!'},
  {title:'Bosch Stabmixer MSM6',shop:'amazon',shopLabel:'Amazon',priceNow:'39,99',priceOld:'64,99',save:'-25€',emoji:'🥤',badge:'-38%',badgeClass:'badge-sale',cat:'haushalt',url:AS('bosch stabmixer msm6'),pin:'Bosch Stabmixer – Nur 39,99€!'},

  // AMAZON – GAMING
  {title:'PlayStation 5 Controller DualSense',shop:'amazon',shopLabel:'Amazon',priceNow:'54,99',priceOld:'74,99',save:'-20€',emoji:'🎮',badge:'-27%',badgeClass:'badge-sale',cat:'gaming',url:AS('ps5 dualsense controller'),pin:'PS5 DualSense Controller – 54,99€!'},
  {title:'Nintendo Switch OLED',shop:'amazon',shopLabel:'Amazon',priceNow:'299,00',priceOld:'349,00',save:'-50€',emoji:'🕹️',badge:'-14%',badgeClass:'badge-sale',cat:'gaming',url:AS('nintendo switch oled'),pin:'Nintendo Switch OLED – 299€!'},
  {title:'SteelSeries Arctis Nova 3',shop:'amazon',shopLabel:'Amazon',priceNow:'49,99',priceOld:'79,99',save:'-30€',emoji:'🎧',badge:'-38%',badgeClass:'badge-hot',cat:'gaming',url:AS('steelseries arctis nova 3'),pin:'SteelSeries Arctis Nova 3 – 49,99€!'},

  // ZALANDO – MODE
  {title:'Nike Air Max 270',shop:'zalando',shopLabel:'Zalando',priceNow:'89,95',priceOld:'129,95',save:'-40€',emoji:'👟',badge:'Zalando',badgeClass:'badge-aff',cat:'mode',url:Z('nike-air-max-270.html'),pin:'Nike Air Max 270 – 89,95€ bei Zalando!'},
  {title:'Adidas Stan Smith',shop:'zalando',shopLabel:'Zalando',priceNow:'69,95',priceOld:'99,95',save:'-30€',emoji:'👟',badge:'Zalando',badgeClass:'badge-aff',cat:'mode',url:Z('adidas-stan-smith.html'),pin:'Adidas Stan Smith – 69,95€ bei Zalando!'},
  {title:"Levi's 501 Original Jeans",shop:'zalando',shopLabel:'Zalando',priceNow:'59,95',priceOld:'99,95',save:'-40€',emoji:'👖',badge:'Zalando',badgeClass:'badge-aff',cat:'mode',url:Z('levis-501.html'),pin:"Levi's 501 Jeans – 59,95€ bei Zalando!"},
  {title:'Tommy Hilfiger Poloshirt',shop:'zalando',shopLabel:'Zalando',priceNow:'44,95',priceOld:'69,95',save:'-25€',emoji:'👕',badge:'Zalando',badgeClass:'badge-aff',cat:'mode',url:Z('tommy-hilfiger-polo.html'),pin:'Tommy Hilfiger Polo – 44,95€!'},
  {title:'Nike Dri-FIT Trainingshose',shop:'zalando',shopLabel:'Zalando',priceNow:'34,95',priceOld:'54,95',save:'-20€',emoji:'👗',badge:'Zalando',badgeClass:'badge-aff',cat:'sport',url:Z('nike-dri-fit-hose.html'),pin:'Nike Dri-FIT Hose – 34,95€!'},
  {title:'Under Armour Sportjacke',shop:'zalando',shopLabel:'Zalando',priceNow:'54,95',priceOld:'84,95',save:'-30€',emoji:'🧥',badge:'Zalando',badgeClass:'badge-aff',cat:'sport',url:Z('under-armour-jacke.html'),pin:'Under Armour Jacke – 54,95€!'},

  // OTTO – HAUSHALT & ELEKTRONIK
  {title:'Miele Waschmaschine WCA 030',shop:'otto',shopLabel:'Otto',priceNow:'499,00',priceOld:'699,00',save:'-200€',emoji:'🫧',badge:'-29%',badgeClass:'badge-sale',cat:'haushalt',url:OT('miele waschmaschine wca030'),pin:'Miele Waschmaschine – 499€ bei Otto!'},
  {title:'LG OLED TV 55" C3',shop:'otto',shopLabel:'Otto',priceNow:'899,00',priceOld:'1299,00',save:'-400€',emoji:'📺',badge:'-31%',badgeClass:'badge-hot',cat:'elektronik',url:OT('lg oled tv 55 c3'),pin:'LG OLED TV 55" – 899€ bei Otto!'},
  {title:'Bosch Geschirrspüler SMS4',shop:'otto',shopLabel:'Otto',priceNow:'399,00',priceOld:'549,00',save:'-150€',emoji:'🍽️',badge:'-27%',badgeClass:'badge-sale',cat:'haushalt',url:OT('bosch geschirrspüler sms4'),pin:'Bosch Geschirrspüler – 399€!'},
  {title:'Ikea KALLAX Regal',shop:'otto',shopLabel:'Otto',priceNow:'69,99',priceOld:'99,99',save:'-30€',emoji:'🪑',badge:'-30%',badgeClass:'badge-sale',cat:'haushalt',url:OT('kallax regal'),pin:'KALLAX Regal – Nur 69,99€ bei Otto!'},

  // MEDIAMARKT – ELEKTRONIK
  {title:'Samsung Galaxy S24',shop:'mediamarkt',shopLabel:'MediaMarkt',priceNow:'699,00',priceOld:'899,00',save:'-200€',emoji:'📱',badge:'-22%',badgeClass:'badge-sale',cat:'elektronik',url:MM('samsung galaxy s24'),pin:'Samsung Galaxy S24 – 699€ bei MediaMarkt!'},
  {title:'Sony PlayStation 5 Slim',shop:'mediamarkt',shopLabel:'MediaMarkt',priceNow:'449,00',priceOld:'499,99',save:'-51€',emoji:'🎮',badge:'-10%',badgeClass:'badge-sale',cat:'gaming',url:MM('playstation 5 slim'),pin:'PS5 Slim – 449€ bei MediaMarkt!'},
  {title:'Bose SoundLink Flex',shop:'mediamarkt',shopLabel:'MediaMarkt',priceNow:'99,00',priceOld:'149,00',save:'-50€',emoji:'🔊',badge:'-34%',badgeClass:'badge-hot',cat:'elektronik',url:MM('bose soundlink flex'),pin:'Bose SoundLink Flex – 99€!'},
  {title:'Apple MacBook Air M2',shop:'mediamarkt',shopLabel:'MediaMarkt',priceNow:'999,00',priceOld:'1299,00',save:'-300€',emoji:'💻',badge:'-23%',badgeClass:'badge-hot',cat:'elektronik',url:MM('apple macbook air m2'),pin:'MacBook Air M2 – 999€ bei MediaMarkt!'},
  {title:'GoPro Hero 12 Black',shop:'mediamarkt',shopLabel:'MediaMarkt',priceNow:'299,00',priceOld:'399,00',save:'-100€',emoji:'📷',badge:'-25%',badgeClass:'badge-sale',cat:'outdoor',url:MM('gopro hero 12 black'),pin:'GoPro Hero 12 – 299€!'},

  // DOUGLAS – BEAUTY
  {title:'Charlotte Tilbury Pillow Talk Lippenstift',shop:'douglas',shopLabel:'Douglas',priceNow:'28,00',priceOld:'36,00',save:'-8€',emoji:'💄',badge:'-22%',badgeClass:'badge-sale',cat:'beauty',url:DG('charlotte tilbury pillow talk'),pin:'Charlotte Tilbury Lipstick – 28€!'},
  {title:'Dyson Airwrap Complete',shop:'douglas',shopLabel:'Douglas',priceNow:'449,00',priceOld:'549,00',save:'-100€',emoji:'💇',badge:'-18%',badgeClass:'badge-hot',cat:'beauty',url:DG('dyson airwrap complete'),pin:'Dyson Airwrap – 449€ bei Douglas!'},
  {title:'La Mer Feuchtigkeitscreme',shop:'douglas',shopLabel:'Douglas',priceNow:'189,00',priceOld:'239,00',save:'-50€',emoji:'🧴',badge:'-21%',badgeClass:'badge-sale',cat:'beauty',url:DG('la mer feuchtigkeitscreme'),pin:'La Mer Creme – 189€ bei Douglas!'},
  {title:'Chanel No. 5 EdP 100ml',shop:'douglas',shopLabel:'Douglas',priceNow:'129,00',priceOld:'159,00',save:'-30€',emoji:'🌸',badge:'-19%',badgeClass:'badge-sale',cat:'beauty',url:DG('chanel no 5 parfum'),pin:'Chanel No. 5 – 129€ bei Douglas!'},
  {title:'Oral-B iO Series 8',shop:'douglas',shopLabel:'Douglas',priceNow:'79,99',priceOld:'149,99',save:'-70€',emoji:'🪥',badge:'-47%',badgeClass:'badge-hot',cat:'beauty',url:DG('oral b io series 8'),pin:'Oral-B iO Series 8 – 79,99€!'},

  // ABOUT YOU – MODE
  {title:'Puma Classics T-Shirt',shop:'aboutyou',shopLabel:'About You',priceNow:'19,99',priceOld:'29,99',save:'-10€',emoji:'👕',badge:'-33%',badgeClass:'badge-sale',cat:'mode',url:AY('puma classics t-shirt'),pin:'Puma T-Shirt – Nur 19,99€!'},
  {title:'New Balance 574 Sneaker',shop:'aboutyou',shopLabel:'About You',priceNow:'74,95',priceOld:'99,95',save:'-25€',emoji:'👟',badge:'About You',badgeClass:'badge-aff',cat:'mode',url:AY('new balance 574'),pin:'New Balance 574 – 74,95€!'},
  {title:'Calvin Klein Jeans Skinny',shop:'aboutyou',shopLabel:'About You',priceNow:'49,95',priceOld:'79,95',save:'-30€',emoji:'👖',badge:'-38%',badgeClass:'badge-sale',cat:'mode',url:AY('calvin klein jeans skinny'),pin:'Calvin Klein Jeans – 49,95€!'},
  {title:'Adidas Ultraboost 22',shop:'aboutyou',shopLabel:'About You',priceNow:'99,95',priceOld:'179,95',save:'-80€',emoji:'🏃',badge:'-44%',badgeClass:'badge-hot',cat:'sport',url:AY('adidas ultraboost 22'),pin:'Adidas Ultraboost 22 – 99,95€!'},
  {title:'The North Face Fleecejacke',shop:'aboutyou',shopLabel:'About You',priceNow:'69,95',priceOld:'119,95',save:'-50€',emoji:'🧥',badge:'-42%',badgeClass:'badge-hot',cat:'outdoor',url:AY('north face fleece jacke'),pin:'North Face Fleece – 69,95€!'},
  {title:'Columbia Regenjacke',shop:'aboutyou',shopLabel:'About You',priceNow:'79,95',priceOld:'129,95',save:'-50€',emoji:'🌧️',badge:'-38%',badgeClass:'badge-sale',cat:'outdoor',url:AY('columbia regenjacke'),pin:'Columbia Regenjacke – 79,95€!'},
];

let activeCat = 'alle', activeShop = 'alle', searchQ = '';

function render() {
  const grid = document.getElementById('deals-grid');
  const none = document.getElementById('no-results');
  let list = products.filter(p => {
    const matchCat  = activeCat  === 'alle' || p.cat  === activeCat;
    const matchShop = activeShop === 'alle' || p.shop === activeShop;
    const matchQ    = !searchQ   || p.title.toLowerCase().includes(searchQ) || p.shopLabel.toLowerCase().includes(searchQ) || p.cat.includes(searchQ);
    return matchCat && matchShop && matchQ;
  });
  document.getElementById('stat-products').textContent = list.length;
  if (!list.length) { grid.innerHTML=''; none.style.display='block'; return; }
  none.style.display = 'none';
  grid.innerHTML = list.map(p => `
    <div class="deal-card">
      <div class="deal-img">${p.emoji}
        <span class="deal-badge ${p.badgeClass}">${p.badge}</span>
        <span class="shop-tag">${p.shopLabel}</span>
      </div>
      <div class="deal-info">
        <h3>${p.title}</h3>
        <div class="cat-tag">${p.cat.charAt(0).toUpperCase()+p.cat.slice(1)}</div>
        <div class="price-row">
          <span class="price-now">${p.priceNow} €</span>
          <span class="price-old">${p.priceOld} €</span>
          <span class="price-save">${p.save}</span>
        </div>
        <div class="deal-actions">
          <a class="btn-deal" href="${p.url}" target="_blank" rel="noopener sponsored">Zum Deal ↗</a>
          <button class="btn-pin" onclick="pin('${p.pin.replace(/'/g,"\\'")}','${p.url}')">❤ Pin</button>
        </div>
      </div>
    </div>`).join('');
}

function filterCat(cat, el) {
  activeCat = cat;
  document.querySelectorAll('.cat-pill').forEach(p=>p.classList.remove('active'));
  el.classList.add('active');
  render();
}

function filterShop(shop, el) {
  activeShop = shop;
  document.querySelectorAll('.shop-pill').forEach(p=>p.classList.remove('active'));
  el.classList.add('active');
  render();
}

function doSearch() {
  searchQ = document.getElementById('search-input').value.toLowerCase().trim();
  render();
}

function pin(desc, url) {
  const p = new URLSearchParams({url, description: desc});
  const w = window.open('https://pinterest.com/pin/create/button/?'+p,'pinterest','width=750,height=550');
  if (!w) window.location.href = 'https://pinterest.com/pin/create/button/?'+p;
}

render();
</script>
</body>
</html>
