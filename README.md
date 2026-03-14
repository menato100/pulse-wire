# pulse-wire
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PulseWire – Breaking News, Global Coverage & Trending Stories</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=Source+Serif+4:ital,wght@0,300;0,400;0,600;1,400&family=DM+Sans:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root {
    --ink: #1a1714;
    --ink2: #3d3830;
    --ink3: #6b6258;
    --paper: #faf8f4;
    --paper2: #f2efe9;
    --paper3: #e8e3da;
    --red: #c0392b;
    --red2: #e74c3c;
    --gold: #b8963a;
    --gold2: #d4ab52;
    --blue: #1a4a7a;
    --serif: 'Playfair Display', Georgia, serif;
    --body-serif: 'Source Serif 4', Georgia, serif;
    --sans: 'DM Sans', system-ui, sans-serif;
  }
  html { font-size: 16px; }
  body { background: var(--paper); color: var(--ink); font-family: var(--body-serif); line-height: 1.6; }

  .top-bar { background: var(--ink); color: #aaa; font-family: var(--sans); font-size: 11px; letter-spacing: .08em; padding: 6px 0; }
  .top-bar-inner { max-width: 1200px; margin: 0 auto; padding: 0 20px; display: flex; justify-content: space-between; align-items: center; }
  .top-bar a { color: #ccc; text-decoration: none; margin-left: 16px; }
  .top-bar a:hover { color: #fff; }
  .ticker { display: flex; gap: 24px; overflow: hidden; flex: 1; align-items: center; }
  .ticker-label { background: var(--red); color: #fff; padding: 1px 8px; font-size: 10px; font-weight: 600; letter-spacing: .1em; border-radius: 2px; white-space: nowrap; }

  header { border-bottom: 3px solid var(--ink); padding: 18px 0 0; background: var(--paper); }
  .header-inner { max-width: 1200px; margin: 0 auto; padding: 0 20px; }
  .header-top { display: flex; align-items: flex-end; justify-content: space-between; gap: 16px; padding-bottom: 14px; border-bottom: 1px solid var(--paper3); }
  .masthead { font-family: var(--serif); font-size: clamp(42px, 7vw, 82px); font-weight: 900; letter-spacing: -.03em; line-height: 1; color: var(--ink); }
  .masthead span { color: var(--red); }
  .header-meta { text-align: right; font-family: var(--sans); font-size: 12px; color: var(--ink3); line-height: 1.8; }
  .header-meta strong { display: block; font-size: 13px; color: var(--ink2); }
  .header-tagline { font-family: var(--body-serif); font-style: italic; font-size: 13px; color: var(--ink3); letter-spacing: .04em; }

  /* AD SLOTS — replace contents with your NetPub ad tags */
  .ad-slot { background: var(--paper2); border: 1px dashed var(--paper3); display: flex; align-items: center; justify-content: center; font-family: var(--sans); font-size: 11px; color: var(--ink3); letter-spacing: .1em; }
  .ad-slot-leaderboard { height: 90px; margin: 14px 0; }
  .ad-label { text-transform: uppercase; font-size: 10px; background: var(--paper3); padding: 2px 8px; border-radius: 2px; }

  nav { border-bottom: 2px solid var(--ink); }
  nav ul { max-width: 1200px; margin: 0 auto; padding: 0 20px; list-style: none; display: flex; gap: 0; flex-wrap: wrap; }
  nav ul li a { display: block; padding: 11px 16px; font-family: var(--sans); font-size: 13px; font-weight: 600; letter-spacing: .05em; text-decoration: none; color: var(--ink2); text-transform: uppercase; transition: color .15s; }
  nav ul li a:hover, nav ul li.active a { color: var(--red); }
  nav ul li.active a { border-bottom: 3px solid var(--red); margin-bottom: -2px; }

  .breaking-bar { background: var(--red); color: #fff; font-family: var(--sans); font-size: 12px; font-weight: 600; letter-spacing: .08em; padding: 7px 0; text-align: center; }
  .breaking-bar em { font-style: normal; background: rgba(0,0,0,.2); padding: 1px 8px; border-radius: 2px; margin-right: 10px; font-size: 10px; letter-spacing: .15em; }

  .container { max-width: 1200px; margin: 0 auto; padding: 28px 20px; }
  .grid { display: grid; grid-template-columns: 1fr 300px; gap: 40px; }
  @media (max-width: 860px) { .grid { grid-template-columns: 1fr; } }

  .section-label { font-family: var(--sans); font-size: 10px; font-weight: 600; letter-spacing: .15em; text-transform: uppercase; color: var(--red); margin-bottom: 8px; display: flex; align-items: center; gap: 8px; }
  .section-label::after { content: ''; flex: 1; height: 1px; background: var(--paper3); }

  .hero { display: grid; grid-template-columns: 3fr 2fr; gap: 32px; padding-bottom: 28px; border-bottom: 2px solid var(--ink); margin-bottom: 28px; }
  @media (max-width: 680px) { .hero { grid-template-columns: 1fr; } }

  .hero-image { width: 100%; aspect-ratio: 16/9; border: 1px solid var(--paper3); margin-bottom: 14px; overflow: hidden; }
  .hero-image-placeholder { width: 100%; height: 100%; min-height: 240px; background: linear-gradient(160deg, #d5cfc4 0%, #c8c0b2 100%); display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 8px; }
  .cat-tag { display: inline-block; background: var(--red); color: #fff; font-family: var(--sans); font-size: 10px; font-weight: 700; letter-spacing: .1em; text-transform: uppercase; padding: 3px 10px; margin-bottom: 10px; }
  .hero-headline { font-family: var(--serif); font-size: clamp(22px, 3.5vw, 34px); font-weight: 700; line-height: 1.2; color: var(--ink); margin-bottom: 10px; cursor: pointer; }
  .hero-headline:hover { color: var(--red); }
  .hero-deck { font-size: 15px; color: var(--ink2); line-height: 1.6; margin-bottom: 12px; }
  .byline { font-family: var(--sans); font-size: 12px; color: var(--ink3); }
  .byline strong { color: var(--ink2); font-weight: 600; }

  .hero-side { display: flex; flex-direction: column; gap: 18px; }
  .side-story { padding-bottom: 18px; border-bottom: 1px solid var(--paper3); }
  .side-story:last-child { border-bottom: none; }
  .side-headline { font-family: var(--serif); font-size: 16px; font-weight: 700; line-height: 1.3; color: var(--ink); cursor: pointer; margin-bottom: 5px; }
  .side-headline:hover { color: var(--red); }
  .side-deck { font-size: 13px; color: var(--ink3); line-height: 1.5; }

  .three-col { display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px; padding-bottom: 28px; border-bottom: 1px solid var(--paper3); margin-bottom: 28px; }
  @media (max-width: 680px) { .three-col { grid-template-columns: 1fr; } }

  .article-card { cursor: pointer; }
  .article-thumb { width: 100%; aspect-ratio: 16/9; background: var(--paper2); border: 1px solid var(--paper3); margin-bottom: 10px; overflow: hidden; }
  .article-thumb-inner { width: 100%; height: 100%; min-height: 120px; background: linear-gradient(135deg, var(--paper3), var(--paper2)); display: flex; align-items: center; justify-content: center; font-size: 24px; opacity: .5; }
  .article-headline { font-family: var(--serif); font-size: 17px; font-weight: 700; line-height: 1.3; color: var(--ink); margin-bottom: 6px; }
  .article-headline:hover { color: var(--red); }
  .article-deck { font-size: 13px; color: var(--ink3); line-height: 1.5; margin-bottom: 8px; }

  .trending-list { display: flex; flex-direction: column; gap: 0; margin-bottom: 28px; padding-bottom: 28px; border-bottom: 1px solid var(--paper3); }
  .trending-item { display: flex; gap: 16px; padding: 14px 0; border-bottom: 1px solid var(--paper3); }
  .trending-item:last-child { border-bottom: none; }
  .trending-num { font-family: var(--serif); font-size: 28px; font-weight: 900; color: var(--paper3); line-height: 1; min-width: 32px; }
  .trending-item:hover .trending-num { color: var(--gold2); }
  .trending-headline { font-family: var(--serif); font-size: 16px; font-weight: 700; line-height: 1.3; color: var(--ink); cursor: pointer; margin-bottom: 4px; }
  .trending-headline:hover { color: var(--red); }

  .video-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 20px; margin-bottom: 28px; }
  @media (max-width: 600px) { .video-grid { grid-template-columns: 1fr; } }
  .video-card { cursor: pointer; }
  .video-thumb { width: 100%; aspect-ratio: 16/9; background: var(--ink); display: flex; align-items: center; justify-content: center; position: relative; overflow: hidden; margin-bottom: 10px; }
  .video-thumb-bg { width: 100%; height: 100%; min-height: 120px; background: linear-gradient(135deg, #2c2823 0%, #1a1714 100%); display: flex; align-items: center; justify-content: center; }
  .play-btn { width: 44px; height: 44px; background: rgba(255,255,255,.9); border-radius: 50%; display: flex; align-items: center; justify-content: center; }
  .play-btn::after { content: ''; border-style: solid; border-width: 8px 0 8px 16px; border-color: transparent transparent transparent var(--ink); margin-left: 3px; }
  .video-headline { font-family: var(--serif); font-size: 15px; font-weight: 700; line-height: 1.3; color: var(--ink); margin-bottom: 4px; }
  .video-headline:hover { color: var(--red); }
  .video-meta { font-family: var(--sans); font-size: 11px; color: var(--ink3); }

  .sidebar-widget { margin-bottom: 28px; }
  .sidebar-title { font-family: var(--sans); font-size: 11px; font-weight: 700; letter-spacing: .12em; text-transform: uppercase; color: var(--ink2); border-bottom: 2px solid var(--ink); padding-bottom: 8px; margin-bottom: 16px; }
  .sidebar-story { padding: 12px 0; border-bottom: 1px solid var(--paper3); }
  .sidebar-story:last-child { border-bottom: none; }
  .sidebar-headline { font-family: var(--serif); font-size: 14px; font-weight: 700; line-height: 1.35; color: var(--ink); cursor: pointer; margin-bottom: 3px; }
  .sidebar-headline:hover { color: var(--red); }
  .sidebar-meta { font-family: var(--sans); font-size: 11px; color: var(--ink3); }

  .opinion-strip { display: grid; grid-template-columns: repeat(4, 1fr); gap: 20px; padding: 24px 0; border-top: 2px solid var(--ink); border-bottom: 1px solid var(--paper3); margin-bottom: 28px; }
  @media (max-width: 760px) { .opinion-strip { grid-template-columns: repeat(2,1fr); } }
  .opinion-card { padding: 16px; background: var(--paper2); border: 1px solid var(--paper3); }
  .opinion-quote { font-family: var(--serif); font-style: italic; font-size: 15px; line-height: 1.5; color: var(--ink); margin-bottom: 10px; cursor: pointer; }
  .opinion-author { font-family: var(--sans); font-size: 11px; font-weight: 600; color: var(--ink3); }

  footer { background: var(--ink); color: #888; padding: 40px 0 20px; margin-top: 40px; }
  .footer-inner { max-width: 1200px; margin: 0 auto; padding: 0 20px; }
  .footer-logo { font-family: var(--serif); font-size: 32px; font-weight: 900; color: #fff; margin-bottom: 4px; }
  .footer-logo span { color: var(--red2); }
  .footer-tagline { font-family: var(--body-serif); font-style: italic; font-size: 13px; color: #666; margin-bottom: 28px; }
  .footer-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 24px; padding-bottom: 28px; border-bottom: 1px solid #2a2724; margin-bottom: 20px; }
  @media (max-width: 640px) { .footer-grid { grid-template-columns: repeat(2,1fr); } }
  .footer-col-title { font-family: var(--sans); font-size: 10px; font-weight: 700; letter-spacing: .12em; text-transform: uppercase; color: #aaa; margin-bottom: 12px; }
  .footer-col a { display: block; font-family: var(--sans); font-size: 13px; color: #666; text-decoration: none; margin-bottom: 7px; }
  .footer-col a:hover { color: #ccc; }
  .footer-bottom { display: flex; justify-content: space-between; align-items: center; font-family: var(--sans); font-size: 11px; flex-wrap: wrap; gap: 8px; }
  .footer-bottom a { color: #555; text-decoration: none; margin-left: 16px; }
  .footer-bottom a:hover { color: #999; }
</style>
</head>
<body>

<!-- ═══════════════════════════════════════════
     TOP BAR
════════════════════════════════════════════ -->
<div class="top-bar">
  <div class="top-bar-inner">
    <div class="ticker" style="display:flex;align-items:center;gap:12px;">
      <span class="ticker-label">LIVE</span>
      <span>DOW +0.6% &nbsp;·&nbsp; S&P 500 +0.3% &nbsp;·&nbsp; NASDAQ –0.1% &nbsp;·&nbsp; Oil $82.40/bbl &nbsp;·&nbsp; Fed Meeting: Rate Decision Due Wednesday</span>
    </div>
    <div style="display:flex;gap:0;white-space:nowrap;">
      <a href="#">Sign In</a>
      <a href="#">Subscribe</a>
      <a href="#">Newsletter</a>
    </div>
  </div>
</div>

<!-- ═══════════════════════════════════════════
     HEADER
════════════════════════════════════════════ -->
<header>
  <div class="header-inner">
    <div class="header-top">
      <div>
        <div class="masthead">Pulse<span>Wire</span></div>
        <div class="header-tagline">America's Window to the World.</div>
      </div>
      <div class="header-meta">
        <strong id="hdate"></strong>
        <span>New York, NY &nbsp;·&nbsp; 54°F Partly Cloudy</span><br>
        <span>U.S. Edition &nbsp;·&nbsp; Global Coverage</span>
      </div>
    </div>

    <!-- ★ AD SLOT 1: Leaderboard 728×90 — replace with your NetPub tag ★ -->
    <div class="ad-slot ad-slot-leaderboard">
      <!-- NETPUB AD TAG HERE -->
      <span class="ad-label">Advertisement – 728×90</span>
    </div>
  </div>

  <nav>
    <ul>
      <li class="active"><a href="#">Home</a></li>
      <li><a href="#">U.S. News</a></li>
      <li><a href="#">Politics</a></li>
      <li><a href="#">World</a></li>
      <li><a href="#">Business</a></li>
      <li><a href="#">Technology</a></li>
      <li><a href="#">Health</a></li>
      <li><a href="#">Opinion</a></li>
      <li><a href="#">Video</a></li>
      <li><a href="#">More ▾</a></li>
    </ul>
  </nav>
</header>

<!-- BREAKING BANNER -->
<div class="breaking-bar">
  <em>BREAKING</em> U.S. Senate passes sweeping border security package in 67–33 bipartisan vote — live updates
</div>

<!-- ═══════════════════════════════════════════
     MAIN CONTENT
════════════════════════════════════════════ -->
<div class="container">
  <div class="section-label">Top Stories</div>

  <!-- HERO -->
  <div class="hero">
    <div class="hero-main">
      <div class="hero-image">
        <div class="hero-image-placeholder">
          <div style="font-size:40px;opacity:.4;">🏛️</div>
          <span style="font-family:var(--sans);font-size:11px;color:#888;letter-spacing:.1em;">FEATURED IMAGE 800×450</span>
        </div>
      </div>
      <span class="cat-tag">U.S. Politics</span>
      <div class="hero-headline">Senate Passes Landmark Border Security Bill as Trump Pushes for Rapid White House Signing</div>
      <div class="hero-deck">In a rare display of bipartisan cooperation, 67 senators voted to approve the most significant immigration enforcement overhaul in two decades — expanding detention capacity, fast-tracking asylum hearings, and allocating $14 billion for border infrastructure. Critics say the bill sidelines humanitarian protections.</div>
      <div class="byline"><strong>By Margaret Ellis</strong> · Washington Bureau Chief · 1 hour ago · 7 min read</div>
    </div>

    <div class="hero-side">
      <div class="side-story">
        <span class="cat-tag" style="font-size:9px;padding:2px 7px;">U.S. Economy</span>
        <div class="side-headline">Fed Signals One Rate Cut in 2026 as Inflation Edges Back Toward 2% Target</div>
        <div class="side-deck">Chair Powell struck a cautiously optimistic tone, warning that trade tariffs remain an "upside risk" to prices.</div>
        <div class="byline" style="font-size:11px;margin-top:6px;">James Whitfield · 2 hrs ago</div>
      </div>
      <div class="side-story">
        <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:var(--blue);">World</span>
        <div class="side-headline">Russia-Ukraine Ceasefire Talks Stall in Istanbul Over Territorial Guarantees</div>
        <div class="side-deck">U.S. envoys joined European mediators as both sides hardened positions on the status of four occupied regions.</div>
        <div class="byline" style="font-size:11px;margin-top:6px;">Reuters / PulseWire · 3 hrs ago</div>
      </div>
      <div class="side-story">
        <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:#5a3e8a;">Tech</span>
        <div class="side-headline">OpenAI Unveils GPT-5 With Real-Time Reasoning — Stock Surges 11% in After-Hours</div>
        <div class="side-deck">The model reportedly outperforms human experts on standardized medical and legal benchmarks, reigniting AI regulation debate in Congress.</div>
        <div class="byline" style="font-size:11px;margin-top:6px;">Sara Kim · 4 hrs ago</div>
      </div>
    </div>
  </div>

  <!-- AMERICA TODAY -->
  <div class="section-label">America Today</div>
  <div class="three-col" style="margin-bottom:28px;">
    <div class="article-card">
      <div class="article-thumb"><div class="article-thumb-inner">🗳️</div></div>
      <span class="cat-tag" style="font-size:9px;padding:2px 7px;">Politics</span>
      <div class="article-headline">2026 Midterms: Democrats Surge in Key Senate Battleground Polls</div>
      <div class="article-deck">New polling in Arizona, Pennsylvania, and Wisconsin shows Democrats within striking distance of flipping three Republican-held seats.</div>
      <div class="byline" style="font-size:11px;">Rachel Torres · 2 hrs ago · 5 min read</div>
    </div>
    <div class="article-card">
      <div class="article-thumb"><div class="article-thumb-inner">⚖️</div></div>
      <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:#1a6b3a;">Supreme Court</span>
      <div class="article-headline">Supreme Court Agrees to Hear Challenge to Social Media Content Moderation Laws</div>
      <div class="article-deck">The justices will weigh whether state laws in Texas and Florida forcing platforms to carry all speech violate the First Amendment.</div>
      <div class="byline" style="font-size:11px;">David Park · 3 hrs ago · 4 min read</div>
    </div>
    <div class="article-card">
      <div class="article-thumb"><div class="article-thumb-inner">💊</div></div>
      <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:#a0522d;">Health</span>
      <div class="article-headline">CDC Reports Measles Outbreaks in Six States — Largest in 30 Years</div>
      <div class="article-deck">Health officials link the surge to declining vaccination rates in certain school districts, calling it a "preventable public health crisis."</div>
      <div class="byline" style="font-size:11px;">Linda Foster · 4 hrs ago · 6 min read</div>
    </div>
  </div>

  <!-- MAIN + SIDEBAR -->
  <div class="grid">
    <div class="main-col">

      <!-- TRENDING -->
      <div class="section-label">Trending Globally</div>
      <div class="trending-list">
        <div class="trending-item">
          <div class="trending-num">01</div>
          <div>
            <span class="cat-tag" style="font-size:9px;padding:2px 7px;">🇺🇸 U.S.</span>
            <div class="trending-headline">Trump Signs Executive Order Withdrawing U.S. from WHO for Second Time</div>
            <div class="byline" style="font-size:11px;">18,200 reading now · 30 min ago</div>
          </div>
        </div>
        <div class="trending-item">
          <div class="trending-num">02</div>
          <div>
            <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:var(--blue);">🇨🇳 China</span>
            <div class="trending-headline">China Launches Record Naval Exercises Near Taiwan Strait, Pentagon Issues Formal Warning</div>
            <div class="byline" style="font-size:11px;">14,700 reading now · 1 hr ago</div>
          </div>
        </div>
        <div class="trending-item">
          <div class="trending-num">03</div>
          <div>
            <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:#5a3e8a;">🇺🇸 Tech</span>
            <div class="trending-headline">Tesla Stock Drops 18% After Musk Confirms He Won't Return as CEO "In Any Capacity"</div>
            <div class="byline" style="font-size:11px;">12,300 reading now · 2 hrs ago</div>
          </div>
        </div>
        <div class="trending-item">
          <div class="trending-num">04</div>
          <div>
            <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:var(--gold);">🇬🇧 UK</span>
            <div class="trending-headline">UK Prime Minister Faces No-Confidence Motion After NHS Funding Scandal Widens</div>
            <div class="byline" style="font-size:11px;">9,800 reading now · 2 hrs ago</div>
          </div>
        </div>
        <div class="trending-item">
          <div class="trending-num">05</div>
          <div>
            <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:#1a6b3a;">🇺🇸 Economy</span>
            <div class="trending-headline">U.S. Adds 312,000 Jobs in February — Unemployment Falls to 3.6%</div>
            <div class="byline" style="font-size:11px;">8,400 reading now · 3 hrs ago</div>
          </div>
        </div>
        <div class="trending-item">
          <div class="trending-num">06</div>
          <div>
            <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:#8b2020;">🇷🇺 Russia</span>
            <div class="trending-headline">Kremlin Dismisses Western Peace Plan, Says Ukraine Must Cede Territory Before Talks Resume</div>
            <div class="byline" style="font-size:11px;">6,900 reading now · 4 hrs ago</div>
          </div>
        </div>
      </div>

      <!-- ★ AD SLOT 2: In-Content 728×90 — replace with your NetPub tag ★ -->
      <div class="ad-slot" style="height:90px;margin-bottom:28px;">
        <!-- NETPUB AD TAG HERE -->
        <span class="ad-label">Advertisement – 728×90 In-Content</span>
      </div>

      <!-- AROUND THE WORLD -->
      <div class="section-label">Around the World</div>
      <div class="three-col" style="border-bottom:none;margin-bottom:28px;">
        <div class="article-card">
          <div class="article-thumb"><div class="article-thumb-inner">🇪🇺</div></div>
          <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:var(--blue);">Europe</span>
          <div class="article-headline">EU Agrees to $500B Joint Defense Fund — Germany and France Lead Push</div>
          <div class="article-deck">European leaders signed the historic defense pact in Brussels, citing an "existential shift" in the continent's security environment.</div>
          <div class="byline" style="font-size:11px;">AP / PulseWire · 1 hr ago · 5 min read</div>
        </div>
        <div class="article-card">
          <div class="article-thumb"><div class="article-thumb-inner">🇮🇳</div></div>
          <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:#b05000;">India</span>
          <div class="article-headline">India Surpasses Japan as World's Fourth-Largest Economy, IMF Data Confirms</div>
          <div class="article-deck">GDP figures show India's rapid ascent, fueled by manufacturing exports and a booming digital services sector.</div>
          <div class="byline" style="font-size:11px;">Priya Nair · 3 hrs ago · 4 min read</div>
        </div>
        <div class="article-card">
          <div class="article-thumb"><div class="article-thumb-inner">🌏</div></div>
          <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:#1a6b3a;">Climate</span>
          <div class="article-headline">Scientists Confirm 2025 Was the Hottest Year on Record — By a Wide Margin</div>
          <div class="article-deck">Global average temperatures exceeded the 1.5°C Paris threshold for the first full calendar year, according to a joint NASA-NOAA report.</div>
          <div class="byline" style="font-size:11px;">Ellen Marsh · 5 hrs ago · 6 min read</div>
        </div>
      </div>

      <!-- VIDEO -->
      <div class="section-label">Video</div>
      <div class="video-grid">
        <div class="video-card">
          <div class="video-thumb">
            <div class="video-thumb-bg"><div class="play-btn"></div></div>
          </div>
          <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:var(--red);margin-bottom:7px;display:inline-block;">Exclusive</span>
          <div class="video-headline">Inside the Senate: The 12 Hours That Passed the Border Bill</div>
          <div class="video-meta">32:18 &nbsp;·&nbsp; 224K views &nbsp;·&nbsp; 2 hours ago</div>
        </div>
        <div class="video-card">
          <div class="video-thumb">
            <div class="video-thumb-bg"><div class="play-btn"></div></div>
          </div>
          <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:var(--blue);margin-bottom:7px;display:inline-block;">World</span>
          <div class="video-headline">Taiwan Strait Crisis Explained: What the U.S. Can and Cannot Do</div>
          <div class="video-meta">18:44 &nbsp;·&nbsp; 187K views &nbsp;·&nbsp; 4 hours ago</div>
        </div>
      </div>

      <!-- OPINION -->
      <div class="section-label" style="margin-top:28px;">Opinion & Analysis</div>
      <div class="opinion-strip">
        <div class="opinion-card">
          <div class="opinion-quote">"The border bill is a win for security. Whether it's a win for America's soul is a different question entirely."</div>
          <div class="opinion-author">CARL WHITMAN &nbsp;·&nbsp; Political Editor</div>
        </div>
        <div class="opinion-card">
          <div class="opinion-quote">"The Fed's caution is warranted, but the longer they wait, the more they risk cratering the housing market."</div>
          <div class="opinion-author">DR. AMY CHEN &nbsp;·&nbsp; Economist</div>
        </div>
        <div class="opinion-card">
          <div class="opinion-quote">"GPT-5 isn't the end of jobs. But it is the end of pretending AI regulation can wait another year."</div>
          <div class="opinion-author">MARCUS REED &nbsp;·&nbsp; Tech Columnist</div>
        </div>
        <div class="opinion-card">
          <div class="opinion-quote">"7 Ways China's Taiwan Moves Are Changing U.S. Defense Spending for the Next Decade"</div>
          <div class="opinion-author">LISTICLE &nbsp;·&nbsp; 9 min read</div>
        </div>
      </div>

      <!-- MORE U.S. NEWS -->
      <div class="section-label">More U.S. News</div>
      <div class="three-col" style="border-bottom:none;">
        <div class="article-card">
          <div class="article-thumb"><div class="article-thumb-inner">🚀</div></div>
          <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:#5a3e8a;">Space</span>
          <div class="article-headline">NASA Announces Artemis III Moon Landing Pushed to 2027 Amid SpaceX Delays</div>
          <div class="article-deck">Funding shortfalls and Starship certification setbacks have forced a 14-month delay to the crewed lunar return mission.</div>
          <div class="byline" style="font-size:11px;">Tom Briggs · 5 hrs ago</div>
        </div>
        <div class="article-card">
          <div class="article-thumb"><div class="article-thumb-inner">🎓</div></div>
          <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:var(--gold);">Education</span>
          <div class="article-headline">Student Loan Forgiveness Program Blocked Again by Federal Appeals Court</div>
          <div class="article-deck">A three-judge panel ruled the administration exceeded its authority, affecting an estimated 8 million borrowers.</div>
          <div class="byline" style="font-size:11px;">Diane Foster · 6 hrs ago</div>
        </div>
        <div class="article-card">
          <div class="article-thumb"><div class="article-thumb-inner">🏘️</div></div>
          <span class="cat-tag" style="font-size:9px;padding:2px 7px;background:#1a6b3a;">Housing</span>
          <div class="article-headline">U.S. Home Sales Hit 12-Year Low as Mortgage Rates Hover Near 7%</div>
          <div class="article-deck">Economists warn of a "frozen market" as both buyers and sellers hold out — and inventory remains near historic lows.</div>
          <div class="byline" style="font-size:11px;">Kevin Marsh · 7 hrs ago</div>
        </div>
      </div>
    </div>

    <!-- ═══════════════════════════════
         SIDEBAR
    ════════════════════════════════ -->
    <aside>

      <!-- ★ AD SLOT 3: Medium Rectangle 300×250 — replace with your NetPub tag ★ -->
      <div class="ad-slot" style="width:300px;min-width:300px;height:250px;margin-bottom:24px;">
        <!-- NETPUB AD TAG HERE -->
        <span class="ad-label">Advertisement – 300×250</span>
      </div>

      <div class="sidebar-widget">
        <div class="sidebar-title">Most Read Today</div>
        <div class="sidebar-story">
          <div class="sidebar-headline">What the Border Bill Actually Does — Provision by Provision</div>
          <div class="sidebar-meta">U.S. Politics · 2.1M reads</div>
        </div>
        <div class="sidebar-story">
          <div class="sidebar-headline">OpenAI's GPT-5: Everything You Need to Know</div>
          <div class="sidebar-meta">Technology · 1.6M reads</div>
        </div>
        <div class="sidebar-story">
          <div class="sidebar-headline">China's Taiwan Drills: A Full Military Breakdown</div>
          <div class="sidebar-meta">World · 1.1M reads</div>
        </div>
        <div class="sidebar-story">
          <div class="sidebar-headline">Fed Rate Decision: What It Means for Your Mortgage, Savings, and 401(k)</div>
          <div class="sidebar-meta">Economy · 870K reads</div>
        </div>
        <div class="sidebar-story">
          <div class="sidebar-headline">Measles Outbreak Map: Is Your State Affected?</div>
          <div class="sidebar-meta">Health · 740K reads</div>
        </div>
      </div>

      <!-- ★ AD SLOT 4: Medium Rectangle 300×250 — replace with your NetPub tag ★ -->
      <div class="ad-slot" style="width:300px;min-width:300px;height:250px;margin-bottom:24px;">
        <!-- NETPUB AD TAG HERE -->
        <span class="ad-label">Advertisement – 300×250</span>
      </div>

      <!-- GLOBAL BRIEFING -->
      <div class="sidebar-widget">
        <div class="sidebar-title">Global Briefing</div>
        <div class="sidebar-story">
          <div style="font-family:var(--sans);font-size:10px;color:var(--ink3);margin-bottom:4px;">🇬🇧 UNITED KINGDOM</div>
          <div class="sidebar-headline">Keir Starmer Survives No-Confidence Vote by 11 Seats</div>
          <div class="sidebar-meta">2 hrs ago</div>
        </div>
        <div class="sidebar-story">
          <div style="font-family:var(--sans);font-size:10px;color:var(--ink3);margin-bottom:4px;">🇫🇷 FRANCE</div>
          <div class="sidebar-headline">Paris Braces for General Strike Over Pension Age Rollback</div>
          <div class="sidebar-meta">3 hrs ago</div>
        </div>
        <div class="sidebar-story">
          <div style="font-family:var(--sans);font-size:10px;color:var(--ink3);margin-bottom:4px;">🇯🇵 JAPAN</div>
          <div class="sidebar-headline">Bank of Japan Raises Rates for Third Time — Yen Jumps to 6-Month High</div>
          <div class="sidebar-meta">4 hrs ago</div>
        </div>
        <div class="sidebar-story">
          <div style="font-family:var(--sans);font-size:10px;color:var(--ink3);margin-bottom:4px;">🇧🇷 BRAZIL</div>
          <div class="sidebar-headline">Amazon Deforestation Hits 4-Year Low Under New Enforcement Push</div>
          <div class="sidebar-meta">5 hrs ago</div>
        </div>
        <div class="sidebar-story">
          <div style="font-family:var(--sans);font-size:10px;color:var(--ink3);margin-bottom:4px;">🇮🇱 MIDDLE EAST</div>
          <div class="sidebar-headline">Gaza Ceasefire Holds Into Week Three as Hostage Negotiations Resume</div>
          <div class="sidebar-meta">6 hrs ago</div>
        </div>
      </div>

      <!-- NEWSLETTER -->
      <div class="sidebar-widget" style="background:var(--ink);padding:20px;color:#ccc;">
        <div style="font-family:var(--serif);font-size:20px;font-weight:700;color:#fff;margin-bottom:6px;">PulseWire AM</div>
        <div style="font-size:13px;line-height:1.6;margin-bottom:14px;">Your 5-minute brief on America and the world — free, every morning at 6am ET.</div>
        <input type="email" placeholder="your@email.com" style="width:100%;padding:9px 12px;font-size:13px;background:#2a2724;border:1px solid #3a3530;color:#ccc;border-radius:4px;margin-bottom:8px;outline:none;">
        <button style="width:100%;background:var(--red);color:#fff;border:none;padding:9px;font-family:var(--sans);font-size:12px;font-weight:700;letter-spacing:.08em;text-transform:uppercase;cursor:pointer;border-radius:4px;">Subscribe Free</button>
      </div>

      <!-- ★ AD SLOT 5: Half-Page 300×600 — replace with your NetPub tag ★ -->
      <div class="ad-slot" style="width:300px;min-width:300px;height:600px;margin-top:24px;">
        <!-- NETPUB AD TAG HERE -->
        <span class="ad-label">Advertisement – 300×600</span>
      </div>

    </aside>
  </div>
</div>

<!-- ═══════════════════════════════════════════
     FOOTER
════════════════════════════════════════════ -->
<footer>
  <div class="footer-inner">
    <div class="footer-logo">Pulse<span>Wire</span></div>
    <div class="footer-tagline">America's Window to the World. Independent. Uncompromising.</div>
    <div class="footer-grid">
      <div class="footer-col">
        <div class="footer-col-title">Sections</div>
        <a href="#">U.S. News</a><a href="#">Politics</a><a href="#">World</a><a href="#">Business</a><a href="#">Technology</a><a href="#">Health</a>
      </div>
      <div class="footer-col">
        <div class="footer-col-title">World Desks</div>
        <a href="#">Europe</a><a href="#">Asia-Pacific</a><a href="#">Middle East</a><a href="#">Latin America</a><a href="#">Africa</a>
      </div>
      <div class="footer-col">
        <div class="footer-col-title">Services</div>
        <a href="#">Subscribe</a><a href="#">Newsletter</a><a href="#">PulseWire App</a><a href="#">Podcasts</a><a href="#">Advertise</a>
      </div>
      <div class="footer-col">
        <div class="footer-col-title">Company</div>
        <a href="#">About Us</a><a href="#">Careers</a><a href="#">Privacy Policy</a><a href="#">Terms of Use</a><a href="#">Contact</a>
      </div>
    </div>
    <div class="footer-bottom">
      <span>© 2026 PulseWire Media LLC. New York, NY. All rights reserved.</span>
      <div>
        <a href="#">Facebook</a><a href="#">Twitter/X</a><a href="#">Instagram</a><a href="#">YouTube</a><a href="#">TikTok</a>
      </div>
    </div>
  </div>
</footer>

<script>
  const d = new Date();
  document.getElementById('hdate').textContent = d.toLocaleDateString('en-US', {
    weekday: 'long', year: 'numeric', month: 'long', day: 'numeric'
  });
</script>

</body>
</html>
