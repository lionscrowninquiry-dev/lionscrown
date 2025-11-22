<!doctype html>
<html lang="ja">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>試合速報（テンプレート）</title>
  <style>
    :root{
      --lions-main:#092048;
      --hawks-main:#ffcc00;
      --bg:#ffffff;
      --card:#ffffff;
      --muted:#94a3b8;
      --score-bg: rgba(255,255,255,0.06);
    }

    *{box-sizing:border-box}
    body{font-family:system-ui,-apple-system,Segoe UI,Roboto,Helvetica,Arial,'Noto Sans JP',sans-serif;background:var(--bg);color:#000;margin:0;padding:0}

    .match-card{
      width:100%;
      max-width:900px;
      margin:16px auto;
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
      border:2px solid rgba(255,255,255,0.04);
      flex-shrink:0;
    }
    .logo img{width:100%;height:100%;object-fit:cover;display:block}
    .logo .fallback{font-weight:700;font-size:20px;color:#fff}

    .team-name{font-size:15px;font-weight:600}
    .team-sub{font-size:12px;color:var(--muted)}

    /* チームカラー反映 */
    #home-team.lions .team-name{color:var(--lions-main)}
    #home-team.hawks .team-name{color:var(--hawks-main)}
    #away-team.lions .team-name{color:var(--lions-main)}
    #away-team.hawks .team-name{color:var(--hawks-main)}

    .score{
      display:flex;
      flex-direction:row;
      align-items:center;
      justify-content:center;
      padding:10px 14px;
      border-radius:14px;
      background:var(--score-bg);
      min-width:0;
      gap:8px;
      transition:box-shadow .25s,border-color .25s;
      flex-shrink:0;
    }
    .score .runs{font-size:36px;font-weight:800;line-height:1}
    .score .label{font-size:12px;color:var(--muted)}

    .meta{
      display:flex;
      flex-direction:column;
      align-items:flex-end;
      gap:6px;
    }
    .inning{
      background:linear-gradient(90deg, rgba(255,255,255,0.03), rgba(255,255,255,0.06));
      padding:6px 10px;
      border-radius:999px;
      font-weight:600;
      font-size:13px;
      border:1px solid rgba(255,255,255,0.03);
    }
    .status{font-size:13px;color:var(--muted)}
    .time{font-size:12px;color:var(--muted)}

    @media (max-width:560px){
      .match-card{
        flex-direction:column;
        align-items:stretch;
        padding:12px;
        gap:12px;
      }
      .teams{
        flex-direction:column;
        gap:10px;
      }
      .team{
        width:100%;
        justify-content:flex-start;
      }
      .score{
        align-self:center;
        width:100%;
        justify-content:center;
        margin:8px 0;
        gap:6px;
        padding:8px 0;
      }
      .meta{
        flex-direction:row;
        justify-content:space-between;
        align-items:center;
        width:100%;
      }
      .score .runs{font-size:32px;}
      .team-name{font-size:14px;}
      .team-sub{font-size:11px;}
    }

    .game-info {
      text-align: left;
      margin-bottom: 15px;
      padding: 12px 10px;
      background-color: #ffffff;
      color: #444;
      border-radius: 10px;
      line-height:1.4;
    }
    .game-info div:first-child{font-weight:700;font-size:16px;margin-bottom:4px}
    .game-info div:last-child{font-size:14px}
  </style>
</head>
<body>

  <div class="game-info">
      <div id="stadium">■26年03月01日【オープン戦】埼玉西武 vs ソフトバンク 1回戦</div>
      <div id="start-time">@ベルーナドーム／開始予定：18:00</div>
  </div>

  <article id="game-summary" class="match-card" aria-live="polite">
    <div class="teams">
      <div class="team" id="home-team">
        <div class="logo" id="home-logo"><img id="home-logo-img" src="https://example.com/lions_logo.png" alt="Lions ロゴ" /><span class="fallback" id="home-logo-fallback">L</span></div>
        <div>
          <div class="team-name" id="home-name">埼玉西武ライオンズ</div>
          <div class="team-sub" id="home-sub">1位</div>
        </div>
      </div>

      <div class="score" role="group" aria-label="スコア">
        <div class="runs" id="home-runs">0</div>
        <div class="label">-</div>
        <div class="runs" id="away-runs">0</div>
      </div>

      <div class="team" id="away-team" style="justify-content:space-between;">
        <div>
          <div class="team-name" id="away-name">福岡ソフトバンクホークス</div>
          <div class="team-sub" id="away-sub">1位</div>
        </div>
        <div class="logo" id="away-logo"><img id="away-logo-img" src="https://example.com/hawks_logo.png" alt="Hawks ロゴ" /><span class="fallback" id="away-logo-fallback">H</span></div>
      </div>
    </div>

    <div class="meta">
      <div class="inning" id="inning">18:00~</div>
      <div class="status" id="game-status">試合前</div>
      <div class="time" id="updated-at">更新: 2026-03-01 00:00</div>
    </div>
  </article>

  <script>
    function fmtDateIso(iso){
      const d = new Date(iso);
      if (isNaN(d)) return '';
      return d.getFullYear()+ '-' + String(d.getMonth()+1).padStart(2,'0') + '-' + String(d.getDate()).padStart(2,'0')
        + ' ' + String(d.getHours()).padStart(2,'0') + ':' + String(d.getMinutes()).padStart(2,'0');
    }

    function setLogoImage(imgEl, fallbackEl, url, alt){
      if (url){
        imgEl.src = url;
        imgEl.alt = alt || '';
        imgEl.style.display = 'block';
        fallbackEl.style.display = 'none';
      } else {
        imgEl.style.display = 'none';
        fallbackEl.style.display = 'flex';
      }
    }

    function updateGame(data){
      document.getElementById('home-name').textContent = data.home.name || '';
      document.getElementById('home-sub').textContent = data.home.sub || '';
      document.getElementById('away-name').textContent = data.away.name || '';
      document.getElementById('away-sub').textContent = data.away.sub || '';

      const homeImg = document.getElementById('home-logo-img');
      const homeFallback = document.getElementById('home-logo-fallback');
      setLogoImage(homeImg, homeFallback, data.home.logoUrl, data.home.name + ' ロゴ');

      const awayImg = document.getElementById('away-logo-img');
      const awayFallback = document.getElementById('away-logo-fallback');
      setLogoImage(awayImg, awayFallback, data.away.logoUrl, data.away.name + ' ロゴ');

      document.getElementById('home-runs').textContent = (typeof data.home.runs === 'number') ? data.home.runs : data.home.runs || '';
      document.getElementById('away-runs').textContent = (typeof data.away.runs === 'number') ? data.away.runs : data.away.runs || '';

      document.getElementById('inning').textContent = data.inning || '';
      document.getElementById('game-status').textContent = data.status || '';
      document.getElementById('updated-at').textContent = '更新: ' + (data.updatedAt ? fmtDateIso(data.updatedAt) : fmtDateIso(new Date().toISOString()));

      const homeTeamEl = document.getElementById('home-team');
      const awayTeamEl = document.getElementById('away-team');
      homeTeamEl.classList.remove('lions','hawks');
      awayTeamEl.classList.remove('lions','hawks');

      if (data.home.code === 'L') homeTeamEl.classList.add('lions');
      if (data.home.code === 'H') homeTeamEl.classList.add('hawks');
      if (data.away.code === 'L') awayTeamEl.classList.add('lions');
      if (data.away.code === 'H') awayTeamEl.classList.add('hawks');
    }

    const sampleData = {
      home: {code:'L', name:'埼玉西武ライオンズ', sub:'1位', runs:0, logoUrl:'https://lions-crown.wweb.jp/img/1759836807957.webp'},
      away: {code:'H', name:'福岡ソフトバンクホークス', sub:'1位', runs:0, logoUrl:'https://lions-crown.wweb.jp/img/1759836829251.webp'},
      inning: '隅田vsモイネロ',
      status: '試合前',
      updatedAt: new Date().toISOString()
    };

    updateGame(sampleData);
  </script>
</body>
</html>
