!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DealFinder</title>
<style>
  *{margin:0;padding:0;box-sizing:border-box}
  body{font-family:-apple-system,BlinkMacSystemFont,'SF Pro Display','Segoe UI',sans-serif;background:#f5f5f7;color:#1d1d1f;min-height:100vh}
  nav{background:rgba(245,245,247,0.85);backdrop-filter:blur(20px);-webkit-backdrop-filter:blur(20px);border-bottom:1px solid rgba(0,0,0,0.08);padding:0 24px;height:52px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:100}
  .nav-logo{font-size:18px;font-weight:600;letter-spacing:-0.3px;color:#1d1d1f}
  .nav-links{display:flex;gap:24px;list-style:none}
  .nav-links a{font-size:13px;color:#1d1d1f;text-decoration:none;opacity:0.8}
  .nav-links a:hover{opacity:1}
  .nav-cta{background:#0071e3;color:#fff;border:none;padding:7px 16px;border-radius:20px;font-size:13px;cursor:pointer;font-weight:500}
  .hero{text-align:center;padding:80px 24px 60px;background:linear-gradient(180deg,#fff 0%,#f5f5f7 100%)}
  .hero-tag{font-size:13px;color:#0071e3;font-weight:500;letter-spacing:0.3px;margin-bottom:16px}
  .hero h1{font-size:clamp(36px,6vw,64px);font-weight:700;letter-spacing:-1.5px;line-height:1.07;color:#1d1d1f;max-width:800px;margin:0 auto 20px}
  .hero p{font-size:19px;color:#6e6e73;max-width:500px;margin:0 auto 36px;line-height:1.5}
  .hero-btns{display:flex;gap:12px;justify-content:center;flex-wrap:wrap}
  .btn-primary{background:#0071e3;color:#fff;border:none;padding:14px 28px;border-radius:980px;font-size:15px;cursor:pointer;font-weight:500;text-decoration:none;display:inline-block}
  .btn-secondary{background:transparent;color:#0071e3;border:1.5px solid #0071e3;padding:14px 28px;border-radius:980px;font-size:15px;cursor:pointer;font-weight:500;text-decoration:none;display:inline-block}
  .search-bar{max-width:640px;margin:48px auto 0;background:#fff;border-radius:16px;padding:6px 6px 6px 20px;display:flex;align-items:center;gap:8px;box-shadow:0 2px 20px rgba(0,0,0,0.08);border:1px solid rgba(0,0,0,0.06)}
  .search-bar input{flex:1;border:none;outline:none;font-size:16px;color:#1d1d1f;background:transparent}
  .search-bar input::placeholder{color:#aeaeb2}
  .search-bar button{background:#0071e3;color:#fff;border:none;padding:10px 20px;border-radius:12px;font-size:15px;cursor:pointer;font-weight:500;white-space:nowrap}
  .section{padding:60px 24px;max-width:1100px;margin:0 auto}
  .section-label{font-size:12px;font-weight:600;letter-spacing:0.5px;color:#0071e3;text-transform:uppercase;margin-bottom:8px}
  .section-title{font-size:clamp(24px,4vw,40px);font-weight:700;letter-spacing:-0.5px;margin-bottom:8px;color:#1d1d1f}
  .section-sub{font-size:17px;color:#6e6e73;margin-bottom:40px}
  .deals-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(240px,1fr));gap:16px}
  .deal-card{background:#fff;border-radius:18px;overflow:hidden;border:1px solid rgba(0,0,0,0.06);transition:transform 0.2s,box-shadow 0.2s;cursor:pointer}
  .deal-card:hover{transform:translateY(-4px);box-shadow:0 12px 40px rgba(0,0,0,0.12)}
  .deal-img{width:100%;height:180px;background:#f5f5f7;display:flex;align-items:center;justify-content:center;font-size:48px;position:relative}
  .deal-badge{position:absolute;top:12px;left:12px;background:#ff3b30;color:#fff;font-size:11px;font-weight:600;padding:4px 10px;border-radius:20px}
  .deal-badge.affiliate{background:#34c759}
  .deal-info{padding:16px}
  .deal-info h3{font-size:15px;font-weight:600;margin-bottom:6px;color:#1d1d1f}
  .deal-info .shop{font-size:12px;color:#6e6e73;margin-bottom:10px}
  .price-row{display:flex;align-items:baseline;gap:8px;margin-bottom:12px}
  .price-now{font-size:20px;font-weight:700;color:#1d1d1f}
  .price-old{font-size:13px;color:#aeaeb2;text-decoration:line-through}
  .price-save{font-size:12px;color:#34c759;font-weight:600}
  .deal-actions{display:flex;gap:8px}
  .btn-buy{flex:1;background:#0071e3;color:#fff;border:none;padding:9px;border-radius:10px;font-size:13px;font-weight:500;cursor:pointer}
  .btn-pin{background:#e60023;border:none;padding:9px 12px;border-radius:10px;cursor:pointer;font-size:14px;color:#fff;font-weight:600;display:flex;align-items:center;gap:5px}
  .btn-pin:hover{background:#c0001d}
  .categories{display:flex;gap:10px;flex-wrap:wrap;margin-bottom:36px}
  .cat-pill{padding:8px 18px;border-radius:20px;border:1px solid rgba(0,0,0,0.12);background:#fff;font-size:14px;cursor:pointer;color:#1d1d1f;transition:all 0.15s}
  .cat-pill:hover,.cat-pill.active{background:#0071e3;color:#fff;border-color:#0071e3}
  .features{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:16px;margin-top:20px}
  .feat-card{background:#fff;border-radius:18px;padding:28px 24px;border:1px solid rgba(0,0,0,0.06)}
  .feat-icon{font-size:28px;margin-bottom:14px}
  .feat-card h3{font-size:16px;font-weight:600;margin-bottom:8px;color:#1d1d1f}
  .feat-card p{font-size:14px;color:#6e6e73;line-height:1.5}
  .paypal-section{background:#fff;border-radius:24px;padding:48px 40px;text-align:center;border:1px solid rgba(0,0,0,0.06);margin-top:60px}
  .paypal-section h2{font-size:clamp(20px,3vw,32px);font-weight:700;letter-spacing:-0.5px;margin-bottom:12px}
  .paypal-section p{font-size:16px;color:#6e6e73;margin-bottom:28px}
  .paypal-logos{display:flex;gap:16px;justify-content:center;flex-wrap:wrap}
  .pay-badge{background:#f5f5f7;border-radius:12px;padding:12px 20px;font-size:14px;font-weight:600;color:#1d1d1f;border:1px solid rgba(0,0,0,0.08)}
  .pay-badge.paypal{color:#003087}
  .dsgvo{background:#f5f5f7;border-radius:24px;padding:40px;margin-top:40px;display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:20px}
  .dsgvo-item{display:flex;gap:12px;align-items:flex-start}
  .dsgvo-icon{width:36px;height:36px;border-radius:10px;background:#0071e3;display:flex;align-items:center;justify-content:center;flex-shrink:0;color:#fff;font-size:16px}
  .dsgvo-item h4{font-size:14px;font-weight:600;margin-bottom:4px}
  .dsgvo-item p{font-size:13px;color:#6e6e73}
  footer{background:#f5f5f7;border-top:1px solid rgba(0,0,0,0.1);padding:40px 24px;text-align:center;color:#6e6e73;font-size:13px}
  footer a{color:#6e6e73;margin:0 12px;text-decoration:none}
  footer a:hover{color:#0071e3}
  .footer-links{margin-bottom:16px;display:flex;flex-wrap:wrap;justify-content:center;gap:4px}
  @media(max-width:640px){.nav-links{display:none}.hero{padding:60px 16px 40px}.section{padding:40px 16px}}
</style>
<script src="https://www.paypal.com/sdk/js?client-id=AXBBFldGnRH-FNDI5ndIjZ6urrEtmTSp1lrhvtipVsP_ofjFH14vdDqkgS-XipPfMLA5YZnhqi5S7hlk&currency=EUR&locale=de_DE"></script>
</head>
<body>

<nav>
  <div class="nav-logo">DealFinder</div>
  <ul class="nav-links">
    <li><a href="#">Deals</a></li>
    <li><a href="#">Kategorien</a></li>
    <li><a href="#">Pinterest</a></li>
    <li><a href="#">Über uns</a></li>
  </ul>
  <button class="nav-cta">Konto erstellen</button>
</nav>

<div class="hero">
  <div class="hero-tag">Täglich aktualisierte Deals</div>
  <h1>Die besten Preise.<br>Einfach gefunden.</h1>
  <p>Günstigste Artikel aus dem Netz – kuratiert, verglichen und direkt kaufbar.</p>
  <div class="hero-btns">
    <a href="#deals" class="btn-primary">Jetzt Deals entdecken</a>
    <a href="#zahlung" class="btn-secondary">Zahlungsoptionen</a>
  </div>
  <div class="search-bar">
    <input type="text" placeholder="Artikel suchen – z. B. iPhone Hülle, Sneaker, Kaffeemaschine …">
    <button>Suchen</button>
  </div>
</div>

<div class="section" id="deals">
  <div class="section-label">Top Deals heute</div>
  <div class="section-title">Günstig. Geprüft. Sofort.</div>
  <p class="section-sub">Eigene Produkte &amp; die besten Affiliate-Angebote im Überblick.</p>

  <div class="categories">
    <div class="cat-pill active">Alle</div>
    <div class="cat-pill">Elektronik</div>
    <div class="cat-pill">Mode</div>
    <div class="cat-pill">Haushalt</div>
    <div class="cat-pill">Sport</div>
    <div class="cat-pill">Beauty</div>
    <div class="cat-pill">Reisen</div>
  </div>

  <div class="deals-grid">
    <div class="deal-card">
      <div class="deal-img">🎧<span class="deal-badge">-42%</span></div>
      <div class="deal-info">
        <h3>Wireless Kopfhörer Pro</h3>
        <div class="shop">Eigener Shop</div>
        <div class="price-row"><span class="price-now">29,99 €</span><span class="price-old">51,99 €</span><span class="price-save">-22 €</span></div>
        <div class="deal-actions">
          <div id="paypal-btn-1" style="width:100%"></div>
          <button class="btn-pin" title="Auf Pinterest teilen">📌</button>
        </div>
      </div>
    </div>
    <div class="deal-card">
      <div class="deal-img">👟<span class="deal-badge affiliate">Affiliate</span></div>
      <div class="deal-info">
        <h3>Lauf-Sneaker Ultraboost</h3>
        <div class="shop">via Zalando</div>
        <div class="price-row"><span class="price-now">59,95 €</span><span class="price-old">89,95 €</span><span class="price-save">-30 €</span></div>
        <div class="deal-actions">
          <button class="btn-buy">Zum Deal ↗</button>
          <button class="btn-pin" title="Auf Pinterest teilen">📌</button>
        </div>
      </div>
    </div>
    <div class="deal-card">
      <div class="deal-img">☕<span class="deal-badge">-35%</span></div>
      <div class="deal-info">
        <h3>Kaffeemaschine Vollautom.</h3>
        <div class="shop">Eigener Shop</div>
        <div class="price-row"><span class="price-now">189,00 €</span><span class="price-old">289,00 €</span><span class="price-save">-100 €</span></div>
        <div class="deal-actions">
          <button class="btn-buy">Kaufen</button>
          <button class="btn-pin" title="Auf Pinterest teilen">📌</button>
        </div>
      </div>
    </div>
    <div class="deal-card">
      <div class="deal-img">📱<span class="deal-badge affiliate">Affiliate</span></div>
      <div class="deal-info">
        <h3>Smartphone Hülle MagSafe</h3>
        <div class="shop">via Amazon</div>
        <div class="price-row"><span class="price-now">9,99 €</span><span class="price-old">19,99 €</span><span class="price-save">-10 €</span></div>
        <div class="deal-actions">
          <button class="btn-buy">Zum Deal ↗</button>
          <button class="btn-pin" title="Auf Pinterest teilen">📌</button>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="section">
  <div class="section-label">Warum DealFinder?</div>
  <div class="section-title">Alles an einem Ort.</div>
  <div class="features">
    <div class="feat-card">
      <div class="feat-icon">🔍</div>
      <h3>Automatische Preissuche</h3>
      <p>Wir durchsuchen täglich tausende Shops und zeigen dir nur die echten Tiefstpreise.</p>
    </div>
    <div class="feat-card">
      <div class="feat-icon">📌</div>
      <h3>Pinterest Integration</h3>
      <p>Jeden Deal direkt auf deinen Pinterest-Board pinnen – teilen mit einem Klick.</p>
    </div>
    <div class="feat-card">
      <div class="feat-icon">🛒</div>
      <h3>Eigener Shop & Affiliate</h3>
      <p>Kaufe direkt bei uns oder werde zu den besten Händlern weitergeleitet.</p>
    </div>
    <div class="feat-card">
      <div class="feat-icon">🔒</div>
      <h3>Sicher & DSGVO-konform</h3>
      <p>Deine Daten sind sicher. Alle Zahlungen SSL-verschlüsselt, konform nach EU-Recht.</p>
    </div>
  </div>
</div>

<div class="section" id="zahlung">
  <div class="paypal-section">
    <div class="section-label" style="margin-bottom:16px">Bezahlung</div>
    <h2>Sicher bezahlen – so wie du es magst.</h2>
    <p>Alle gängigen Zahlungsmethoden. Schnell, sicher, DSGVO-konform.</p>
    <div class="paypal-logos">
      <div class="pay-badge paypal">💙 PayPal</div>
      <div class="pay-badge">💳 Kreditkarte</div>
      <div class="pay-badge">📱 Apple Pay</div>
      <div class="pay-badge">G Google Pay</div>
      <div class="pay-badge">🏦 Klarna</div>
    </div>
  </div>

  <div class="dsgvo">
    <div class="dsgvo-item">
      <div class="dsgvo-icon">🔒</div>
      <div><h4>SSL-Verschlüsselung</h4><p>Alle Zahlungsdaten werden 256-Bit verschlüsselt übertragen.</p></div>
    </div>
    <div class="dsgvo-item">
      <div class="dsgvo-icon">📋</div>
      <div><h4>DSGVO-konform</h4><p>Datenschutz nach EU-Recht. Keine Weitergabe an Dritte.</p></div>
    </div>
    <div class="dsgvo-item">
      <div class="dsgvo-icon">↩️</div>
      <div><h4>14 Tage Rückgabe</h4><p>Gesetzliches Widerrufsrecht – problemlose Rückabwicklung.</p></div>
    </div>
    <div class="dsgvo-item">
      <div class="dsgvo-icon">🧾</div>
      <div><h4>Automatische Rechnung</h4><p>Nach jedem Kauf erhältst du eine steuerliche Rechnung per E-Mail.</p></div>
    </div>
  </div>
</div>

<footer>
  <div class="footer-links">
    <a href="#">Impressum</a>
    <a href="#">Datenschutz</a>
    <a href="#">AGB</a>
    <a href="#">Widerrufsrecht</a>
    <a href="#">Zahlungsoptionen</a>
    <a href="#">Kontakt</a>
    <a href="#">Pinterest</a>
  </div>
  <p>© 2026 DealFinder · Alle Preise inkl. MwSt. · Affiliate-Links gekennzeichnet</p>
</footer>

<script>
// ─── Amazon Affiliate-Links ───────────────────────────────
function openAffiliate(url) {
  window.open(url, '_blank', 'noopener');
}

// ─── Produkt-Detail Dummy ─────────────────────────────────
function openProduct(name, price) {
  alert('Produkt: ' + name + '\nPreis: ' + price + '\n\nHier kommt später deine Produktseite!');
}

// ─── Pinterest Share-Funktion ─────────────────────────────
function pinProduct(description, imageUrl, pageUrl) {
  const base   = 'https://pinterest.com/pin/create/button/';
  const fullUrl = location.href.split('?')[0];
  const params = new URLSearchParams({
    url:         fullUrl,
    media:       imageUrl || fullUrl,
    description: description
  });
  const pinterestUrl = base + '?' + params.toString();
  const win = window.open(pinterestUrl, 'pinterest', 'width=750,height=550,noopener');
  if (!win) {
    window.location.href = pinterestUrl;
  }
}

// ─── Supabase Konfiguration ───────────────────────────────
const SUPABASE_URL    = 'https://DEIN-PROJEKT.supabase.co';
const SUPABASE_ANON   = 'DEIN_SUPABASE_ANON_KEY';

async function saveOrder(details, productTitle, amount) {
  try {
    const res = await fetch(SUPABASE_URL + '/rest/v1/orders', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'apikey':       SUPABASE_ANON,
        'Authorization':'Bearer ' + SUPABASE_ANON,
        'Prefer':       'return=representation'
      },
      body: JSON.stringify({
        paypal_order_id: details.id,
        vorname:         details.payer.name.given_name,
        nachname:        details.payer.name.surname,
        email:           details.payer.email_address,
        produkt:         productTitle,
        betrag:          parseFloat(amount),
        status:          'bezahlt',
        erstellt_am:     new Date().toISOString()
      })
    });
    if (res.ok) console.log('Bestellung gespeichert ✓');
    else console.error('Supabase Fehler:', await res.text());
  } catch(e) {
    console.error('Verbindungsfehler:', e);
  }
}

// ─── PayPal Button Renderer ───────────────────────────────
function renderPayPalBtn(containerId, price, title) {
  paypal.Buttons({
    createOrder: (data, actions) => actions.order.create({
      purchase_units: [{ amount: { value: price, currency_code: 'EUR' }, description: title }]
    }),
    onApprove: (data, actions) => actions.order.capture().then(async details => {
      await saveOrder(details, title, price);
      alert('Danke, ' + details.payer.name.given_name + '! Deine Bestellung wurde gespeichert.');
    }),
    onError: err => alert('Zahlung fehlgeschlagen. Bitte erneut versuchen.'),
    style: { layout: 'horizontal', color: 'blue', shape: 'rect', label: 'pay', height: 35 }
  }).render('#' + containerId);
}
renderPayPalBtn('paypal-btn-1', '29.99', 'Wireless Kopfhörer Pro');
renderPayPalBtn('paypal-btn-2', '189.00', 'Kaffeemaschine Vollautomat');
</script>
</body>
</html>
