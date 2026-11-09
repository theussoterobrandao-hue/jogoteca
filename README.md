[index.html](https://github.com/user-attachments/files/34593971/index.html)
<!doctype html>
<html lang="pt-BR">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Jogoteca</title>
<meta name="theme-color" content="#0f5c66">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
/* Layout: mobile-first, coluna única com barra de navegação inferior; topo com menu a partir de 900px.
   Paleta e tipo seguem o protótipo do Figma (verde-água + amarelo, Inter). */
:root {
  --fundo: #f2faf9;
  --topo: rgba(242, 250, 249, .92);
  --superficie: #ffffff;
  --superficie-suave: #e6f5f2;
  --superficie-hover: #d6efea;
  --hero: #c9f0ec;
  --palco: #d4f1ec;
  --tinta: #12324a;
  --tinta-suave: #4f6b7a;
  --placeholder: #7f98a3;
  --marca: #0f5c66;
  --marca-texto: #0f5c66;
  --marca-viva: #14b8b0;
  --amarelo: #ffc94a;
  --amarelo-escuro: #f0b429;
  --sobre-amarelo: #12324a;
  --turquesa: #4fd1c5;
  --borda: #dcebe8;
  --sombra: 0 1px 2px rgba(18, 50, 74, .06), 0 4px 14px rgba(18, 50, 74, .06);
  --sombra-hover: 0 6px 20px rgba(18, 50, 74, .12);

  --fonte: "Inter", system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
  --raio: 14px;
  --raio-sm: 8px;
  --tabbar: 64px;
}
@media (prefers-color-scheme: dark) {
  :root:not([data-theme="light"]) {
    --fundo: #0c1a20; --topo: rgba(12, 26, 32, .92); --superficie: #12262d; --superficie-suave: #18323a;
    --superficie-hover: #1f3e47; --hero: #123a3d; --palco: #133b3e; --tinta: #e4f1f1; --tinta-suave: #9db7be;
    --placeholder: #6f8c95; --marca-texto: #5fd8cc; --borda: #22414a;
    --sombra: 0 1px 2px rgba(0, 0, 0, .3); --sombra-hover: 0 6px 20px rgba(0, 0, 0, .4);
    color-scheme: dark;
  }
}
:root[data-theme="dark"] {
  --fundo: #0c1a20; --topo: rgba(12, 26, 32, .92); --superficie: #12262d; --superficie-suave: #18323a;
  --superficie-hover: #1f3e47; --hero: #123a3d; --palco: #133b3e; --tinta: #e4f1f1; --tinta-suave: #9db7be;
  --placeholder: #6f8c95; --marca-texto: #5fd8cc; --borda: #22414a;
  --sombra: 0 1px 2px rgba(0, 0, 0, .3); --sombra-hover: 0 6px 20px rgba(0, 0, 0, .4);
  color-scheme: dark;
}

*, *::before, *::after { box-sizing: border-box; }
body {
  margin: 0;
  font-family: var(--fonte); font-size: 15px; line-height: 1.5;
  color: var(--tinta); background: var(--fundo);
  padding-bottom: calc(var(--tabbar) + env(safe-area-inset-bottom, 0px));
}
body::before { content: ""; position: fixed; inset: 0 0 auto; height: env(safe-area-inset-top, 0px); z-index: 25; background: var(--fundo); }
h1, h2 { margin: 0; line-height: 1.2; letter-spacing: -.01em; text-wrap: balance; }
p { margin: 0; }
a { color: inherit; }
svg { display: block; }

.wrap {
  width: 100%; max-width: 1120px; margin: 0 auto;
  padding-left: max(16px, env(safe-area-inset-left, 0px));
  padding-right: max(16px, env(safe-area-inset-right, 0px));
}
main.wrap { padding-block: 20px 32px; outline: none; }

.sr-only { position: absolute; width: 1px; height: 1px; margin: -1px; overflow: hidden; clip: rect(0 0 0 0); white-space: nowrap; border: 0; }
:focus-visible { outline: 3px solid var(--marca-viva); outline-offset: 2px; border-radius: 4px; }

/* Topo */
.topbar { position: sticky; top: env(safe-area-inset-top, 0px); z-index: 20; background: var(--topo); backdrop-filter: saturate(160%) blur(10px); border-bottom: 1px solid var(--borda); }
.topbar .wrap { display: flex; align-items: center; justify-content: space-between; height: 56px; }
.logo { display: inline-flex; align-items: center; gap: 8px; text-decoration: none; font-weight: 800; letter-spacing: .02em; font-size: 16px; }
.logo__mark { display: grid; place-items: center; width: 28px; height: 28px; border-radius: 8px; background: var(--marca-viva); color: var(--marca); font-size: 16px; }
.topnav { display: none; gap: 28px; }
.topnav a { text-decoration: none; font-size: 14px; color: var(--tinta-suave); padding: 6px 0; border-bottom: 2px solid transparent; }
.topnav a:hover { color: var(--tinta); }
.topnav a[aria-current="page"] { color: var(--tinta); font-weight: 600; border-color: var(--amarelo); }

/* Barra inferior */
.tabbar {
  position: fixed; left: 0; right: 0; bottom: 0; z-index: 30;
  display: grid; grid-template-columns: repeat(3, 1fr);
  height: calc(var(--tabbar) + env(safe-area-inset-bottom, 0px));
  padding-bottom: env(safe-area-inset-bottom, 0px);
  padding-left: env(safe-area-inset-left, 0px); padding-right: env(safe-area-inset-right, 0px);
  background: var(--superficie); border-top: 1px solid var(--borda); box-shadow: var(--sombra);
}
.tabbar a { display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 4px; text-decoration: none; font-size: 12px; font-weight: 500; color: var(--tinta-suave); }
.tabbar svg { width: 22px; height: 22px; fill: currentColor; }
.tabbar a[aria-current="page"] { color: var(--marca-texto); font-weight: 700; }
.tabbar a[aria-current="page"] svg { fill: var(--marca-viva); }

/* Botões */
.btn { display: inline-flex; align-items: center; justify-content: center; gap: 6px; min-height: 44px; padding: 0 18px; border: 0; border-radius: var(--raio-sm); font: 600 14px/1 var(--fonte); text-decoration: none; cursor: pointer; transition: background-color .15s, transform .1s; }
.btn:active { transform: translateY(1px); }
.btn--primario { background: var(--amarelo); color: var(--sobre-amarelo); }
.btn--primario:hover { background: var(--amarelo-escuro); }
.btn--claro { background: var(--superficie-suave); color: var(--tinta); }
.btn--claro:hover { background: var(--superficie-hover); }
.acoes { display: flex; flex-wrap: wrap; gap: 10px; }
.acoes--rodape { margin-top: 24px; }
.sobretitulo { font-size: 11px; font-weight: 700; letter-spacing: .06em; text-transform: uppercase; color: var(--marca-texto); }

/* Hero */
.hero { position: relative; overflow: hidden; display: grid; gap: 16px; padding: 22px 20px; border-radius: var(--raio); background: var(--hero); }
.hero h1 { font-size: 28px; margin: 8px 0 10px; }
.hero__texto { position: relative; min-width: 0; }
.hero__texto > p:not(.sobretitulo) { color: var(--tinta-suave); margin-bottom: 18px; }
.hero__texto .acoes .btn { flex: 1 1 auto; }
.hero__arte { position: absolute; right: -40px; top: -30px; height: 150px; width: 200px; opacity: .25; pointer-events: none; }
.hero__arte span { position: absolute; border-radius: 50%; }
.hero__disco { right: 8%; top: 0; width: 150px; height: 150px; background: var(--marca-viva); }
.hero__anel { right: calc(8% + 35px); top: 35px; width: 80px; height: 80px; background: var(--amarelo); }
.hero__nucleo { right: calc(8% + 59px); top: 59px; width: 32px; height: 32px; background: var(--marca); }
.hero__bolha { right: calc(8% + 140px); top: 70px; width: 42px; height: 42px; background: var(--turquesa); opacity: .7; }
.hero__arte .hero__linha { right: 6%; bottom: 0; width: 170px; height: 6px; border-radius: 3px; background: var(--amarelo); }

/* Seções e cards */
.secao { margin-top: 28px; }
.secao__cab { display: flex; align-items: baseline; justify-content: space-between; gap: 12px; margin-bottom: 12px; }
.secao__cab h2 { font-size: 18px; }
.secao__cab p { font-size: 12px; color: var(--tinta-suave); text-align: right; }
.grade { list-style: none; margin: 0; padding: 0; display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 12px; }
.card { display: flex; flex-direction: column; height: 100%; background: var(--superficie); border: 1px solid var(--borda); border-radius: var(--raio-sm); overflow: hidden; text-decoration: none; box-shadow: var(--sombra); transition: transform .15s, box-shadow .15s; }
.card:hover { transform: translateY(-2px); box-shadow: var(--sombra-hover); }
.card__info { display: flex; flex-direction: column; gap: 2px; padding: 10px 10px 12px; min-width: 0; }
.card__titulo { font-size: 13px; font-weight: 700; }
.card__genero { font-size: 12px; color: var(--tinta-suave); }

.capa { position: relative; overflow: hidden; aspect-ratio: 16 / 9; max-width: 100%; background: var(--tema); }
.capa span { position: absolute; }
.capa__circulo { right: -16%; top: -32%; width: 54%; aspect-ratio: 1; border-radius: 50%; background: var(--destaque); }
.capa__bolha { left: 6%; bottom: 8%; width: 22%; aspect-ratio: 1; border-radius: 50%; background: rgba(255, 255, 255, .14); }
.capa__faixa { left: 0; right: 0; bottom: 12%; height: 5%; background: var(--destaque); opacity: .9; }
.capa__titulo { left: 8%; right: 40%; top: 20%; color: #fff; font-weight: 800; font-size: clamp(11px, 3.2vw, 14px); line-height: 1.15; text-shadow: 0 1px 2px rgba(0, 0, 0, .25); }
.capa--grande { border-radius: var(--raio); }
.capa--grande .capa__circulo { right: -10%; top: -40%; width: 58%; }
.capa--grande .capa__bolha { left: 8%; bottom: 10%; width: 18%; }
.capa--grande .capa__titulo { top: auto; bottom: 22%; right: 45%; font-size: clamp(24px, 7vw, 40px); }

/* Páginas internas */
.cab-pagina { margin-bottom: 18px; }
.cab-pagina h1 { font-size: 26px; margin-bottom: 6px; }
.cab-pagina p { font-size: 14px; color: var(--tinta-suave); }

.busca { display: flex; align-items: center; gap: 8px; padding: 6px 6px 6px 12px; margin-bottom: 14px; background: var(--superficie-suave); border-radius: var(--raio-sm); }
.busca svg { width: 18px; height: 18px; fill: var(--marca-texto); flex: none; }
.busca input { flex: 1; min-width: 0; height: 40px; border: 0; background: transparent; font: 16px var(--fonte); color: var(--tinta); }
.busca input::placeholder { color: var(--placeholder); }
.busca input:focus { outline: none; }
.busca:focus-within { box-shadow: 0 0 0 3px var(--marca-viva); }
.busca .btn { min-height: 40px; padding: 0 14px; }

.meta { display: flex; flex-wrap: wrap; justify-content: space-between; gap: 4px 16px; margin-bottom: 12px; font-size: 12px; color: var(--tinta-suave); }
.vazio { padding: 24px 0; color: var(--tinta-suave); }
.link-texto { background: none; border: 0; padding: 0; font: inherit; color: var(--marca-texto); font-weight: 600; text-decoration: underline; cursor: pointer; }

.pag { display: flex; justify-content: center; flex-wrap: wrap; gap: 8px; margin-top: 24px; }
.pag__item { display: inline-grid; place-items: center; min-width: 44px; min-height: 40px; padding: 0 12px; border-radius: var(--raio-sm); background: var(--superficie-suave); font-size: 14px; font-weight: 600; text-decoration: none; }
.pag__item--ativo { background: var(--amarelo); color: var(--sobre-amarelo); }
.pag__item--desab { opacity: .45; }

.migalhas { display: flex; flex-wrap: wrap; gap: 6px; font-size: 12px; color: var(--tinta-suave); margin-bottom: 14px; }
.migalhas a { text-decoration: none; }
.migalhas a:hover { text-decoration: underline; }
.detalhe { display: grid; gap: 20px; }
.detalhe__info { min-width: 0; }
.detalhe h1 { font-size: 30px; margin: 6px 0 10px; }
.detalhe__desc { color: var(--tinta-suave); margin-bottom: 14px; max-width: 60ch; }
.ficha { margin: 0 0 20px; display: grid; gap: 6px; font-size: 14px; }
.ficha div { display: flex; flex-wrap: wrap; gap: 6px; }
.ficha dt { color: var(--tinta-suave); }
.ficha dt::after { content: ":"; }
.ficha dd { margin: 0; font-weight: 600; }
.detalhe .acoes .btn { flex: 1 1 auto; }
.aviso { margin-top: 24px; padding: 16px; border-radius: var(--raio-sm); background: var(--superficie-suave); }
.aviso h2 { font-size: 15px; margin-bottom: 4px; }
.aviso p { font-size: 13px; color: var(--tinta-suave); }

.palco { display: grid; place-items: center; text-align: center; gap: 6px; min-height: 260px; padding: 32px 20px; margin-bottom: 20px; border-radius: var(--raio); background: var(--palco); }
.palco__estrela { font-size: 34px; color: var(--marca-texto); animation: pulsar 2.4s ease-in-out infinite; }
.palco h2 { font-size: 26px; }
.palco p { font-size: 14px; color: var(--tinta-suave); }
@keyframes pulsar { 50% { transform: scale(1.15); opacity: .8; } }
@media (prefers-reduced-motion: reduce) { *, *::before, *::after { animation: none !important; transition: none !important; } }

@media (min-width: 600px) {
  .grade { grid-template-columns: repeat(3, minmax(0, 1fr)); gap: 16px; }
  .hero { grid-template-columns: 1.4fr 1fr; align-items: center; padding: 28px; }
  .hero__arte { position: relative; right: auto; top: auto; width: auto; opacity: 1; }
  .hero__texto .acoes .btn { flex: 0 0 auto; }
  .hero h1 { font-size: 32px; }
  .detalhe { grid-template-columns: minmax(220px, 300px) 1fr; align-items: start; gap: 24px; }
  .detalhe .acoes .btn { flex: 0 0 auto; }
  .capa--grande { aspect-ratio: 1 / 1; }
  .capa--grande .capa__circulo { right: -22%; top: -22%; width: 85%; }
  .capa--grande .capa__bolha { left: 12%; bottom: 18%; width: 30%; }
  .capa--grande .capa__titulo { bottom: 34%; right: 20%; font-size: 36px; }
}
@media (min-width: 900px) {
  body { padding-bottom: 0; }
  .tabbar { display: none; }
  .topnav { display: flex; }
  .topbar .wrap { height: 64px; }
  main.wrap { padding-block: 28px 56px; }
  .grade { grid-template-columns: repeat(4, minmax(0, 1fr)); gap: 18px; }
  .hero { padding: 32px 36px; }
  .hero h1 { font-size: 36px; }
  .hero__arte { height: 190px; }
  .hero__disco { width: 190px !important; height: 190px !important; }
  .hero__anel { width: 100px !important; height: 100px !important; top: 45px !important; right: calc(8% + 45px) !important; }
  .hero__nucleo { width: 40px !important; height: 40px !important; top: 75px !important; right: calc(8% + 75px) !important; }
  .hero__bolha { right: calc(8% + 175px) !important; top: 90px !important; width: 56px !important; height: 56px !important; }
  .hero__arte .hero__linha { width: 220px; }
  .cab-pagina h1 { font-size: 30px; }
  .detalhe { grid-template-columns: 340px 1fr; gap: 32px; }
  .detalhe h1 { font-size: 36px; }
}
</style>
</head>
<body>

<header class="topbar">
  <div class="wrap">
    <a class="logo" href="#inicio" aria-label="Jogoteca, ir para o início"><span class="logo__mark" aria-hidden="true">✦</span>JOGOTECA</a>
    <nav class="topnav" aria-label="Principal">
      <a href="#inicio" data-nav="inicio">Início</a>
      <a href="#catalogo" data-nav="catalogo">Catálogo</a>
      <a href="#busca" data-nav="busca">Buscar jogos</a>
    </nav>
  </div>
</header>

<main id="conteudo" class="wrap" tabindex="-1"></main>

<nav class="tabbar" aria-label="Navegação rápida">
  <a href="#inicio" data-nav="inicio"><svg viewBox="0 0 24 24" aria-hidden="true"><path d="M3 10.5 12 3l9 7.5V20a1 1 0 0 1-1 1h-5v-6h-6v6H4a1 1 0 0 1-1-1z"/></svg><span>Início</span></a>
  <a href="#catalogo" data-nav="catalogo"><svg viewBox="0 0 24 24" aria-hidden="true"><path d="M4 4h7v7H4zM13 4h7v7h-7zM4 13h7v7H4zM13 13h7v7h-7z"/></svg><span>Catálogo</span></a>
  <a href="#busca" data-nav="busca"><svg viewBox="0 0 24 24" aria-hidden="true"><path d="M10.5 3a7.5 7.5 0 0 1 5.9 12.1l4.8 4.8-1.4 1.4-4.8-4.8A7.5 7.5 0 1 1 10.5 3zm0 2a5.5 5.5 0 1 0 0 11 5.5 5.5 0 0 0 0-11z"/></svg><span>Buscar</span></a>
</nav>

<script>
const JOGOS = [
  ["astro-arena","Astro Arena","Ação","12 anos","#0f5c66","#ffd166","Duelos rápidos em arenas flutuantes no meio de um cinturão de asteroides."],
  ["astro-lab","Astro Lab","Estratégia","Livre","#0f5c66","#fbe08a","Monte um laboratório orbital e pesquise tecnologias para colonizar novos planetas."],
  ["astro-voyage","Astro Voyage","Exploração","Livre","#124e66","#ffd166","Uma viagem tranquila por sistemas solares desconhecidos, catalogando cada descoberta."],
  ["castelo-das-nuvens","Castelo das Nuvens","Estratégia","10 anos","#0d6670","#fbe08a","Defenda um castelo suspenso no céu organizando recursos e aliados."],
  ["circuito-neon","Circuito Neon","Corrida","Livre","#0d6670","#ffd166","Corridas noturnas em pistas iluminadas, com atalhos que mudam a cada volta."],
  ["floresta-luminosa","Floresta Luminosa","Exploração","Livre","#0d6670","#fbe08a","Explore uma floresta que brilha à noite e descubra os segredos de suas criaturas."],
  ["jardim-de-cristal","Jardim de Cristal","Simulação","Livre","#0f5c66","#ffd166","Cultive plantas de cristal e transforme um terreno vazio num jardim premiado."],
  ["labirinto-prisma","Labirinto Prisma","Quebra-cabeça","Livre","#0d6670","#fbe08a","Redirecione feixes de luz para abrir passagens num labirinto de espelhos."],
  ["mare-de-neon","Maré de Neon","Arcade","Livre","#124e66","#ffd166","Surfe ondas de luz e acumule pontos num arcade de ritmo acelerado."],
  ["mundo-de-origami","Mundo de Origami","Casual","Livre","#0d6670","#fbe08a","Dobre papéis para criar pontes, barcos e caminhos num mundo feito de origami."],
  ["orbita-zero","Órbita Zero","Aventura espacial","10 anos","#0f5c66","#4fd1c5","Viaje entre mundos, descubra ruínas cósmicas e explore um universo repleto de mistérios. Um jogo fictício criado para demonstrar o protótipo."],
  ["pixel-rush","Pixel Rush","Plataforma","Livre","#0d6670","#fbe08a","Plataforma clássica em pixel art, com fases curtas e desafios cronometrados."],
  ["portais-do-tempo","Portais do Tempo","Aventura","10 anos","#0d6670","#fbe08a","Atravesse portais para diferentes épocas e corrija falhas na linha do tempo."],
  ["rota-astral","Rota Astral","Aventura","10 anos","#0f5c66","#9be7df","Trace rotas entre constelações e guie uma nave de carga até o destino."],
  ["ruinas-do-sol","Ruínas do Sol","Ação","12 anos","#124e66","#4fd1c5","Enfrente guardiões antigos em templos escondidos sob o deserto."],
  ["saltos-da-lua","Saltos da Lua","Plataforma","Livre","#0f5c66","#ffd166","Pule entre crateras com gravidade reduzida e colete fragmentos lunares."],
  ["torre-esmeralda","Torre Esmeralda","Estratégia","10 anos","#0d6670","#fbe08a","Construa andar por andar uma torre defensiva contra ondas de invasores."],
  ["trilha-cosmica","Trilha Cósmica","Corrida","Livre","#0f5c66","#ffd166","Corridas em trilhas espaciais com curvas impossíveis e turbo de cometas."],
  ["vale-das-estrelas","Vale das Estrelas","Aventura","Livre","#0d6670","#4fd1c5","Acompanhe uma pequena exploradora num vale onde as estrelas caem toda noite."],
  ["vila-dos-ventos","Vila dos Ventos","Simulação","Livre","#0f5c66","#9be7df","Administre uma vila movida a cata-ventos e mantenha todos felizes."],
  ["voo-livre","Voo Livre","Aventura","Livre","#0f5c66","#fbe08a","Plane sobre ilhas flutuantes e descubra caminhos escondidos entre as nuvens."],
  ["xadrez-lunar","Xadrez Lunar","Estratégia","Livre","#0d6670","#fbe08a","Uma variação do xadrez jogada num tabuleiro que muda com as fases da lua."],
  ["ypsilon-quest","Ypsilon Quest","Quebra-cabeça","Livre","#0f5c66","#ffd166","Resolva enigmas lógicos para atravessar um mundo em forma de letra Y."],
  ["zenite-azul","Zênite Azul","Ação","12 anos","#124e66","#ffd166","Combates aéreos no ponto mais alto do céu, sobre um oceano sem fim."]
].map(([slug, titulo, genero, classificacao, tema, destaque, descricao]) => ({ slug, titulo, genero, classificacao, tema, destaque, descricao }));

const SECOES_HOME = [
  { titulo: "Jogos em destaque", sub: "Escolhas especiais da plataforma", slugs: ["orbita-zero","floresta-luminosa","circuito-neon","castelo-das-nuvens"] },
  { titulo: "Mais acessados", sub: "Os favoritos da comunidade", slugs: ["astro-arena","pixel-rush","rota-astral","labirinto-prisma"] },
  { titulo: "Novidades", sub: "Os jogos adicionados recentemente", slugs: ["astro-lab","jardim-de-cristal","mare-de-neon","vale-das-estrelas"] }
];

(function () {
  "use strict";
  const POR_PAGINA = 20;
  const app = document.getElementById("conteudo");
  let termoBusca = "astro"; // exemplo inicial, como no Figma

  const esc = (s) => String(s).replace(/[&<>"']/g, (c) => ({ "&": "&amp;", "<": "&lt;", ">": "&gt;", '"': "&quot;", "'": "&#39;" }[c]));
  const normalizar = (s) => s.normalize("NFD").replace(/[\u0300-\u036f]/g, "").toLowerCase().trim();
  const ordenados = [...JOGOS].sort((a, b) => a.titulo.localeCompare(b.titulo, "pt-BR", { sensitivity: "base" }));
  const porSlug = (slug) => JOGOS.find((j) => j.slug === slug);
  const totalPaginas = Math.ceil(ordenados.length / POR_PAGINA);

  const capa = (j, grande) => `
    <div class="capa${grande ? " capa--grande" : ""}" style="--tema:${j.tema};--destaque:${j.destaque}" aria-hidden="true">
      <span class="capa__circulo"></span><span class="capa__bolha"></span>${grande ? "" : '<span class="capa__faixa"></span>'}
      <span class="capa__titulo">${esc(j.titulo.toUpperCase())}</span>
    </div>`;
  const card = (j) => `<li><a class="card" href="#jogo-${j.slug}">${capa(j)}<span class="card__info"><span class="card__titulo">${esc(j.titulo)}</span><span class="card__genero">${esc(j.genero)}</span></span></a></li>`;
  const grade = (l) => `<ul class="grade" role="list">${l.map(card).join("")}</ul>`;
  const formBusca = (v, rotulo) => `
    <form class="busca" role="search" data-busca>
      <label class="sr-only" for="campo-busca">Buscar por nome ou parte do título</label>
      <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M10.5 3a7.5 7.5 0 0 1 5.9 12.1l4.8 4.8-1.4 1.4-4.8-4.8A7.5 7.5 0 1 1 10.5 3zm0 2a5.5 5.5 0 1 0 0 11 5.5 5.5 0 0 0 0-11z"/></svg>
      <input id="campo-busca" name="q" type="search" autocomplete="off" enterkeyhint="search" placeholder="Buscar por nome ou parte do título..." value="${esc(v)}">
      <button class="btn btn--primario" type="submit">${rotulo}</button>
    </form>`;

  function inicio() {
    return { t: "Início", h: `
      <section class="hero">
        <div class="hero__texto">
          <p class="sobretitulo">Experiência digital • Catálogo de jogos</p>
          <h1>Descubra seu próximo jogo favorito.</h1>
          <p>Explore títulos em destaque, descubra novidades e navegue por uma coleção de aventuras.</p>
          <div class="acoes">
            <a class="btn btn--primario" href="#catalogo">Explorar catálogo <span aria-hidden="true">→</span></a>
            <a class="btn btn--claro" href="#jogo-orbita-zero">Ver jogo em destaque</a>
          </div>
        </div>
        <div class="hero__arte" aria-hidden="true"><span class="hero__disco"></span><span class="hero__anel"></span><span class="hero__nucleo"></span><span class="hero__bolha"></span><span class="hero__linha"></span></div>
      </section>
      ${SECOES_HOME.map((s) => `<section class="secao"><div class="secao__cab"><h2>${s.titulo}</h2><p>${s.sub}</p></div>${grade(s.slugs.map(porSlug))}</section>`).join("")}` };
  }

  function catalogo(p) {
    const lista = ordenados.slice((p - 1) * POR_PAGINA, p * POR_PAGINA);
    const href = (n) => (n === 1 ? "#catalogo" : `#catalogo-${n}`);
    let pag = p > 1 ? `<a class="pag__item" href="${href(p - 1)}">Anterior</a>` : `<span class="pag__item pag__item--desab" aria-disabled="true">Anterior</span>`;
    for (let n = 1; n <= totalPaginas; n++) pag += `<a class="pag__item${n === p ? " pag__item--ativo" : ""}" href="${href(n)}"${n === p ? ' aria-current="page"' : ""}>${n}</a>`;
    pag += p < totalPaginas ? `<a class="pag__item" href="${href(p + 1)}">Próxima</a>` : `<span class="pag__item pag__item--desab" aria-disabled="true">Próxima</span>`;
    return { t: `Catálogo, página ${p}`, h: `
      <header class="cab-pagina">
        <h1>Catálogo de jogos</h1>
        <p>${p === 1 ? "Explore toda a coleção. Organize, pesquise e encontre sua próxima aventura." : `Página ${p} · Continuação alfabética da coleção fictícia`}</p>
      </header>
      ${p === 1 ? formBusca("", "Buscar") : ""}
      <div class="meta"><span>${POR_PAGINA} jogos por página • Ordem alfabética (A–Z)</span><span>Página ${p} de ${totalPaginas} • ${ordenados.length} jogos fictícios</span></div>
      ${grade(lista)}
      <nav class="pag" aria-label="Paginação">${pag}</nav>` };
  }

  function busca() {
    const termo = termoBusca.trim(), n = normalizar(termo);
    const res = n ? ordenados.filter((j) => normalizar(j.titulo).includes(n)) : [];
    let corpo;
    if (!termo) corpo = `<p class="vazio">Digite parte do nome de um jogo. Exemplo: <button type="button" class="link-texto" data-exemplo="astro">astro</button>.</p>`;
    else if (!res.length) corpo = `<p class="vazio">Nenhum jogo encontrado para “${esc(termo)}”. Tente outro trecho do título.</p>`;
    else corpo = `<div class="meta"><span>${res.length} ${res.length === 1 ? "jogo encontrado" : "jogos encontrados"} • Os resultados aparecem em ordem alfabética</span></div>${grade(res)}`;
    return { t: "Buscar jogos", h: `
      <header class="cab-pagina">
        <h1>${termo ? "Resultados da busca" : "Buscar jogos"}</h1>
        <p>Pesquisa por trecho do título${termo ? `: “${esc(termo)}”` : ""}.</p>
      </header>
      ${formBusca(termo, "Pesquisar")}
      <div aria-live="polite">${corpo}</div>
      <div class="acoes acoes--rodape"><a class="btn btn--claro" href="#catalogo">Voltar ao catálogo</a></div>` };
  }

  function detalhes(j) {
    return { t: j.titulo, h: `
      <nav class="migalhas" aria-label="Você está em"><a href="#inicio">Início</a><span aria-hidden="true">/</span><a href="#catalogo">Catálogo</a><span aria-hidden="true">/</span><span aria-current="page">${esc(j.titulo)}</span></nav>
      <article class="detalhe">
        ${capa(j, true)}
        <div class="detalhe__info">
          <p class="sobretitulo">${esc(j.genero.split(" ")[0])} • Disponível</p>
          <h1>${esc(j.titulo)}</h1>
          <p class="detalhe__desc">${esc(j.descricao)}</p>
          <dl class="ficha">
            <div><dt>Gênero</dt><dd>${esc(j.genero)}</dd></div>
            <div><dt>Classificação etária</dt><dd>${esc(j.classificacao)}</dd></div>
            <div><dt>Disponibilidade</dt><dd>Disponível</dd></div>
          </dl>
          <div class="acoes">
            <a class="btn btn--primario" href="#acesso-${j.slug}">Jogar agora <span aria-hidden="true">→</span></a>
            <a class="btn btn--claro" href="#catalogo">Voltar ao catálogo</a>
          </div>
        </div>
      </article>
      <aside class="aviso"><h2>Fluxo demonstrativo</h2><p>A navegação e a abertura do jogo são simuladas. O registro real de acessos depende de uma implementação futura.</p></aside>` };
  }

  function acesso(j) {
    return { t: `Acesso: ${j.titulo}`, h: `
      <header class="cab-pagina"><h1>Acesso ao jogo</h1><p>Esta tela simula a abertura do endereço de um jogo pelo navegador.</p></header>
      <section class="palco"><span class="palco__estrela" aria-hidden="true">✦</span><h2>${esc(j.titulo)}</h2><p>Demonstração do fluxo de acesso</p></section>
      <div class="acoes"><a class="btn btn--primario" href="#jogo-${j.slug}">Voltar aos detalhes</a><a class="btn btn--claro" href="#inicio">Ir para a Home</a></div>` };
  }

  function rota() {
    const h = location.hash.replace(/^#/, "");
    let m;
    if (!h || h === "inicio") return ["inicio", inicio()];
    if (h === "catalogo") return ["catalogo", catalogo(1)];
    if ((m = h.match(/^catalogo-(\d+)$/))) return ["catalogo", catalogo(Math.min(Math.max(+m[1], 1), totalPaginas))];
    if (h === "busca") return ["busca", busca()];
    if ((m = h.match(/^(jogo|acesso)-([a-z0-9-]+)$/)) && porSlug(m[2])) {
      const j = porSlug(m[2]);
      return ["catalogo", m[1] === "jogo" ? detalhes(j) : acesso(j)];
    }
    return ["inicio", inicio()];
  }

  let primeira = true;
  function render() {
    const [nav, tela] = rota();
    app.innerHTML = tela.h;
    document.title = `${tela.t} · Jogoteca`;
    document.querySelectorAll("[data-nav]").forEach((a) => a.dataset.nav === nav ? a.setAttribute("aria-current", "page") : a.removeAttribute("aria-current"));
    window.scrollTo(0, 0);
    if (!primeira) app.focus({ preventScroll: true });
    primeira = false;
  }

  function buscar(q) {
    termoBusca = q;
    if (location.hash === "#busca") render(); else location.hash = "busca";
  }

  document.addEventListener("submit", (e) => {
    const f = e.target.closest("[data-busca]");
    if (!f) return;
    e.preventDefault();
    f.q.blur(); // fecha o teclado no celular
    buscar(f.q.value);
  });
  document.addEventListener("click", (e) => {
    const b = e.target.closest("[data-exemplo]");
    if (b) buscar(b.dataset.exemplo);
  });

  window.addEventListener("hashchange", render);
  render();
})();
</script>
</body>
</html>
