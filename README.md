<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Lueur Studio — objets pour la maison</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=DM+Sans:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --paper:#EFEBE3;
    --ink:#1D1B18;
    --ink-soft:#625C50;
    --line:#D9D2C2;
    --surface:#E3DDCE;
    --slate:#35424E;
    --slate-deep:#232C34;
    --brass:#B08D57;
    --bg:var(--paper); --fg:var(--ink); --fg-soft:var(--ink-soft);
    --border:var(--line); --panel:var(--surface);
    --accent:var(--slate); --accent-deep:var(--slate-deep); --accent-2:var(--brass);
  }
  @media (prefers-color-scheme: dark){
    :root:not([data-theme="light"]){
      --bg:#181613; --fg:#EFEBE3; --fg-soft:#B9B2A2;
      --border:#3A362E; --panel:#232019;
      --accent:#8FA6B8; --accent-deep:#C7D6E0; --accent-2:#C9A66E;
    }
  }
  :root[data-theme="dark"]{
    --bg:#181613; --fg:#EFEBE3; --fg-soft:#B9B2A2;
    --border:#3A362E; --panel:#232019;
    --accent:#8FA6B8; --accent-deep:#C7D6E0; --accent-2:#C9A66E;
  }
  *{box-sizing:border-box;}
  html,body{margin:0;padding:0;}
  body{background:var(--bg); color:var(--fg); font-family:'DM Sans',sans-serif; min-height:100vh; -webkit-font-smoothing:antialiased;}
  a{color:inherit;}
  .wrap{max-width:1080px; margin:0 auto; padding:0 24px;}

  header.top{position:sticky; top:0; z-index:30; background:var(--bg); border-bottom:1px solid var(--border);}
  .top-inner{display:flex; align-items:center; justify-content:space-between; padding:20px 24px; max-width:1080px; margin:0 auto; gap:16px;}
  .brand{display:flex; align-items:center; gap:11px;}
  .brand-mark{width:26px;height:26px;flex:none;}
  .brand-name{font-family:'DM Serif Display', serif; font-size:22px;}
  nav.top-nav{display:flex; gap:28px; font-size:14px;}
  nav.top-nav a{text-decoration:none; color:var(--fg-soft); border-bottom:1px solid transparent; padding-bottom:2px;}
  nav.top-nav a:hover{color:var(--fg); border-color:var(--accent-2);}
  .cart-btn{display:flex; align-items:center; gap:8px; background:none; border:1px solid var(--border); color:var(--fg); padding:9px 14px; cursor:pointer; font-family:inherit; font-size:14px;}
  .cart-btn:hover{border-color:var(--accent-2);}
  .cart-count{background:var(--accent-deep); color:var(--bg); border-radius:50%; width:19px; height:19px; display:inline-flex; align-items:center; justify-content:center; font-size:11px; font-weight:600;}

  .hero{padding:76px 24px 56px; display:grid; grid-template-columns:1.1fr 0.9fr; gap:50px; align-items:end; max-width:1080px; margin:0 auto;}
  .hero-eyebrow{font-size:13px; color:var(--accent-2); margin-bottom:16px;}
  .hero h1{font-family:'DM Serif Display', serif; font-size:clamp(32px,4.6vw,50px); line-height:1.12; margin:0 0 20px; max-width:15ch;}
  .hero p{font-size:16px; line-height:1.65; color:var(--fg-soft); max-width:48ch; margin:0;}
  .hero-side{border-left:1px solid var(--border); padding-left:28px;}
  .hero-side p{font-size:14px; line-height:1.7; color:var(--fg-soft); margin:0 0 14px;}
  .hero-side b{display:block; font-family:'DM Serif Display',serif; font-size:15px; color:var(--fg); margin-bottom:4px;}

  .section-head{display:flex; justify-content:space-between; align-items:baseline; margin:0 auto 30px; padding:0 24px 16px; border-bottom:1px solid var(--border); max-width:1080px;}
  .section-head h2{font-family:'DM Serif Display', serif; font-size:26px; margin:0;}
  .section-head span{font-size:13px; color:var(--fg-soft);}

  .catalog{max-width:1080px; margin:0 auto 70px; padding:0 24px; display:grid; grid-template-columns:repeat(2,1fr); gap:1px; background:var(--border); border:1px solid var(--border);}
  .item{background:var(--bg); padding:26px 26px 24px; display:flex; flex-direction:column; gap:14px;}
  .item-top{display:flex; justify-content:space-between; align-items:flex-start;}
  .item-num{font-size:12px; color:var(--fg-soft); letter-spacing:0.02em;}
  .item-art{width:100%; aspect-ratio:4/3; background:var(--panel); display:flex; align-items:center; justify-content:center;}
  .item-art svg{width:44%; height:44%;}
  .item-name{font-family:'DM Serif Display', serif; font-size:19px; margin:0;}
  .item-desc{font-size:13.5px; color:var(--fg-soft); line-height:1.55; margin:0; max-width:42ch;}
  .item-foot{display:flex; justify-content:space-between; align-items:center; margin-top:auto; padding-top:6px;}
  .item-price{font-family:'DM Serif Display', serif; font-size:18px;}
  .add-btn{background:var(--fg); color:var(--bg); border:none; padding:9px 15px; font-family:inherit; font-size:13px; cursor:pointer;}
  .add-btn:hover{background:var(--accent-2); color:var(--ink);}
  .add-btn.added{background:var(--accent);}

  .promise{background:var(--panel); border-top:1px solid var(--border); border-bottom:1px solid var(--border);}
  .promise-inner{max-width:1080px; margin:0 auto; padding:52px 24px; display:grid; grid-template-columns:repeat(3,1fr); gap:36px;}
  .promise-item b{display:block; font-family:'DM Serif Display', serif; font-size:17px; margin-bottom:8px;}
  .promise-item p{font-size:13.5px; color:var(--fg-soft); line-height:1.6; margin:0;}

  footer{padding:44px 24px 64px; text-align:center; font-size:13px; color:var(--fg-soft);}

  .overlay{position:fixed; inset:0; background:rgba(15,13,10,.45); opacity:0; pointer-events:none; transition:opacity .25s ease; z-index:40;}
  .overlay.open{opacity:1; pointer-events:auto;}
  .drawer{position:fixed; top:0; right:0; height:100%; width:min(400px,92vw); background:var(--bg); border-left:1px solid var(--border); transform:translateX(100%); transition:transform .3s ease; z-index:50; display:flex; flex-direction:column;}
  .drawer.open{transform:translateX(0);}
  .drawer-head{display:flex; justify-content:space-between; align-items:center; padding:20px 22px; border-bottom:1px solid var(--border);}
  .drawer-head h3{font-family:'DM Serif Display', serif; font-size:19px; margin:0;}
  .drawer-close{background:none;border:none;font-size:22px;color:var(--fg-soft);cursor:pointer; line-height:1;}
  .drawer-items{flex:1; overflow-y:auto; padding:14px 22px;}
  .drawer-empty{color:var(--fg-soft); font-size:14px; padding:30px 0; text-align:center;}
  .cart-item{display:flex; gap:12px; padding:14px 0; border-bottom:1px solid var(--border); align-items:center;}
  .cart-item-art{width:46px;height:46px;background:var(--panel);flex:none;display:flex;align-items:center;justify-content:center;}
  .cart-item-art svg{width:26px;height:26px;}
  .cart-item-info{flex:1; min-width:0;}
  .cart-item-info b{display:block; font-size:14px; font-weight:500;}
  .cart-item-info span{font-size:12.5px; color:var(--fg-soft);}
  .qty-row{display:flex; align-items:center; gap:8px; margin-top:6px;}
  .qty-btn{width:22px;height:22px;border:1px solid var(--border); background:none; color:var(--fg); cursor:pointer; font-size:13px; display:flex; align-items:center; justify-content:center;}
  .qty-val{font-size:13px; min-width:16px; text-align:center;}
  .remove-btn{background:none;border:none;color:var(--fg-soft);font-size:12px;cursor:pointer;text-decoration:underline; margin-left:auto;}
  .drawer-foot{border-top:1px solid var(--border); padding:20px 22px;}
  .total-row{display:flex; justify-content:space-between; font-size:15px; margin-bottom:14px;}
  .total-row b{font-family:'DM Serif Display', serif; font-size:19px;}
  .checkout-btn{width:100%; background:#0070BA; color:#fff; border:none; padding:13px; font-family:inherit; font-size:14.5px; cursor:pointer; display:flex; align-items:center; justify-content:center; gap:8px;}
  .checkout-btn:hover{background:#005ea6;}
  .checkout-btn:disabled{background:var(--border); color:var(--fg-soft); cursor:not-allowed;}
  .note{font-size:11.5px; color:var(--fg-soft); text-align:center; margin-top:10px; line-height:1.5;}
  .setup-warning{font-size:11.5px; background:#F4E3D2; color:#6B4A22; border:1px solid #E0B98A; padding:9px 11px; margin-top:12px; line-height:1.5;}
  @media (prefers-color-scheme: dark){ :root:not([data-theme="light"]) .setup-warning{background:#3A2E1A; color:#E8C58E; border-color:#5A4322;} }
  :root[data-theme="dark"] .setup-warning{background:#3A2E1A; color:#E8C58E; border-color:#5A4322;}

  @media (max-width:760px){
    .hero{grid-template-columns:1fr; gap:28px;}
    .hero-side{border-left:none; border-top:1px solid var(--border); padding-left:0; padding-top:24px;}
    nav.top-nav{display:none;}
    .catalog{grid-template-columns:1fr;}
    .promise-inner{grid-template-columns:1fr; gap:24px;}
  }
</style>
</head>
<body>

<header class="top">
  <div class="top-inner">
    <div class="brand">
      <svg class="brand-mark" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
        <circle cx="16" cy="14" r="9" stroke="currentColor" stroke-width="1.5"/>
        <path d="M16 23v5M12 28h8" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
      </svg>
      <div class="brand-name">Lueur Studio</div>
    </div>
    <nav class="top-nav">
      <a href="#catalogue">Catalogue</a>
      <a href="#promesse">La démarche</a>
    </nav>
    <button class="cart-btn" id="cartBtn">Panier <span class="cart-count" id="cartCount">0</span></button>
  </div>
</header>

<div class="hero">
  <div>
    <div class="hero-eyebrow">Objets pour la maison, choisis un à un</div>
    <h1>Peu d'objets, mais qui restent.</h1>
    <p>Une petite sélection de pièces pour la maison — céramique, bois, lin — pensées pour durer plus longtemps qu'une saison de déco.</p>
  </div>
  <div class="hero-side">
    <b>Livraison sous 3 à 6 jours</b>
    <p>Expédié depuis nos entrepôts partenaires en Europe.</p>
    <b>Paiement sécurisé via PayPal</b>
    <p>Aucune carte à saisir sur le site.</p>
  </div>
</div>

<div class="section-head" id="catalogue">
  <h2>Catalogue</h2>
  <span id="itemCount">8 pièces</span>
</div>
<div class="catalog" id="catalogList"></div>

<div class="promise" id="promesse">
  <div class="promise-inner">
    <div class="promise-item"><b>Sélection resserrée</b><p>Chaque pièce est choisie pour sa forme et sa matière, pas pour remplir le catalogue.</p></div>
    <div class="promise-item"><b>Fournisseur unique</b><p>Un seul partenaire logistique européen, pour une qualité constante d'un objet à l'autre.</p></div>
    <div class="promise-item"><b>Retours simples</b><p>14 jours pour changer d'avis, sans justification à donner.</p></div>
  </div>
</div>

<footer>Lueur Studio — boutique indépendante. Paiement par PayPal.</footer>

<div class="overlay" id="overlay"></div>
<div class="drawer" id="drawer">
  <div class="drawer-head">
    <h3>Votre panier</h3>
    <button class="drawer-close" id="drawerClose">&times;</button>
  </div>
  <div class="drawer-items" id="drawerItems"></div>
  <div class="drawer-foot">
    <div class="total-row"><span>Total</span><b id="drawerTotal">0,00&nbsp;€</b></div>
    <button class="checkout-btn" id="checkoutBtn">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M7.5 21h3l.6-4h3.2c3.6 0 6.2-1.7 6.9-5.4.6-3-1-5.6-4.6-5.6H10L7.5 21zM11 9h3.4c1.7 0 2.4 1 2.1 2.4-.4 1.9-1.7 2.6-3.4 2.6h-2.9L11 9z"/></svg>
      Payer avec PayPal
    </button>
    <p class="note" id="payNote">Tu seras redirigé vers PayPal.me pour régler le montant exact.</p>
  </div>
</div>

<script>
/* ==== À CONFIGURER ====
   Remplace la ligne ci-dessous par ton identifiant PayPal.me
   (ce qui suit "paypal.me/" dans ton lien, ex: "JeanDupont")
*/
const PAYPAL_USERNAME = ""; // <-- mets ton identifiant PayPal.me ici, entre les guillemets

const icons = {
  tray: `<svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg"><ellipse cx="24" cy="24" rx="17" ry="8" stroke="currentColor" stroke-width="1.5"/><ellipse cx="24" cy="21" rx="17" ry="8" stroke="currentColor" stroke-width="1.5"/></svg>`,
  lamp: `<svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M12 18c0-7 5.4-11 12-11s12 4 12 11" stroke="currentColor" stroke-width="1.5"/><path d="M24 18v20M17 38h14" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/><path d="M12 18h24" stroke="currentColor" stroke-width="1.5"/></svg>`,
  notebook: `<svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg"><rect x="13" y="8" width="22" height="32" rx="1" stroke="currentColor" stroke-width="1.5"/><path d="M13 14h22M18 8v6" stroke="currentColor" stroke-width="1.3"/></svg>`,
  throw: `<svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg"><rect x="9" y="14" width="30" height="20" rx="1" stroke="currentColor" stroke-width="1.5"/><path d="M9 20h30M9 26h30M15 14v20M21 14v20M27 14v20M33 14v20" stroke="currentColor" stroke-width="0.9"/></svg>`,
  candle: `<svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg"><rect x="17" y="18" width="14" height="18" rx="1" stroke="currentColor" stroke-width="1.5"/><path d="M24 18v-5M22 10c0 2 1 3 2 3s2-1 2-3-2-4-2-4-2 2-2 4z" stroke="currentColor" stroke-width="1.4"/></svg>`,
  rack: `<svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M12 12l10 8-10 8M36 12l-10 8 10 8" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/><path d="M12 36h24" stroke="currentColor" stroke-width="1.5"/></svg>`,
  diffuser: `<svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M17 22h14l-2 14a2 2 0 0 1-2 2h-6a2 2 0 0 1-2-2l-2-14z" stroke="currentColor" stroke-width="1.5"/><path d="M20 22c0-5 2-8 4-10 2 2 4 5 4 10" stroke="currentColor" stroke-width="1.3"/><path d="M18 12c-2 1.5-2 3 0 4.5M30 12c-2 1.5-2 3 0 4.5" stroke="currentColor" stroke-width="1.1" stroke-linecap="round"/></svg>`,
  basket: `<svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M11 18h26l-3 18a2 2 0 0 1-2 2H16a2 2 0 0 1-2-2l-3-18z" stroke="currentColor" stroke-width="1.5"/><path d="M11 18c0-4 5.8-6 13-6s13 2 13 6" stroke="currentColor" stroke-width="1.4"/></svg>`
};

const products = [
  {id:'p1', name:'Vide-poche en grès brut', desc:'Pièce tournée à la main, glaçure mate irrégulière, forme unique par exemplaire.', price:24, icon:'tray'},
  {id:'p2', name:'Lampe champignon verre dépoli', desc:'Lumière chaude et diffuse, base en métal brossé, idéale sur un bureau.', price:59, icon:'lamp'},
  {id:'p3', name:'Carnet pointillé toilé', desc:'160 pages 100g, couverture en toile rigide, fermoir élastique.', price:14, icon:'notebook'},
  {id:'p4', name:'Plaid en coton gaufré', desc:'130x180cm, tissage gaufré épais, lavable en machine à 30°.', price:39, icon:'throw'},
  {id:'p5', name:'Bougie bois de cèdre', desc:'Cire de soja, 40h de combustion, contenant en verre réutilisable.', price:19, icon:'candle'},
  {id:'p6', name:'Porte-revues en hêtre massif', desc:'Structure pliée sans vis apparente, finition huilée.', price:34, icon:'rack'},
  {id:'p7', name:'Diffuseur de brume en céramique', desc:'Réservoir 200ml, arrêt automatique, veilleuse LED douce.', price:29, icon:'diffuser'},
  {id:'p8', name:'Corbeille en jonc de mer', desc:'Tressée à la main, deux tailles empilables, doublure coton en option.', price:27, icon:'basket'}
];

const fmt = n => n.toLocaleString('fr-FR',{minimumFractionDigits:2, maximumFractionDigits:2}) + '\u00A0€';

let cart = {};
try{ cart = JSON.parse(localStorage.getItem('lueur_cart') || '{}'); }catch(e){ cart = {}; }
function saveCart(){ try{ localStorage.setItem('lueur_cart', JSON.stringify(cart)); }catch(e){} }

function renderCatalog(){
  const el = document.getElementById('catalogList');
  el.innerHTML = '';
  products.forEach((p, i) => {
    const card = document.createElement('div');
    card.className = 'item';
    card.innerHTML = `
      <div class="item-top"><span class="item-num">Réf. ${String(i+1).padStart(2,'0')}</span></div>
      <div class="item-art">${icons[p.icon]}</div>
      <h3 class="item-name">${p.name}</h3>
      <p class="item-desc">${p.desc}</p>
      <div class="item-foot">
        <span class="item-price">${fmt(p.price)}</span>
        <button class="add-btn" data-id="${p.id}">Ajouter</button>
      </div>`;
    el.appendChild(card);
  });
  document.querySelectorAll('.add-btn').forEach(btn=>{
    btn.addEventListener('click', () => {
      addToCart(btn.dataset.id);
      btn.textContent = 'Ajouté';
      btn.classList.add('added');
      setTimeout(()=>{ btn.textContent='Ajouter'; btn.classList.remove('added'); }, 1100);
    });
  });
}

function addToCart(id){ cart[id] = (cart[id]||0) + 1; saveCart(); renderCart(); }
function changeQty(id, delta){ if(!cart[id]) return; cart[id]+=delta; if(cart[id]<=0) delete cart[id]; saveCart(); renderCart(); }
function removeItem(id){ delete cart[id]; saveCart(); renderCart(); }

function renderCart(){
  const itemsEl = document.getElementById('drawerItems');
  const totalEl = document.getElementById('drawerTotal');
  const countEl = document.getElementById('cartCount');
  const checkoutBtn = document.getElementById('checkoutBtn');
  const payNote = document.getElementById('payNote');
  const ids = Object.keys(cart);
  let total = 0, count = 0;
  itemsEl.innerHTML = '';
  if(ids.length === 0){
    itemsEl.innerHTML = '<div class="drawer-empty">Votre panier est vide pour l\\'instant.</div>';
  } else {
    ids.forEach(id => {
      const p = products.find(x=>x.id===id);
      if(!p) return;
      const qty = cart[id];
      total += p.price * qty;
      count += qty;
      const item = document.createElement('div');
      item.className = 'cart-item';
      item.innerHTML = `
        <div class="cart-item-art">${icons[p.icon]}</div>
        <div class="cart-item-info">
          <b>${p.name}</b>
          <span>${fmt(p.price)} l'unité</span>
          <div class="qty-row">
            <button class="qty-btn" data-act="minus" data-id="${id}">−</button>
            <span class="qty-val">${qty}</span>
            <button class="qty-btn" data-act="plus" data-id="${id}">+</button>
            <button class="remove-btn" data-act="remove" data-id="${id}">retirer</button>
          </div>
        </div>`;
      itemsEl.appendChild(item);
    });
  }
  totalEl.textContent = fmt(total);
  countEl.textContent = count;
  itemsEl.querySelectorAll('[data-act]').forEach(btn=>{
    btn.addEventListener('click', () => {
      const id = btn.dataset.id;
      if(btn.dataset.act==='plus') changeQty(id,1);
      else if(btn.dataset.act==='minus') changeQty(id,-1);
      else removeItem(id);
    });
  });

  checkoutBtn.disabled = ids.length === 0;
  if(!PAYPAL_USERNAME){
    payNote.innerHTML = 'Identifiant PayPal.me non configuré — ajoute-le dans le code (variable <code>PAYPAL_USERNAME</code>) pour activer le paiement.';
  } else {
    payNote.textContent = 'Tu seras redirigé vers PayPal.me pour régler ' + fmt(total) + '.';
  }
}

const drawer = document.getElementById('drawer');
const overlay = document.getElementById('overlay');
function openDrawer(){ drawer.classList.add('open'); overlay.classList.add('open'); }
function closeDrawer(){ drawer.classList.remove('open'); overlay.classList.remove('open'); }
document.getElementById('cartBtn').addEventListener('click', openDrawer);
document.getElementById('drawerClose').addEventListener('click', closeDrawer);
overlay.addEventListener('click', closeDrawer);

document.getElementById('checkoutBtn').addEventListener('click', () => {
  const ids = Object.keys(cart);
  if(ids.length === 0) return;
  let total = 0;
  ids.forEach(id => { const p = products.find(x=>x.id===id); if(p) total += p.price * cart[id]; });
  if(!PAYPAL_USERNAME){
    alert("Identifiant PayPal.me manquant : ajoute-le dans le code (variable PAYPAL_USERNAME) avant de pouvoir encaisser un paiement.");
    return;
  }
  const amount = total.toFixed(2);
  window.open(`https://paypal.me/${PAYPAL_USERNAME}/${amount}EUR`, '_blank');
});

renderCatalog();
renderCart();
</script>

</body>
</html>