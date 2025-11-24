<!doctype html>
<html lang="ja">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>L-Crown | 西武ライオンズ データ速報</title>

  <style>
    :root{
      --lions-blue:#092048;
      --hawks-yellow:#ffcc00;
      --bg:#f5f7fa;
      --card:#ffffff;
      --muted:#94a3b8;
      --border:#e2e8f0;
      --score-bg: rgba(255,255,255,0.06);
    }
    body{
      margin:0;
      background:var(--bg);
      font-family:'Hiragino Sans','Noto Sans JP',sans-serif;
      color:#1a1a1a;
    }

    /* ▼ 固定ヘッダー（ハンバーガー対応） */
    header{
      position:sticky;
      top:0;
      z-index:50;
      background:var(--lions-blue);
      color:#fff;
      padding:12px 20px;
      font-size:1.3rem;
      font-weight:700;
      display:flex;
      align-items:center;
      justify-content:space-between;
      box-shadow:0 2px 6px rgba(0,0,0,0.2);
    }
    header .title{ font-size:1.4rem; }

    /* ▼ ハンバーガーアイコン */
    .nav-toggle{ display:none; }
    .nav-toggle-label{
      cursor:pointer;
      width:32px;
      height:24px;
      display:flex;
      flex-direction:column;
      justify-content:space-between;
      z-index:60;
    }
    .nav-toggle-label span,
    .nav-toggle-label span:before,
    .nav-toggle-label span:after{
      content:"";
      display:block;
      height:4px;
      background:#fff;
      border-radius:4px;
      transition:.3s;
    }

    /* ▼ ナビ本体（スライドイン） */
    .nav-menu{
      position:fixed;
      top:0;
      right:-240px;
      width:240px;
      height:100vh;
      background:#fff;
      box-shadow:-3px 0 8px rgba(0,0,0,0.15);
      padding-top:70px;
      transition:right .35s ease;
      z-index:55;
    }
    .nav-menu ul{ list-style:none; padding:0; margin:0; }
    .nav-menu li{ padding:15px 20px; }
    .nav-menu a{
      text-decoration:none;
      color:#1a1a1a;
      font-size:1.1rem;
      font-weight:600;
    }

    /* ▼ オーバーレイ */
    .overlay{
      position:fixed;
      inset:0;
      background:rgba(0,0,0,0.45);
      backdrop-filter:blur(3px);
      display:none;
      z-index:54;
    }
    .nav-toggle:checked ~ .overlay{ display:block; }
    .nav-toggle:checked ~ .nav-menu{ right:0; }

    /* ▼ コンテナ */
    .container{
      max-width:1100px;
      margin:0 auto;
      padding:20px;
    }


    /* ======================= */
    /* ★ 試合速報 */
    /* ======================= */
    .game-card{
      background:var(--card);
      padding:20px;
      border-radius:14px;
      box-shadow:0 2px 6px rgba(0,0,0,0.08);
      margin-bottom:25px;
    }

    .match-card{
      width:100%;
      padding:14px;
      border-radius:14px;
      background:var(--card);
      color:#000;
      box-shadow:0 6px 20px rgba(2,6,23,0.15);
      display:flex;
      gap:16px;
      align-items:center;
      flex-wrap:wrap;
    }

    .teams{
      display:flex;
      flex:1;
      align-items:center;
      gap:16px;
      flex-wrap:wrap;
    }

    .team{
      flex:1 1 120px;
      display:flex;
      align-items:center;
      gap:14px;
    }

    .logo{
      width:56px;
      height:56px;
      border-radius:12px;
      overflow:hidden;
      display:flex;
      align-items:center;
      justify-content:center;
      background:linear-gradient(135deg, rgba(255,255,255,0.02), rgba(255,255,255,0.04));
      border:2px solid rgba(0,0,0,0.05);
      flex-shrink:0;
    }
    .logo img{ width:100%; height:100%; object-fit:cover; display:block; }

    .team-name{ font-size:15px; font-weight:600; }
    .team-sub{ font-size:12px; color:var(--muted); }

    .lions .team-name{ color:var(--lions-blue); }
    .hawks .team-name{ color:var(--hawks-yellow); }

    .score{
      display:flex;
      flex-direction:row;
      align-items:center;
      justify-content:center;
      padding:10px 14px;
      border-radius:14px;
      background:var(--score-bg);
      gap:8px;
      flex-shrink:0;
    }
    .score .runs{ font-size:36px; font-weight:800; }
    .score .label{ font-size:12px; color:var(--muted); }

    .meta{
      display:flex;
      flex-direction:column;
      align-items:flex-end;
      gap:6px;
    }
    .inning{
      padding:6px 10px;
      border-radius:999px;
      font-weight:600;
      font-size:13px;
      background:#f3f4f6;
    }

    @media(max-width:560px){
      .match-card{ flex-direction:column; }
      .score{ width:100%; }
      .meta{ flex-direction:row; justify-content:space-between; width:100%; }
    }


    /* ======================= */
    /* ★ ニュース */
    /* ======================= */
    .news-section{
      background:var(--card);
      padding:20px;
      border-radius:14px;
      box-shadow:0 2px 6px rgba(0,0,0,0.08);
      margin-bottom:25px;
    }


    /* ============================ */
    /* ★ TOP3カード（カード型） */
    /* ============================ */
    .rank-section{
      background:var(--card);
      padding:20px;
      border-radius:14px;
      box-shadow:0 2px 6px rgba(0,0,0,0.08);
      margin-bottom:25px;
    }

    .ranking-tabs{
      display:flex;
      gap:10px;
      margin-bottom:14px;
    }
    .ranking-tabs button{
      padding:8px 14px;
      border-radius:8px;
      border:none;
      background:#e5e7eb;
      cursor:pointer;
      font-weight:600;
    }
    .ranking-tabs button.active{
      background:var(--lions-blue);
      color:#fff;
    }

    .ranking-content{ display:none; }
    .ranking-content.active{ display:block; }

    .ranking-card{
      display:flex;
      gap:12px;
      padding:12px;
      background:#fff;
      border-radius:12px;
      margin-bottom:10px;
      border-left:5px solid var(--lions-blue);
      box-shadow:0 2px 6px rgba(0,0,0,0.05);
    }

    .rank-num{
      font-size:1.3rem;
      font-weight:700;
    }
    .player-name{
      font-size:1.05rem;
      font-weight:700;
    }
    .player-detail{
      font-size:0.95rem;
      color:#555;
    }

  </style>
</head>

<body>

<header>
  <div class="title">L-Crown（西武ライオンズ データサイト）</div>

  <input type="checkbox" id="nav-toggle" class="nav-toggle">
  <label for="nav-toggle" class="nav-toggle-label">
    <span></span>
  </label>

  <div class="overlay"></div>

  <nav class="nav-menu">
    <ul>
      <li><a href="#game">試合速報</a></li>
      <li><a href="#news">ニュース</a></li>
      <li><a href="#rank">TOP3</a></li>
    </ul>
  </nav>
</header>

<div class="container">

  <!-- 試合速報 -->
  <section class="game-card" id="game">
    <h2>試合速報</h2>

    <div class="match-card">
      <div class="teams">
        <div class="team lions">
          <div class="logo"><span class="fallback">L</span></div>
          <div>
            <div class="team-name">Lions</div>
            <div class="team-sub">埼玉西武</div>
          </div>
        </div>

        <div class="score">
          <div class="runs">3 - 2</div>
        </div>

        <div class="team hawks">
          <div class="logo"><span class="fallback">H</span></div>
          <div>
            <div class="team-name">Hawks</div>
            <div class="team-sub">福岡ソフトバンク</div>
          </div>
        </div>
      </div>

      <div class="meta">
        <div class="inning">7回表</div>
        <div class="status">ベルーナドーム</div>
      </div>
    </div>
  </section>

  <!-- ニュース -->
  <section class="news-section" id="news">
    <h2>ニュース</h2>
    <ul>
      <li>2025/03/01 サイトをリニューアルしました。</li>
      <li>2025/02/28 選手データを最新版に更新しました。</li>
      <li>2025/02/27 今季の日程ページを公開しました。</li>
    </ul>
  </section>

  <!-- ランキング -->
  <section class="rank-section" id="rank">
    <h2>TOP3 ランキング</h2>

    <div class="ranking-tabs">
      <button class="active" data-target="batting">打撃</button>
      <button data-target="pitching">投球</button>
    </div>

    <div id="batting" class="ranking-content active">
      <div class="ranking-card">
        <div class="rank-num">1</div>
        <div>
          <div class="player-name">山川 穂高</div>
          <div class="player-detail">打率 .320 / HR 35</div>
        </div>
      </div>

      <div class="ranking-card">
        <div class="rank-num">2</div>
        <div>
          <div class="player-name">森 友哉</div>
          <div class="player-detail">打率 .310 / HR 28</div>
        </div>
      </div>

      <div class="ranking-card">
        <div class="rank-num">3</div>
        <div>
          <div class="player-name">源田 壮亮</div>
          <div class="player-detail">打率 .305 / 盗塁 25</div>
        </div>
      </div>
    </div>

    <div id="pitching" class="ranking-content">
      <div class="ranking-card">
        <div class="rank-num">1</div>
        <div>
          <div class="player-name">髙橋 光成</div>
          <div class="player-detail">防御率 2.10 / 12勝</div>
        </div>
      </div>

      <div class="ranking-card">
        <div class="rank-num">2</div>
        <div>
          <div class="player-name">平良 海馬</div>
          <div class="player-detail">防御率 2.30 / 30H</div>
        </div>
      </div>

      <div class="ranking-card">
        <div class="rank-num">3</div>
        <div>
          <div class="player-name">増田 達至</div>
          <div class="player-detail">防御率 2.50 / 28S</div>
        </div>
      </div>
    </div>
  </section>

</div>

<footer style="text-align:center; padding:40px; color:#777;">
  © 2025 L-Crown / Seibu Lions Data
</footer>

<script>
const tabs = document.querySelectorAll('.ranking-tabs button');
const contents = document.querySelectorAll('.ranking-content');

tabs.forEach(btn => {
  btn.addEventListener('click', () => {
    tabs.forEach(t => t.classList.remove('active'));
    btn.classList.add('active');

    contents.forEach(c => c.classList.remove('active'));
    document.getElementById(btn.dataset.target).classList.add('active');
  });
});
</script>

</body>
</html>
