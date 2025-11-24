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

    /* ▼ 背景の薄黒オーバーレイ */
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
    /* ★ 試合速報（新デザイン） */
    /* ======================= */

    .game-card{
      background:var(--card);
      padding:20px;
      border-radius:14px;
      box-shadow:0 2px 6px rgba(0,0,0,0.08);
      margin-bottom:25px;
    }

    /* ▼ 速報カード本体（前回提示の高品質テンプレ移植） */
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
    .logo .fallback{ font-weight:700; font-size:20px; color:#fff; }

    .team-name{ font-size:15px; font-weight:600; }
    .team-sub{ font-size:12px; color:var(--muted); }

    /* ▼ チームカラー連動 */
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
    .status{ font-size:13px; color:var(--muted); }
    .time{ font-size:12px; color:var(--muted); }

    @media(max-width:560px){
      .match-card{ flex-direction:column; align-items:stretch; }
      .score{ width:100%; }
      .meta{ flex-direction:row; justify-content:space-between; width:100%; }
    }


    /* ======================= */
    /* ★ ニュース（現状維持） */
    /* ======================= */
    .news-section{
      background:var(--card);
      padding:20px;
      border-radius:14px;
      box-shadow:0 2px 6px rgba(0,0,0,0.08);
      margin-bottom:25px;
    }


    /* ============================ */
    /* ★ TOP3（カードデザイン化） */
    /* ============================ */

    .rank-section{
      background:var(--card);
      padding:20px;
      border-radius:14px;
      box-shadow:0 2px 6px rgba(0,0,0,0.08);
      margin-bottom:25px;
    }

    .rank-cards{
      display:grid;
      grid-template-columns:repeat(auto-fill,minmax(260px,1fr));
      gap:14px;
    }

    .rank-card{
      background:#fff;
      border-radius:14px;
      padding:14px 16px;
      box-shadow:0 2px 8px rgba(0,0,0,0.05);
      border-left:6px solid var(--lions-blue);
      transition:.25s;
    }
    .rank-card:hover{
      transform:translateY(-3px);
      box-shadow:0 6px 16px rgba(0,0,0,0.12);
    }

    .rank-no{ font-size:1.2rem; font-weight:700; }
    .rank-name{ font-size:1.05rem; font-weight:700; margin:4px 0; }
    .rank-value{ font-size:0.95rem; color:#555; }

    .rank-btn{


<!-- ▼ ここから後半の統合エリア（TOP3 / フッター / スクリプト） -->
<section class="ranking-section">
  <div class="ranking-tabs">
    <button class="active" data-target="batting">打撃 TOP3</button>
    <button data-target="pitching">投球 TOP3</button>
  </div>

  <div id="batting" class="ranking-content active">
    <div class="ranking-card">
      <div class="rank-num">1</div>
      <div class="rank-info">
        <div class="player-name">山川 穂高</div>
        <div class="player-detail">打率 .320 / HR 35</div>
      </div>
    </div>
    <div class="ranking-card">
      <div class="rank-num">2</div>
      <div class="rank-info">
        <div class="player-name">森 友哉</div>
        <div class="player-detail">打率 .310 / HR 28</div>
      </div>
    </div>
    <div class="ranking-card">
      <div class="rank-num">3</div>
      <div class="rank-info">
        <div class="player-name">源田 壮亮</div>
        <div class="player-detail">打率 .305 / 盗塁 25</div>
      </div>
    </div>
  </div>

  <div id="pitching" class="ranking-content">
    <div class="ranking-card">
      <div class="rank-num">1</div>
      <div class="rank-info">
        <div class="player-name">髙橋 光成</div>
        <div class="player-detail">防御率 2.10 / 12勝</div>
      </div>
    </div>
    <div class="ranking-card">
      <div class="rank-num">2</div>
      <div class="rank-info">
        <div class="player-name">平良 海馬</div>
        <div class="player-detail">防御率 2.30 / 30H</div>
      </div>
    </div>
    <div class="ranking-card">
      <div class="rank-num">3</div>
      <div class="rank-info">
        <div class="player-name">増田 達至</div>
        <div class="player-detail">防御率 2.50 / 28S</div>
      </div>
    </div>
  </div>
</section>

<footer class="site-footer">
  <p>© Lions Crown - All Rights Reserved.</p>
</footer>

<script>
// ▼ ランキング切替
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
