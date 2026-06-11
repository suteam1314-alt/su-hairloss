[index.html.html](https://github.com/user-attachments/files/28835848/index.html.html)
<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
  <title>產後胸部緊實問卷</title>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --pink:      #c0627a;
      --pink-dark: #9e4f65;
      --pink-light:#fbeaef;
      --pink-pale: #fdf6f8;
      --border:    #f0d5db;
      --text:      #2d2026;
      --muted:     #7a6068;
      --white:     #ffffff;
      --success:   #2e7d5e;
    }

    body {
      font-family: -apple-system, "Helvetica Neue", "PingFang TC", "Microsoft JhengHei", sans-serif;
      background: var(--pink-pale);
      color: var(--text);
      min-height: 100vh;
    }

    /* ── Header ── */
    .header {
      background: var(--pink);
      color: var(--white);
      padding: 28px 20px 22px;
      text-align: center;
      position: relative;
    }
    .header::after {
      content: '';
      display: block;
      width: 48px; height: 3px;
      background: rgba(255,255,255,0.45);
      border-radius: 2px;
      margin: 14px auto 0;
    }
    .header h1 { font-size: 20px; font-weight: 700; letter-spacing: 0.04em; }
    .header p  { font-size: 13px; opacity: 0.82; margin-top: 6px; line-height: 1.6; }

    /* ── Progress bar ── */
    .progress-wrap { background: rgba(0,0,0,0.08); height: 4px; }
    .progress-bar  { height: 4px; background: rgba(255,255,255,0.7); width: 0%; transition: width 0.4s ease; }

    /* ── Layout ── */
    .form-body { padding: 16px; max-width: 500px; margin: 0 auto 40px; }

    /* ── Section cards ── */
    .section {
      background: var(--white);
      border-radius: 14px;
      padding: 20px 18px;
      margin-bottom: 14px;
      border: 1px solid var(--border);
    }
    .section-title {
      font-size: 14px;
      font-weight: 700;
      color: var(--pink);
      border-left: 3px solid var(--pink);
      padding-left: 10px;
      margin-bottom: 18px;
      letter-spacing: 0.03em;
    }
    .section-num {
      display: inline-block;
      background: var(--pink);
      color: #fff;
      font-size: 11px;
      font-weight: 700;
      border-radius: 4px;
      padding: 1px 7px;
      margin-right: 6px;
      vertical-align: middle;
    }

    /* ── Fields ── */
    .field { margin-bottom: 18px; }
    .field:last-child { margin-bottom: 0; }
    .field > label {
      display: block;
      font-size: 13px;
      font-weight: 600;
      color: var(--text);
      margin-bottom: 8px;
    }
    .req { color: #e05070; margin-left: 3px; }
    .hint { font-size: 11px; color: var(--muted); font-weight: 400; margin-left: 4px; }

    /* ── Select ── */
    select {
      width: 100%;
      padding: 11px 36px 11px 13px;
      border: 1.5px solid var(--border);
      border-radius: 10px;
      font-size: 14px;
      background: var(--pink-pale) url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%23c0627a' stroke-width='1.8' fill='none' stroke-linecap='round'/%3E%3C/svg%3E") no-repeat right 13px center;
      color: var(--text);
      appearance: none; -webkit-appearance: none;
      cursor: pointer;
      transition: border-color 0.2s;
    }
    select:focus { outline: none; border-color: var(--pink); }

    /* ── Text / Email input ── */
    input[type="text"], input[type="email"], input[type="tel"] {
      width: 100%;
      padding: 11px 13px;
      border: 1.5px solid var(--border);
      border-radius: 10px;
      font-size: 14px;
      background: var(--pink-pale);
      color: var(--text);
      transition: border-color 0.2s;
    }
    input[type="text"]:focus,
    input[type="email"]:focus { outline: none; border-color: var(--pink); }
    input::placeholder { color: #c0a8b0; }

    /* ── Radio / Checkbox ── */
    .option-group { display: flex; flex-direction: column; gap: 8px; }
    .option-group.inline { flex-direction: row; flex-wrap: wrap; gap: 8px; }

    .opt-label {
      display: flex;
      align-items: center;
      gap: 10px;
      font-size: 14px;
      color: var(--text);
      cursor: pointer;
      padding: 10px 13px;
      border: 1.5px solid var(--border);
      border-radius: 10px;
      background: var(--pink-pale);
      transition: background 0.15s, border-color 0.15s;
      user-select: none;
    }
    .opt-label:hover { background: #fdf0f3; border-color: #e8a0b0; }
    .opt-label.selected { background: var(--pink-light); border-color: var(--pink); }
    .opt-label.inline-item { padding: 8px 14px; font-size: 13px; }

    .opt-circle {
      width: 18px; height: 18px; flex-shrink: 0;
      border: 2px solid #d8b0bb;
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      transition: border-color 0.15s;
    }
    .opt-circle-inner {
      width: 9px; height: 9px;
      background: var(--pink);
      border-radius: 50%;
      opacity: 0; transform: scale(0.4);
      transition: opacity 0.15s, transform 0.15s;
    }
    .opt-label.selected .opt-circle { border-color: var(--pink); }
    .opt-label.selected .opt-circle-inner { opacity: 1; transform: scale(1); }

    .opt-square {
      width: 18px; height: 18px; flex-shrink: 0;
      border: 2px solid #d8b0bb;
      border-radius: 5px;
      display: flex; align-items: center; justify-content: center;
      transition: border-color 0.15s, background 0.15s;
    }
    .opt-square svg { opacity: 0; transition: opacity 0.15s; }
    .opt-label.selected .opt-square { border-color: var(--pink); background: var(--pink); }
    .opt-label.selected .opt-square svg { opacity: 1; }

    /* ── Scale ── */
    .scale-wrap { display: flex; gap: 8px; }
    .scale-item {
      flex: 1;
      display: flex; flex-direction: column; align-items: center; gap: 5px;
      font-size: 12px; color: var(--muted);
      cursor: pointer;
    }
    .scale-dot {
      width: 36px; height: 36px;
      border: 2px solid var(--border);
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-size: 14px; font-weight: 600; color: var(--muted);
      background: var(--pink-pale);
      transition: all 0.15s;
    }
    .scale-item.selected .scale-dot {
      background: var(--pink); border-color: var(--pink);
      color: #fff; transform: scale(1.1);
    }
    .scale-labels {
      display: flex; justify-content: space-between;
      font-size: 11px; color: var(--muted);
      margin-top: 4px; padding: 0 2px;
    }

    /* ── Divider ── */
    .divider { height: 1px; background: var(--border); margin: 18px 0; }

    /* ── Submit button ── */
    .submit-btn {
      width: 100%;
      padding: 15px;
      background: var(--pink);
      color: #fff;
      border: none;
      border-radius: 12px;
      font-size: 16px;
      font-weight: 700;
      cursor: pointer;
      letter-spacing: 0.05em;
      transition: background 0.2s, transform 0.1s;
      margin-top: 4px;
    }
    .submit-btn:hover:not(:disabled) { background: var(--pink-dark); }
    .submit-btn:active:not(:disabled) { transform: scale(0.98); }
    .submit-btn:disabled { background: #d4b0ba; cursor: not-allowed; }

    /* ── Error message ── */
    .err-msg {
      color: #c0303a; font-size: 12px;
      padding: 10px 14px;
      background: #fef0f0; border-radius: 8px; border: 1px solid #f5c0c0;
      margin-bottom: 12px; display: none;
    }

    /* ── Success screen ── */
    #success-screen {
      display: none;
      text-align: center;
      padding: 60px 24px 80px;
      max-width: 420px; margin: 0 auto;
    }
    .success-icon {
      width: 72px; height: 72px;
      background: var(--pink-light); border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      margin: 0 auto 20px;
    }
    .success-icon svg { width: 36px; height: 36px; stroke: var(--pink); }
    #success-screen h2 { font-size: 22px; color: var(--pink); margin-bottom: 10px; }
    #success-screen p  { font-size: 14px; color: var(--muted); line-height: 1.8; }
    .result-card {
      background: var(--white); border: 1px solid var(--border);
      border-radius: 12px; padding: 16px 18px;
      margin: 24px 0; text-align: left;
      font-size: 13px; line-height: 2;
      color: var(--text);
    }
    .result-card strong { color: var(--pink); }
  </style>
</head>
<body>

<div class="header">
  <h1>產後胸部緊實問卷</h1>
  <p>填寫約需 3 分鐘・完成後顯示個人化保養建議</p>
  <div class="progress-wrap"><div class="progress-bar" id="progress"></div></div>
</div>

<div id="form-wrap" class="form-body">

  <!-- 第 1 節 -->
  <div class="section">
    <div class="section-title"><span class="section-num">1</span>基本資料</div>

    <div class="field">
      <label>年齡<span class="req">*</span></label>
      <select id="age">
        <option value="">請選擇</option>
        <option value="20-25">20–25 歲</option>
        <option value="26-30">26–30 歲</option>
        <option value="31-35">31–35 歲</option>
        <option value="36-40">36–40 歲</option>
        <option value="40+">40 歲以上</option>
      </select>
    </div>

    <div class="field">
      <label>產後時間<span class="req">*</span></label>
      <select id="postpartum_period">
        <option value="">請選擇</option>
        <option value="1m內">1 個月內</option>
        <option value="1-3m">1–3 個月</option>
        <option value="3-6m">3–6 個月</option>
        <option value="6-12m">6–12 個月</option>
        <option value="1y+">1 年以上</option>
      </select>
    </div>

    <div class="field">
      <label>目前哺乳狀況<span class="req">*</span></label>
      <div class="option-group" id="breastfeeding">
        <label class="opt-label" onclick="selectRadio('breastfeeding', '親餵中', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 親餵中
        </label>
        <label class="opt-label" onclick="selectRadio('breastfeeding', '擠乳瓶餵', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 擠乳瓶餵
        </label>
        <label class="opt-label" onclick="selectRadio('breastfeeding', '已斷乳', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 已斷乳
        </label>
        <label class="opt-label" onclick="selectRadio('breastfeeding', '未哺乳', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 未哺乳
        </label>
      </div>
    </div>
  </div>

  <!-- 第 2 節 -->
  <div class="section">
    <div class="section-title"><span class="section-num">2</span>胸部外觀變化</div>

    <div class="field">
      <label>與懷孕前相比，下垂程度？<span class="req">*</span></label>
      <div class="option-group" id="sagging_level">
        <label class="opt-label" onclick="selectRadio('sagging_level', '無變化', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 沒有明顯變化
        </label>
        <label class="opt-label" onclick="selectRadio('sagging_level', '稍微下垂', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 稍微下垂，還可以接受
        </label>
        <label class="opt-label" onclick="selectRadio('sagging_level', '明顯下垂', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 明顯下垂，有些困擾
        </label>
        <label class="opt-label" onclick="selectRadio('sagging_level', '非常下垂', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 非常明顯，很不滿意
        </label>
      </div>
    </div>

    <div class="divider"></div>

    <div class="field">
      <label>上胸豐滿感變化？</label>
      <div class="option-group" id="fullness_change">
        <label class="opt-label" onclick="selectRadio('fullness_change', '更豐滿', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 更加豐滿
        </label>
        <label class="opt-label" onclick="selectRadio('fullness_change', '差不多', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 差不多
        </label>
        <label class="opt-label" onclick="selectRadio('fullness_change', '稍微縮水', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 稍微縮水、有空洞感
        </label>
        <label class="opt-label" onclick="selectRadio('fullness_change', '明顯縮水', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 明顯縮水、上胸凹陷
        </label>
      </div>
    </div>

    <div class="divider"></div>

    <div class="field">
      <label>目前皮膚狀況<span class="hint">（可複選）</span></label>
      <div class="option-group" id="skin_issues">
        <label class="opt-label" onclick="toggleCheck(this)">
          <span class="opt-square"><svg viewBox="0 0 12 10" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="1,5 4.5,9 11,1"/></svg></span> 妊娠紋（胸部）
        </label>
        <label class="opt-label" onclick="toggleCheck(this)">
          <span class="opt-square"><svg viewBox="0 0 12 10" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="1,5 4.5,9 11,1"/></svg></span> 皮膚明顯鬆弛
        </label>
        <label class="opt-label" onclick="toggleCheck(this)">
          <span class="opt-square"><svg viewBox="0 0 12 10" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="1,5 4.5,9 11,1"/></svg></span> 乾燥暗沉
        </label>
        <label class="opt-label" onclick="toggleCheck(this)">
          <span class="opt-square"><svg viewBox="0 0 12 10" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="1,5 4.5,9 11,1"/></svg></span> 色素沉澱
        </label>
        <label class="opt-label" onclick="toggleCheck(this)">
          <span class="opt-square"><svg viewBox="0 0 12 10" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="1,5 4.5,9 11,1"/></svg></span> 以上皆無
        </label>
      </div>
    </div>

    <div class="divider"></div>

    <div class="field">
      <label>整體外觀滿意度</label>
      <div class="scale-wrap" id="satisfaction">
        <div class="scale-item" onclick="selectScale('satisfaction', '1', this)">
          <div class="scale-dot">1</div>
        </div>
        <div class="scale-item" onclick="selectScale('satisfaction', '2', this)">
          <div class="scale-dot">2</div>
        </div>
        <div class="scale-item" onclick="selectScale('satisfaction', '3', this)">
          <div class="scale-dot">3</div>
        </div>
        <div class="scale-item" onclick="selectScale('satisfaction', '4', this)">
          <div class="scale-dot">4</div>
        </div>
        <div class="scale-item" onclick="selectScale('satisfaction', '5', this)">
          <div class="scale-dot">5</div>
        </div>
      </div>
      <div class="scale-labels"><span>很不滿意</span><span>非常滿意</span></div>
    </div>
  </div>

  <!-- 第 3 節 -->
  <div class="section">
    <div class="section-title"><span class="section-num">3</span>觸感自測</div>

    <div class="field">
      <label>輕壓後的回彈速度<span class="req">*</span></label>
      <div class="option-group" id="elasticity">
        <label class="opt-label" onclick="selectRadio('elasticity', '立即回彈', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 立即回彈，彈性佳
        </label>
        <label class="opt-label" onclick="selectRadio('elasticity', '1-2秒', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 1–2 秒內回彈
        </label>
        <label class="opt-label" onclick="selectRadio('elasticity', '3-5秒', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 3–5 秒緩慢回彈
        </label>
        <label class="opt-label" onclick="selectRadio('elasticity', '幾乎不回彈', this)">
          <span class="opt-circle"><span class="opt-circle-inner"></span></span> 幾乎不回彈，明顯鬆軟
        </label>
      </div>
    </div>
  </div>

  <!-- 第 4 節 -->
  <div class="section">
    <div class="section-title"><span class="section-num">4</span>保養需求</div>

    <div class="field">
      <label>希望改善的問題<span class="hint">（可複選）</span></label>
      <div class="option-group" id="improve_goals">
        <label class="opt-label" onclick="toggleCheck(this)">
          <span class="opt-square"><svg viewBox="0 0 12 10" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="1,5 4.5,9 11,1"/></svg></span> 增加緊實彈性
        </label>
        <label class="opt-label" onclick="toggleCheck(this)">
          <span class="opt-square"><svg viewBox="0 0 12 10" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="1,5 4.5,9 11,1"/></svg></span> 改善下垂
        </label>
        <label class="opt-label" onclick="toggleCheck(this)">
          <span class="opt-square"><svg viewBox="0 0 12 10" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="1,5 4.5,9 11,1"/></svg></span> 淡化妊娠紋
        </label>
        <label class="opt-label" onclick="toggleCheck(this)">
          <span class="opt-square"><svg viewBox="0 0 12 10" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="1,5 4.5,9 11,1"/></svg></span> 恢復豐滿感
        </label>
        <label class="opt-label" onclick="toggleCheck(this)">
          <span class="opt-square"><svg viewBox="0 0 12 10" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="1,5 4.5,9 11,1"/></svg></span> 改善皮膚乾燥
        </label>
      </div>
    </div>

    <div class="divider"></div>

    <div class="field">
      <label>可接受的產品預算</label>
      <select id="budget">
        <option value="">請選擇</option>
        <option value="500以下">500 元以下</option>
        <option value="500-1000">500–1,000 元</option>
        <option value="1000-2000">1,000–2,000 元</option>
        <option value="2000+">2,000 元以上</option>
      </select>
    </div>
  </div>

  <div class="err-msg" id="err-msg">請確認標示 * 的必填欄位都已填寫</div>
  <button class="submit-btn" id="submit-btn" onclick="submitForm()">送出問卷</button>

</div>

<!-- 成功畫面 -->
<div id="success-screen">
  <div style="padding:24px 16px 0;max-width:500px;margin:0 auto;">
    <div style="text-align:center;margin-bottom:20px;">
      <div style="width:64px;height:64px;background:#fbeaef;border-radius:50%;display:flex;align-items:center;justify-content:center;margin:0 auto 12px;">
        <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="#c0627a" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"/></svg>
      </div>
      <h2 style="font-size:20px;color:#c0627a;font-weight:700;margin-bottom:6px;">您的專屬保養方案</h2>
      <p style="font-size:13px;color:#7a6068;line-height:1.7;">根據您的哺乳狀況與胸部現況，為您整理以下建議</p>
    </div>
    <div id="bf-notice" style="background:#fff8e6;border:1px solid #f5d87a;border-radius:10px;padding:12px 14px;margin-bottom:14px;font-size:13px;color:#7a5a00;line-height:1.7;display:none;"></div>
    <div id="main-product" style="background:#fff;border:2px solid #c0627a;border-radius:14px;padding:18px;margin-bottom:12px;"></div>
    <div id="sub-product" style="background:#fff;border:1px solid #f0d5db;border-radius:14px;padding:18px;margin-bottom:12px;display:none;"></div>
    <div id="usage-steps" style="background:#fdf6f8;border:1px solid #f0d5db;border-radius:14px;padding:18px;margin-bottom:16px;"></div>
    <div id="caution-box" style="display:none;background:#fff3f3;border:1px solid #f5b8b8;border-radius:10px;padding:12px 14px;margin-bottom:16px;font-size:13px;color:#8b2020;line-height:1.7;"></div>
    <a href="line://ti/p/@121iagox" onclick="if(!/android|iphone|ipad|ipod/.test(navigator.userAgent.toLowerCase())){this.href='https://line.me/R/ti/p/@121iagox'}" style="display:flex;align-items:center;justify-content:center;gap:10px;background:#06C755;color:#fff;text-decoration:none;border-radius:12px;padding:14px 20px;font-size:15px;font-weight:700;letter-spacing:0.04em;margin-bottom:10px;">
      <svg width="22" height="22" viewBox="0 0 24 24" fill="white"><path d="M12 2C6.48 2 2 5.92 2 10.72c0 2.94 1.64 5.55 4.18 7.24-.18.63-.65 2.28-.74 2.63-.12.44.16.43.34.32.14-.09 2.22-1.47 3.12-2.06.68.1 1.38.15 2.1.15 5.52 0 10-3.92 10-8.28C22 5.92 17.52 2 12 2z"/></svg>
      加入 LINE 官方帳號・諮詢專業顧問
    </a>
    <p style="font-size:12px;color:#b08090;text-align:center;margin-bottom:32px;">顧問將依您的狀況提供進一步個人化建議 ✨</p>
  </div>
</div>


<script>
  const state = {
    breastfeeding: '',
    sagging_level: '',
    fullness_change: '',
    skin_issues: [],
    satisfaction: '',
    elasticity: '',
    improve_goals: [],
    budget: '',
  };

  function selectRadio(field, value, el) {
    state[field] = value;
    const group = document.getElementById(field);
    group.querySelectorAll('.opt-label').forEach(l => l.classList.remove('selected'));
    el.classList.add('selected');
    updateProgress();
  }

  function selectScale(field, value, el) {
    state[field] = value;
    const wrap = document.getElementById(field);
    wrap.querySelectorAll('.scale-item').forEach(i => i.classList.remove('selected'));
    el.classList.add('selected');
    updateProgress();
  }

  function toggleCheck(el) {
    el.classList.toggle('selected');
    updateProgress();
  }

  function updateProgress() {
    const required = ['age', 'postpartum_period', 'breastfeeding', 'sagging_level', 'elasticity'];
    let filled = 0;
    required.forEach(f => {
      if (f === 'age' || f === 'postpartum_period') {
        if (document.getElementById(f).value) filled++;
      } else if (state[f]) filled++;
    });
    document.getElementById('progress').style.width = (filled / required.length * 100) + '%';
  }

  document.getElementById('age').addEventListener('change', updateProgress);
  document.getElementById('postpartum_period').addEventListener('change', updateProgress);

  function submitForm() {
    const errMsg = document.getElementById('err-msg');
    const age = document.getElementById('age').value;
    const period = document.getElementById('postpartum_period').value;
    if (!age || !period || !state.breastfeeding || !state.sagging_level || !state.elasticity) {
      errMsg.style.display = 'block';
      errMsg.scrollIntoView({ behavior: 'smooth', block: 'center' });
      return;
    }
    errMsg.style.display = 'none';
    const btn = document.getElementById('submit-btn');
    btn.disabled = true;
    btn.textContent = '處理中…';

    const skinChecked = [...document.querySelectorAll('#skin_issues .opt-label.selected')].map(l => l.textContent.trim());
    const goalsChecked = [...document.querySelectorAll('#improve_goals .opt-label.selected')].map(l => l.textContent.trim());

    const data = {
      age, period,
      breastfeeding: state.breastfeeding,
      sagging_level: state.sagging_level,
      fullness_change: state.fullness_change,
      skin_issues: skinChecked,
      satisfaction: state.satisfaction,
      elasticity: state.elasticity,
      improve_goals: goalsChecked,
      budget: document.getElementById('budget').value,
    };

    showResult(data);
    var ua = navigator.userAgent.toLowerCase();
    var isMobile = /android|iphone|ipad|ipod/.test(ua);
    if (isMobile) {
      location.href = 'line://ti/p/@121iagox';
    } else {
      window.open('https://line.me/R/ti/p/@121iagox', '_blank');
    }
  }

  // ── 產品資料 ─────────────────────────────────────────
  const PRODUCTS = {
    cream: {
      name: '緊緻胸部霜狀產品',
      tag: '日常保養首選',
      desc: '質地清爽不黏膩，快速吸收，適合每日早晚使用。含高效緊緻成分，長期使用可改善肌膚彈性與緊實度。',
      suitable: '適合輕度鬆弛、日常維護保養、哺乳中媽媽（外用安全）',
      usage: '每日早晚各一次，取適量均勻塗抹於胸部，以螺旋方式由外向內按摩至吸收。',
      badge_color: '#e8f4fd',
      badge_text: '#1a5f8a',
    },
    mask: {
      name: '保濕緊緻行胸膜',
      tag: '密集修護推薦',
      desc: '片狀胸膜設計，高濃度活性成分直接貼敷吸收，一次 20 分鐘相當於密集保養療程，明顯改善下垂與鬆弛。',
      suitable: '適合明顯下垂、哺乳後斷乳期、皮膚鬆弛需要密集修護者',
      usage: '建議每週 2–3 次，貼敷 15–20 分鐘後取下，輕拍餘液至吸收，勿沖洗。',
      badge_color: '#fbeaef',
      badge_text: '#7b2040',
    },
  };

  // ── 依哺乳狀況決定建議邏輯 ────────────────────────────
  function buildResult(data) {
    const bf = data.breastfeeding;
    const sag = data.sagging_level;
    const elas = data.elasticity;
    const skin = data.skin_issues || [];

    let bfNotice = '';
    let mainProduct = null;
    let subProduct = null;
    let steps = [];
    let caution = '';

    // ── 哺乳中（親餵 / 擠乳）────────────────────────────
    if (bf === '親餵中' || bf === '擠乳瓶餵') {
      bfNotice = '⚠️ 您目前仍在哺乳中，建議優先選擇外用乳霜類產品，避免成分透過皮膚吸收影響乳汁。每次使用後哺乳前請先以溫水清潔胸部。';
      mainProduct = PRODUCTS.cream;

      if (sag === '明顯下垂' || sag === '非常下垂') {
        steps = [
          '每日早晚沐浴後，取 1–2 元硬幣大小的緊緻胸部霜狀產品',
          '以雙手手掌由乳房下緣向上托提，螺旋式按摩 3–5 分鐘',
          '搭配支撐型哺乳內衣，減少哺乳時的重力拉扯',
          '斷乳後可升級為保濕緊緻行胸膜進行密集修護',
        ];
        caution = '哺乳中建議暫緩使用胸膜貼片，待斷乳後再進行密集療程效果更佳且更安全。';
      } else {
        steps = [
          '每日早晚塗抹緊緻胸部霜狀產品，維持肌膚保濕與彈性',
          '按摩方向：由下往上、由外往內，每次 3 分鐘',
          '搭配足夠支撐的哺乳內衣，避免胸部下垂加劇',
        ];
      }

    // ── 已斷乳（未滿 3 個月）────────────────────────────
    } else if (bf === '已斷乳') {
      bfNotice = '✅ 斷乳後是黃金修護期！此時胸部組織正在重新穩定，搭配密集保養效果最顯著。建議兩款產品搭配使用。';
      mainProduct = PRODUCTS.mask;
      subProduct = PRODUCTS.cream;

      if (sag === '非常下垂' || elas === '幾乎不回彈') {
        steps = [
          '每週一、三、五使用保濕緊緻行胸膜，貼敷 20 分鐘',
          '其餘每日早晚搭配緊緻胸部霜狀產品按摩',
          '貼膜後黃金吸收期（30 分鐘內）避免沐浴',
          '持續 4–6 週為一個完整療程，建議照鏡記錄變化',
        ];
      } else {
        steps = [
          '每週 2 次使用保濕緊緻行胸膜做密集修護',
          '每日早晚以緊緻胸部霜狀產品維持日常保養',
          '按摩時可搭配提拉手法，加強上胸豐滿感',
        ];
      }

    // ── 未哺乳 ────────────────────────────────────────
    } else {
      if (sag === '明顯下垂' || sag === '非常下垂' || elas === '幾乎不回彈' || elas === '3-5秒') {
        mainProduct = PRODUCTS.mask;
        subProduct = PRODUCTS.cream;
        steps = [
          '每週 3 次使用保濕緊緻行胸膜，貼敷 20 分鐘做密集修護',
          '每日早晚以緊緻胸部霜狀產品按摩維持，效果加乘',
          '建議搭配胸部訓練（伏地挺身、啞鈴擴胸），強化支撐肌群',
          '連續使用 8 週觀察改善效果',
        ];
      } else {
        mainProduct = PRODUCTS.cream;
        steps = [
          '每日早晚塗抹緊緻胸部霜狀產品，維持彈性與緊實',
          '每週 1–2 次可加強使用保濕緊緻行胸膜做週期保養',
          '搭配均衡飲食與足夠水分，由內而外維持肌膚狀態',
        ];
      }
    }

    // 皮膚問題附加建議
    const skinTips = [];
    if (skin.some(s => s.includes('妊娠紋'))) skinTips.push('妊娠紋建議在使用胸膜後趁吸收期加強按摩紋路處');
    if (skin.some(s => s.includes('乾燥'))) skinTips.push('乾燥肌請先拍化妝水再使用霜狀產品，保濕效果更好');
    if (skin.some(s => s.includes('鬆弛'))) skinTips.push('鬆弛部位每次按摩時間建議延長至 5–8 分鐘');
    if (skinTips.length > 0) steps.push(...skinTips);

    return { bfNotice, mainProduct, subProduct, steps, caution };
  }

  function productHTML(product, isMain) {
    return `
      <div style="display:flex;align-items:center;gap:8px;margin-bottom:10px;">
        <span style="background:${product.badge_color};color:${product.badge_text};font-size:11px;font-weight:700;border-radius:5px;padding:3px 8px;">${isMain ? '★ 主推' : '搭配使用'}</span>
        <span style="font-size:11px;color:#999;">${product.tag}</span>
      </div>
      <div style="font-size:16px;font-weight:700;color:#2d2026;margin-bottom:6px;">${product.name}</div>
      <div style="font-size:13px;color:#5a4850;line-height:1.7;margin-bottom:8px;">${product.desc}</div>
      <div style="font-size:12px;color:#9a7080;background:#fdf6f8;border-radius:7px;padding:8px 10px;line-height:1.6;">
        <strong style="color:#c0627a;">適合：</strong>${product.suitable}
      </div>`;
  }

  function showResult(data) {
    const r = buildResult(data);

    // 哺乳提示
    const bfEl = document.getElementById('bf-notice');
    if (r.bfNotice) { bfEl.innerHTML = r.bfNotice; bfEl.style.display = 'block'; }

    // 主推產品
    document.getElementById('main-product').innerHTML = productHTML(r.mainProduct, true);

    // 搭配產品
    if (r.subProduct) {
      const subEl = document.getElementById('sub-product');
      subEl.innerHTML = productHTML(r.subProduct, false);
      subEl.style.display = 'block';
    }

    // 使用步驟
    const stepsHTML = r.steps.map((s, i) => `
      <div style="display:flex;gap:10px;align-items:flex-start;padding:6px 0;${i < r.steps.length-1 ? 'border-bottom:1px solid #f0d5db;' : ''}">
        <span style="min-width:22px;height:22px;background:#c0627a;color:#fff;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;margin-top:1px;">${i+1}</span>
        <span style="font-size:13px;color:#3d2830;line-height:1.7;">${s}</span>
      </div>`).join('');
    document.getElementById('usage-steps').innerHTML =
      `<div style="font-size:14px;font-weight:700;color:#c0627a;margin-bottom:10px;">建議使用方式</div>${stepsHTML}`;

    // 注意事項
    if (r.caution) {
      const cEl = document.getElementById('caution-box');
      cEl.innerHTML = '⚠️ 注意：' + r.caution;
      cEl.style.display = 'block';
    }

    document.getElementById('form-wrap').style.display = 'none';
    document.getElementById('success-screen').style.display = 'block';
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }
</script>
</body>
</html>
