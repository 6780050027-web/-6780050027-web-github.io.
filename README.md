# -6780050027-web-github.io.
<!doctype html>
<html lang="th">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>🏫 School Leadership Challenge — Avatar Game (Fixed)</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap');

    :root{
      --bg: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      --card: #ffffff;
      --card-dark: #f8fafc;
      --ink: #1a202c;
      --muted: #64748b;
      --primary: #6366f1;
      --primary-light: #a5b4fc;
      --success: #10b981;
      --warning: #f59e0b;
      --danger: #ef4444;
      --purple: #8b5cf6;
      --shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
      --shadow-lg: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
      --radius: 20px;
      --radius-sm: 12px;
      --border: #e2e8f0;
      --glass: rgba(255, 255, 255, 0.25);
      --glass-border: rgba(255, 255, 255, 0.18);
    }

    *{box-sizing:border-box}
    html,body{
      margin:0;padding:0;min-height:100vh;background:var(--bg);color:var(--ink);
      font-family:'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;line-height:1.6;
    }
    body::before{content:'';position:fixed;inset:0;z-index:-1;
      background:
        radial-gradient(circle at 20% 80%, rgba(120,119,198,.3) 0%, transparent 50%),
        radial-gradient(circle at 80% 20%, rgba(255,119,198,.3) 0%, transparent 50%),
        radial-gradient(circle at 40% 40%, rgba(120,219,255,.2) 0%, transparent 50%);
    }

    .container{max-width:1400px;margin:0 auto;padding:20px;position:relative;z-index:1}
    .hidden{display:none}
    .text-center{text-align:center}
    .mt-4{margin-top:16px}
    .mb-4{margin-bottom:16px}

    .header{
      background:var(--glass);backdrop-filter:blur(20px);-webkit-backdrop-filter:blur(20px);
      border:1px solid var(--glass-border);color:white;padding:32px;border-radius:var(--radius);
      margin-bottom:32px;box-shadow:var(--shadow-lg);position:relative;overflow:hidden;
    }
    .header::before{content:'';position:absolute;inset:0;
      background:linear-gradient(135deg,rgba(255,255,255,.1) 0%, rgba(255,255,255,.05) 100%);z-index:-1}
    .header h1{margin:0;font-size:2.5rem;font-weight:800;display:flex;gap:16px;align-items:center;
      background:linear-gradient(135deg,#fff 0%,#f1f5f9 100%);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
    .header .subtitle{opacity:.9;margin-top:12px;font-size:1.1rem;font-weight:400;text-shadow:0 2px 4px rgba(0,0,0,.1)}

    .game-setup{background:var(--card);border-radius:var(--radius);padding:32px;box-shadow:var(--shadow);
      margin-bottom:32px;border:1px solid rgba(255,255,255,.1);position:relative;overflow:hidden}
    .game-setup::before{content:'';position:absolute;left:0;right:0;top:0;height:4px;
      background:linear-gradient(90deg,var(--primary) 0%, var(--purple) 50%, var(--success) 100%)}

    .setup-form{display:grid;gap:20px}
    .form-group{display:flex;flex-direction:column;gap:8px}
    .form-group label{font-weight:600;color:var(--ink);font-size:1rem}
    .form-group input,.form-group select{padding:12px 16px;border:2px solid var(--border);border-radius:var(--radius-sm);font-size:1rem;background:white;transition:.2s}
    .form-group input:focus,.form-group select:focus{outline:none;border-color:var(--primary);box-shadow:0 0 0 3px rgba(99,102,241,.1)}

    .players-setup{display:grid;gap:16px}
    .player-setup{display:flex;gap:12px;align-items:center;padding:16px;background:linear-gradient(135deg,#f8fafc 0%, #f1f5f9 100%);border-radius:var(--radius-sm);border:1px solid var(--border)}
    .player-setup input{flex:1}

    .avatar-selection{display:grid;grid-template-columns:repeat(auto-fit,minmax(120px,1fr));gap:16px;margin:16px 0}
    .avatar-option{background:linear-gradient(135deg,#f8fafc 0%, #f1f5f9 100%);border:3px solid var(--border);border-radius:var(--radius-sm);padding:16px;text-align:center;cursor:pointer;transition:.3s;position:relative;overflow:hidden}
    .avatar-option::before{content:'';position:absolute;left:0;right:0;top:0;height:3px;background:var(--border);transition:.3s}
    .avatar-option:hover{border-color:var(--primary);transform:translateY(-4px);box-shadow:var(--shadow)}
    .avatar-option:hover::before{background:linear-gradient(90deg,var(--primary) 0%, var(--purple) 100%)}
    .avatar-option.selected{border-color:var(--success);background:linear-gradient(135deg,#ecfdf5 0%, #d1fae5 100%);transform:translateY(-2px);box-shadow:var(--shadow)}
    .avatar-option.selected::before{background:linear-gradient(90deg,var(--success) 0%, #22c55e 100%)}
    .avatar-emoji{font-size:3rem;margin-bottom:8px;display:block}
    .avatar-name{font-weight:600;font-size:.9rem;color:var(--ink)}

    .game-board{display:grid;gap:24px;grid-template-columns:1fr 320px;align-items:start}
    @media(max-width:1200px){.game-board{grid-template-columns:1fr}}
    .main-board{background:var(--card);border-radius:var(--radius);padding:32px;box-shadow:var(--shadow);border:1px solid rgba(255,255,255,.1)}
    .sidebar{display:flex;flex-direction:column;gap:20px;position:sticky;top:20px}

    .players-grid{display:grid;gap:20px;margin-bottom:24px}
    @media(min-width:800px){.players-grid{grid-template-columns:repeat(auto-fit,minmax(320px,1fr))}}

    .player-card{background:var(--card);border-radius:var(--radius);padding:24px;box-shadow:var(--shadow);border:2px solid transparent;transition:.3s;position:relative;overflow:hidden}
    .player-card::before{content:'';position:absolute;left:0;right:0;top:0;height:4px;background:linear-gradient(90deg,var(--muted) 0%, var(--muted) 100%);transition:.3s}
    .player-card.current-turn{border-color:var(--success);background:linear-gradient(135deg,#ecfdf5 0%, #d1fae5 100%);transform:translateY(-4px);box-shadow:var(--shadow-lg);animation:pulse 2s infinite}
    .player-card.current-turn::before{background:linear-gradient(90deg,var(--success) 0%, #22c55e 100%)}
    @keyframes pulse{0%,100%{box-shadow:var(--shadow-lg)}50%{box-shadow:0 25px 50px -12px rgba(16,185,129,.4)}}

    .player-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:16px}
    .player-info{display:flex;align-items:center;gap:12px}
    .player-avatar{font-size:2.5rem;background:linear-gradient(135deg,#f8fafc 0%, #f1f5f9 100%);border-radius:50%;width:60px;height:60px;display:flex;align-items:center;justify-content:center;border:3px solid var(--border)}
    .player-details{flex:1}
    .player-name{font-weight:700;font-size:1.2rem;margin:0}
    .player-school{color:var(--muted);font-size:.95rem;font-weight:500;margin:0}
    .player-level{display:inline-block;background:linear-gradient(135deg,var(--primary) 0%, var(--purple) 100%);color:white;border-radius:20px;padding:4px 12px;font-size:.75rem;font-weight:700;margin-top:4px}

    .dimensions{display:grid;grid-template-columns:repeat(2,1fr);gap:12px;margin-bottom:16px}
    .dimension{text-align:center;padding:16px 12px;border-radius:var(--radius-sm);background:#f8fafc;border:1px solid rgba(255,255,255,.2);position:relative;overflow:hidden}
    .dimension::before{content:'';position:absolute;left:0;right:0;top:0;height:3px}
    .dimension.student-quality{background:linear-gradient(135deg,#fef2f2 0%, #fee2e2 100%);color:#dc2626}
    .dimension.student-quality::before{background:linear-gradient(90deg,#ef4444 0%, #dc2626 100%)}
    .dimension.enrollment{background:linear-gradient(135deg,#eff6ff 0%, #dbeafe 100%);color:#2563eb}
    .dimension.enrollment::before{background:linear-gradient(90deg,#3b82f6 0%, #2563eb 100%)}
    .dimension.wellbeing{background:linear-gradient(135deg,#ecfdf5 0%, #d1fae5 100%);color:#059669}
    .dimension.wellbeing::before{background:linear-gradient(90deg,#10b981 0%, #059669 100%)}
    .dimension.reputation{background:linear-gradient(135deg,#faf5ff 0%, #e9d5ff 100%);color:#7c3aed}
    .dimension.reputation::before{background:linear-gradient(90deg,#8b5cf6 0%, #7c3aed 100%)}
    .dimension-label{font-size:.85rem;font-weight:600;margin-bottom:8px;opacity:.8}
    .dimension-score{font-size:1.5rem;font-weight:800;line-height:1}
    .progress-bar{width:100%;height:6px;background:rgba(255,255,255,.3);border-radius:3px;margin-top:8px;overflow:hidden}
    .progress-fill{height:100%;border-radius:3px;transition:width .5s ease}
    .student-quality .progress-fill{background:linear-gradient(90deg,#ef4444 0%, #dc2626 100%)}
    .enrollment .progress-fill{background:linear-gradient(90deg,#3b82f6 0%, #2563eb 100%)}
    .wellbeing .progress-fill{background:linear-gradient(90deg,#10b981 0%, #059669 100%)}
    .reputation .progress-fill{background:linear-gradient(90deg,#8b5cf6 0%, #7c3aed 100%)}

    .total-score{text-align:center;font-size:1.2rem;font-weight:700;color:var(--primary);padding:12px;background:linear-gradient(135deg,#f8fafc 0%, #f1f5f9 100%);border-radius:var(--radius-sm);border:2px solid var(--primary-light);position:relative;overflow:hidden}
    .total-score::before{content:'';position:absolute;top:0;left:-100%;width:100%;height:100%;background:linear-gradient(90deg,transparent,rgba(99,102,241,.1),transparent);transition:left .5s}
    .player-card.current-turn .total-score::before{left:100%}

    .scenario-card{background:linear-gradient(135deg,#fef2f2 0%, #fee2e2 100%);border:2px solid #f87171;border-radius:var(--radius);padding:28px;margin-bottom:24px;position:relative;overflow:hidden}
    .scenario-card::before{content:'';position:absolute;left:0;right:0;top:0;height:4px;background:linear-gradient(90deg,#ef4444 0%, #dc2626 100%)}
    .scenario-title{font-size:1.4rem;font-weight:700;margin-bottom:16px;color:#dc2626;display:flex;gap:8px;align-items:center}
    .scenario-text{line-height:1.7;margin-bottom:16px;font-size:1.05rem;color:#374151}

    .actions-panel{background:linear-gradient(135deg,#f8fafc 0%, #f1f5f9 100%);border-radius:var(--radius);padding:24px;margin-bottom:20px;border:1px solid rgba(255,255,255,.2)}
    .actions-grid{display:grid;gap:16px}
    @media(min-width:600px){.actions-grid{grid-template-columns:repeat(2,1fr)}}
    .action-card{background:white;border:2px solid var(--border);border-radius:var(--radius-sm);padding:20px;cursor:pointer;transition:.3s;position:relative;overflow:hidden}
    .action-card::before{content:'';position:absolute;left:0;right:0;top:0;height:3px;background:var(--border);transition:.3s}
    .action-card:hover{border-color:var(--primary);transform:translateY(-4px);box-shadow:var(--shadow)}
    .action-card:hover::before{background:linear-gradient(90deg,var(--primary) 0%, var(--purple) 100%)}
    .action-card.selected{border-color:var(--primary);background:linear-gradient(135deg,#f0f9ff 0%, #e0f2fe 100%);transform:translateY(-2px);box-shadow:var(--shadow)}
    .action-card.selected::before{background:linear-gradient(90deg,var(--primary) 0%, var(--purple) 100%)}
    .action-title{font-weight:700;margin-bottom:8px;font-size:1.1rem;color:var(--ink)}
    .action-effects{font-size:.9rem;color:var(--muted);font-weight:500}

    .evidence-section{margin-top:20px}
    .evidence-cards{display:grid;gap:12px;margin-top:12px}
    .evidence-card{background:white;border:2px solid var(--border);border-radius:var(--radius-sm);padding:16px;cursor:pointer;font-size:.95rem;transition:.3s;position:relative;overflow:hidden}
    .evidence-card::before{content:'';position:absolute;left:0;right:0;top:0;height:3px;background:var(--border);transition:.3s}
    .evidence-card:hover{border-color:var(--primary);transform:translateY(-3px);box-shadow:var(--shadow)}
    .evidence-card:hover::before{background:linear-gradient(90deg,var(--primary) 0%, var(--purple) 100%)}
    .evidence-card.selected{border-color:var(--success);background:linear-gradient(135deg,#ecfdf5 0%, #d1fae5 100%);transform:translateY(-2px);box-shadow:var(--shadow)}
    .evidence-card.selected::before{background:linear-gradient(90deg,var(--success) 0%, #22c55e 100%)}
    .evidence-title{font-weight:700;margin-bottom:8px;color:var(--ink);font-size:1rem}
    .evidence-detail{font-size:.9rem;color:var(--muted);margin-bottom:8px;line-height:1.5;font-weight:500}
    .evidence-citation{font-size:.8rem;color:#6b7280;font-style:italic;border-top:1px solid #f3f4f6;padding-top:8px;margin-bottom:8px}
    .evidence-bonus{display:inline-block;background:linear-gradient(135deg,var(--primary) 0%, var(--purple) 100%);color:white;border-radius:20px;padding:4px 12px;font-size:.75rem;font-weight:700;margin-top:4px;box-shadow:0 2px 4px rgba(0,0,0,.1)}

    .turn-controls{display:flex;gap:16px;justify-content:center;margin-top:24px}
    .btn{padding:16px 32px;border:none;border-radius:var(--radius-sm);font-weight:600;font-size:1rem;cursor:pointer;transition:.3s;position:relative;overflow:hidden;box-shadow:0 4px 6px -1px rgba(0,0,0,.1)}
    .btn::before{content:'';position:absolute;top:0;left:-100%;width:100%;height:100%;background:linear-gradient(90deg,transparent,rgba(255,255,255,.2),transparent);transition:left .5s}
    .btn:hover::before{left:100%}
    .btn-primary{background:linear-gradient(135deg,var(--primary) 0%, var(--purple) 100%);color:white;border:2px solid transparent}
    .btn-primary:hover{transform:translateY(-2px);box-shadow:var(--shadow)}
    .btn-secondary{background:linear-gradient(135deg,#f8fafc 0%, #f1f5f9 100%);color:var(--ink);border:2px solid var(--border)}
    .btn-secondary:hover{background:linear-gradient(135deg,#f1f5f9 0%, #e2e8f0 100%);transform:translateY(-2px);box-shadow:var(--shadow)}
    .btn:disabled{opacity:.5;cursor:not-allowed;transform:none!important;box-shadow:none!important}
    .btn:disabled::before{display:none}

    .game-info{background:var(--card);border-radius:var(--radius);padding:24px;box-shadow:var(--shadow);border:1px solid rgba(255,255,255,.1);position:relative;overflow:hidden}
    .game-info::before{content:'';position:absolute;left:0;right:0;top:0;height:4px;background:linear-gradient(90deg,var(--primary) 0%, var(--purple) 50%, var(--success) 100%)}
    .round-info{text-align:center;margin-bottom:20px}
    .round-number{font-size:2rem;font-weight:800;background:linear-gradient(135deg,var(--primary) 0%, var(--purple) 100%);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}

    .leaderboard{background:var(--card);border-radius:var(--radius);padding:24px;box-shadow:var(--shadow);border:1px solid rgba(255,255,255,.1);position:relative;overflow:hidden}
    .leaderboard::before{content:'';position:absolute;left:0;right:0;top:0;height:4px;background:linear-gradient(90deg,#ffd700 0%, #ff6b6b 50%, #4ecdc4 100%)}
    .leaderboard h3{margin:0 0 20px 0;font-size:1.3rem;font-weight:700}
    .leaderboard-item{display:flex;justify-content:space-between;align-items:center;padding:12px 16px;border-radius:var(--radius-sm);margin-bottom:8px;border:1px solid transparent}
    .leaderboard-item .player-info{gap:8px}
    .leaderboard-item .player-avatar{width:40px;height:40px;font-size:1.5rem}
    .leaderboard-item:nth-child(1){background:linear-gradient(135deg,#fef3c7 0%, #fde68a 100%);border-color:#f59e0b;color:#92400e;font-weight:700}
    .leaderboard-item:nth-child(2){background:linear-gradient(135deg,#f3f4f6 0%, #e5e7eb 100%);border-color:#9ca3af;color:#374151;font-weight:600}
    .leaderboard-item:nth-child(3){background:linear-gradient(135deg,#fed7aa 0%, #fdba74 100%);border-color:#ea580c;color:#9a3412;font-weight:600}

    .final-results{background:var(--glass);backdrop-filter:blur(20px);-webkit-backdrop-filter:blur(20px);border:1px solid var(--glass-border);color:white;border-radius:var(--radius);padding:40px;text-align:center;box-shadow:var(--shadow-lg);position:relative;overflow:hidden}
    .final-results::before{content:'';position:absolute;inset:0;background:linear-gradient(135deg,rgba(255,255,255,.1) 0%, rgba(255,255,255,.05) 100%);z-index:-1}
    .winner-announcement{font-size:2.5rem;font-weight:800;margin-bottom:20px;background:linear-gradient(135deg,#fff 0%, #f1f5f9 100%);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
    .winner-avatar{font-size:5rem;margin:20px 0;animation:celebration 2s infinite}
    @keyframes celebration{0%,100%{transform:scale(1) rotate(0)}25%{transform:scale(1.1) rotate(-5deg)}75%{transform:scale(1.1) rotate(5deg)}}
    .final-scores{display:grid;gap:16px;margin-top:24px}
    .final-score-item{background:rgba(255,255,255,.15);backdrop-filter:blur(10px);border:1px solid rgba(255,255,255,.2);border-radius:var(--radius-sm);padding:20px;transition:.2s}
    .final-score-item:hover{background:rgba(255,255,255,.2);transform:translateY(-2px)}
    .final-score-item .player-info{justify-content:flex-start;margin-bottom:12px}
    .final-score-item .player-avatar{width:50px;height:50px;font-size:2rem;background:rgba(255,255,255,.2);border-color:rgba(255,255,255,.3)}
    .achievement-badge{display:inline-block;background:linear-gradient(135deg,#ffd700 0%, #ffed4e 100%);color:#92400e;border-radius:20px;padding:6px 16px;font-size:.8rem;font-weight:700;margin:4px;box-shadow:0 2px 4px rgba(0,0,0,.1)}
  </style>
</head>
<body>
<div class="container">
  <div class="header">
    <h1>🏫 School Leadership Challenge</h1>
    <div class="subtitle">เกมจำลองการบริหารโรงเรียนเชิงวิเคราะห์ — ใช้หลักฐานเชิงประจักษ์วิเคราะห์สถานการณ์และตัดสินใจอย่างมีเหตุผล</div>
  </div>

  <!-- Game Setup -->
  <div id="gameSetup" class="game-setup">
    <h2>🎯 ตั้งค่าเกม</h2>
    <div class="setup-form">
      <div class="form-group">
        <label>โหมดการเล่น:</label>
        <select id="gameMode">
          <option value="single">🎓 Single Player (ฝึกฝน)</option>
          <option value="multi">👥 Multiplayer (แข่งขัน 2–6 คน)</option>
        </select>
      </div>

      <div id="multiplayerSetup" class="hidden">
        <div class="form-group">
          <label>จำนวนผู้เล่น:</label>
          <select id="playerCount">
            <option value="2">2 คน</option><option value="3">3 คน</option><option value="4">4 คน</option><option value="5">5 คน</option><option value="6">6 คน</option>
          </select>
        </div>
        <div class="form-group">
          <label>ข้อมูลผู้เล่น:</label>
          <div id="playersSetup" class="players-setup"></div>
        </div>
      </div>

      <div id="singlePlayerSetup" class="hidden">
        <div class="form-group">
          <label>ข้อมูลผู้เล่น:</label>
          <div class="player-setup">
            <span>ผู้เล่น:</span>
            <input type="text" placeholder="ชื่อผู้เล่น" id="singlePlayerName">
            <input type="text" placeholder="ชื่อโรงเรียน" id="singleSchoolName">
          </div>
          <div class="form-group" style="margin-top:16px">
            <label>ประเภทโรงเรียน:</label>
            <select id="singleSchoolContext">
              <option value="">🎲 สุ่มประเภทโรงเรียน</option>
            </select>
          </div>
          <!-- แก้: ไม่ฝัง template literal ตรง HTML ให้ JS เติมภายหลัง -->
          <div class="avatar-selection" id="singleAvatarSelection"></div>
        </div>
      </div>

      <div class="form-group">
        <label>จำนวนรอบ:</label>
        <select id="roundCount">
          <option value="6">6 รอบ (เร็ว)</option>
          <option value="8" selected>8 รอบ (มาตรฐาน)</option>
          <option value="10">10 รอบ (ยาว)</option>
        </select>
      </div>

      <button class="btn btn-primary" id="btnStart">🚀 เริ่มเกม</button>
    </div>
  </div>

  <!-- Game Board -->
  <div id="gameBoard" class="game-board hidden">
    <div class="main-board">
      <div id="currentScenario" class="scenario-card">
        <div class="scenario-title">🔍 สถานการณ์เชิงวิเคราะห์ — รอบที่ <span id="currentRound">1</span></div>
        <div class="scenario-text" id="scenarioText">กำลังโหลดสถานการณ์...</div>
      </div>

      <div id="playersGrid" class="players-grid"></div>

      <div id="actionSelection" class="actions-panel">
        <h3>🎯 เลือกกลยุทธ์การบริหาร (ผู้เล่น: <span id="currentPlayerName">-</span>)</h3>
        <div id="actionsGrid" class="actions-grid"></div>

        <div class="evidence-section">
          <h4>📊 เลือกหลักฐานสนับสนุน (สูงสุด 3 ใบ):</h4>
          <div id="evidenceCards" class="evidence-cards"></div>
          <div id="bonusPreview" class="hidden" style="background:#e6fffa;border:2px solid #38a169;border-radius:8px;padding:12px;margin-top:12px;">
            <div style="font-weight:bold;color:#2f855a;margin-bottom:8px;">🎯 ผลรวมโบนัสจากหลักฐาน:</div>
            <div id="bonusDetails" style="font-size:.9rem;color:#2f855a;"></div>
          </div>
        </div>

        <div class="turn-controls">
          <button id="submitTurn" class="btn btn-primary" disabled>✅ ยืนยันการตัดสินใจ</button>
          <button class="btn btn-secondary" id="btnSkip">⏭️ ข้ามรอบ</button>
        </div>
      </div>
    </div>

    <div class="sidebar">
      <div class="game-info">
        <div class="round-info">
          <div>รอบที่</div>
          <div class="round-number"><span id="roundDisplay">1</span>/<span id="maxRounds">8</span></div>
        </div>
        <div class="text-center">
          <strong>เหตุการณ์กลาง:</strong><br>
          <span id="globalEvent" class="text-muted">ปกติ</span>
        </div>
      </div>

      <div class="leaderboard">
        <h3>🏆 อันดับคะแนน</h3>
        <div id="leaderboardList"></div>
      </div>

      <div class="game-info">
        <button class="btn btn-secondary" id="btnReset" style="width:100%">🔄 เริ่มเกมใหม่</button>
      </div>
    </div>
  </div>

  <!-- Final Results -->
  <div id="finalResults" class="final-results hidden">
    <div class="winner-announcement">🎉 <span id="winnerName">ผู้ชนะ</span> ชนะ!</div>
    <div class="winner-avatar" id="winnerAvatar">👑</div>
    <div>โรงเรียน: <strong id="winnerSchool">-</strong></div>
    <div>คะแนนรวม: <strong id="winnerScore">0</strong> คะแนน</div>

    <div id="achievements" style="margin:20px 0;"></div>

    <div class="final-scores" id="finalScoresList"></div>

    <div class="mt-4">
      <button class="btn btn-primary" id="btnPlayAgain">🎮 เล่นใหม่</button>
    </div>
  </div>
</div>

<script>
// ====== Data ======
const avatarOptions = [
  { id:'principal_man', emoji:'👨‍💼', name:'ผู้อำนวยการชาย' },
  { id:'principal_woman', emoji:'👩‍💼', name:'ผู้อำนวยการหญิง' },
  { id:'teacher_man', emoji:'👨‍🏫', name:'ครูชาย' },
  { id:'teacher_woman', emoji:'👩‍🏫', name:'ครูหญิง' },
  { id:'student_man', emoji:'👨‍🎓', name:'นักเรียนชาย' },
  { id:'student_woman', emoji:'👩‍🎓', name:'นักเรียนหญิง' },
  { id:'scientist', emoji:'👨‍🔬', name:'นักวิจัย' },
  { id:'leader', emoji:'🧑‍💼', name:'ผู้นำ' },
  { id:'innovator', emoji:'👨‍💻', name:'นักนวัตกรรม' },
  { id:'mentor', emoji:'👴', name:'ที่ปรึกษา' },
  { id:'visionary', emoji:'🧙‍♂️', name:'นักวิสัยทัศน์' },
  { id:'champion', emoji:'🏆', name:'แชมเปี้ยน' }
];

const schoolContexts = [
  { id:'urban_public', name:'โรงเรียนรัฐในเมือง',
    description:'โรงเรียนรัฐบาลในเขตเมือง มีนักเรียนหลากหลาย งบประมาณจำกัด',
    characteristics:['งบประมาณจำกัด','นักเรียนหลากหลาย','แข่งขันสูง','เข้าถึงเทคโนโลยี'],
    modifiers:{ enrollment:1.2, reputation:0.9, wellbeing:0.8, studentQuality:1.0 } },
  { id:'rural_public', name:'โรงเรียนรัฐในชนบท',
    description:'โรงเรียนรัฐบาลในพื้นที่ห่างไกล ทรัพยากรจำกัด แต่ชุมชนเข้มแข็ง',
    characteristics:['ทรัพยากรจำกัด','ชุมชนเข้มแข็ง','ครูขาดแคลน','ใกล้ชิดธรรมชาติ'],
    modifiers:{ enrollment:0.7, reputation:1.1, wellbeing:1.2, studentQuality:0.8 } },
  { id:'private_premium', name:'โรงเรียนเอกชนระดับสูง',
    description:'โรงเรียนเอกชนค่าเทอมสูง มีสิ่งอำนวยความสะดวกครบครัน',
    characteristics:['งบประมาณเพียงพอ','คาดหวังสูง','สิ่งอำนวยความสะดวกดี','แข่งขันรุนแรง'],
    modifiers:{ enrollment:0.9, reputation:1.3, wellbeing:0.9, studentQuality:1.2 } },
  { id:'private_affordable', name:'โรงเรียนเอกชนราคาประหยัด',
    description:'โรงเรียนเอกชนค่าเทอมปานกลาง เน้นคุณภาพในราคาที่เข้าถึงได้',
    characteristics:['งบประมาณปานกลาง','ผู้ปกครองคาดหวัง','ต้องแข่งขัน','ยืดหยุ่น'],
    modifiers:{ enrollment:1.1, reputation:1.0, wellbeing:1.0, studentQuality:1.1 } },
  { id:'international', name:'โรงเรียนนานาชาติ',
    description:'โรงเรียนหลักสูตรนานาชาติ มีนักเรียนต่างชาติ มาตรฐานสากล',
    characteristics:['มาตรฐานสากล','หลากหลายวัฒนธรรม','ค่าใช้จ่ายสูง','คาดหวังสูงมาก'],
    modifiers:{ enrollment:0.8, reputation:1.4, wellbeing:0.8, studentQuality:1.3 } },
  { id:'vocational', name:'โรงเรียนอาชีวศึกษา',
    description:'โรงเรียนเน้นทักษะอาชีพ เชื่อมโยงกับอุตสาหกรรม',
    characteristics:['เน้นทักษะปฏิบัติ','เชื่อมโยงอุตสาหกรรม','นักเรียนหลากหลาย','โอกาสงาน'],
    modifiers:{ enrollment:1.0, reputation:0.9, wellbeing:1.1, studentQuality:0.9 } }
];

// ---- Scenarios (ตัดมาเฉพาะชุดหลักของต้นฉบับ) ----
const scenarioPool = [
  { id:'declining_engagement', title:"สัญญาณเตือนจากข้อมูลประจำวัน",
    contexts:['urban_public','rural_public','private_affordable'],
    baseText:"ข้อมูลการเข้าเรียนแสดงแนวโน้มที่น่าสนใจ: การมาสาย +12%, การขาดเรียน +8%, การส่งงานล่าช้า +15% ในช่วง 2 เดือนที่ผ่านมา",
    contextVariations:{
      urban_public:"พร้อมกับรายงานจากครูว่านักเรียนดูเหนื่อยล้าและไม่กระตือรือร้นเหมือนเดิม",
      rural_public:"ขณะที่ผู้ปกครองเริ่มสอบถามเรื่องเรียนออนไลน์และโรงเรียนในเมืองมากขึ้น",
      private_affordable:"ประกอบกับผู้ปกครองถามเรื่องผ่อนผันค่าเทอมและขอดูผลการเรียนบ่อยขึ้น"
    },
    globalEvent:"การเปลี่ยนแปลงพฤติกรรมนักเรียน"
  },
  { id:'staff_pattern_changes', title:"รูปแบบการทำงานที่เปลี่ยนไป",
    contexts:['urban_public','private_premium','international'],
    baseText:"การใช้ห้องครูลดลง 25%, จองห้องประชุมลดลง 40%, แต่อีเมลหลังเวลางานเพิ่มขึ้น 60%",
    contextVariations:{
      urban_public:"พร้อมวันลาป่วยเพิ่มขึ้นเล็กน้อย และมีการขอลดกิจกรรมพิเศษ",
      private_premium:"ครูตอบข้อความผู้ปกครองช้าลงและขอเลื่อนประชุมบ่อยขึ้น",
      international:"ครูต่างชาติสอบถามเรื่องการต่อสัญญาน้อยลงกว่าปีที่แล้ว"
    },
    globalEvent:"การเปลี่ยนแปลงพฤติกรรมบุคลากร"
  },
  { id:'digital_engagement_mystery', title:"ปริศนาการใช้เทคโนโลยี",
    contexts:['urban_public','private_affordable','rural_public'],
    baseText:"เวลาใช้งาน LMS เฉลี่ย 15 นาที/วัน (ลดจาก 45 นาที) แต่ดาวน์โหลดเนื้อหาเพิ่ม 200%",
    contextVariations:{
      urban_public:"เรียนพิเศษออนไลน์ในพื้นที่เพิ่ม 80% และถามเรื่อง Hybrid มากขึ้น",
      private_affordable:"เริ่มเปรียบเทียบค่าเทอมกับคอร์สออนไลน์และถามเรื่องลดค่าใช้จ่าย",
      rural_public:"เด็กเก่งขอใบรับรองผลเพื่อย้ายเข้าเมืองมากขึ้น"
    },
    globalEvent:"การเปลี่ยนแปลงพฤติกรรมดิจิทัล"
  },
  { id:'resource_allocation_puzzle', title:"ปริศนาการจัดสรรทรัพยากร",
    contexts:['urban_public','rural_public'],
    baseText:"งบปีใหม่ออกแล้ว แต่ 60% ต้องใช้กับ 'โครงการยกระดับคุณภาพ' ที่ยังไม่ชัดเจน",
    contextVariations:{
      urban_public:"ค่าใช้จ่ายประจำเพิ่ม 15% และมีแรงกดดันลดอัตราส่วนครู:นักเรียน",
      rural_public:"มี NGO เสนอสนับสนุนถ้าปรับวิธีการสอน"
    },
    globalEvent:"ความท้าทายการจัดการทรัพยากร"
  },
  { id:'performance_paradox', title:"ปรากฏการณ์ผลการดำเนินงาน",
    contexts:['urban_public','rural_public','private_premium'],
    baseText:"คะแนนมาตรฐานเพิ่ม 8% แต่ความพึงพอใจครูลด 12% และการมีส่วนร่วมผู้ปกครองลด 18%",
    contextVariations:{
      urban_public:"ถูกกดดันให้ปรับอันดับและเน้นสอบมากขึ้น",
      rural_public:"นักเรียนเก่งสนใจย้ายเข้าเมือง แต่นักเรียนทั่วไปยังผูกพัน",
      private_premium:"ผู้ปกครองอยากได้อันดับดีขึ้นแต่ยังอยากให้เด็กมีความสุข"
    },
    globalEvent:"ความท้าทายการวัดผล"
  }
];

// ---- Actions ----
const baseActions = [
  { id:'invest_teachers', title:'👨‍🏫 ลงทุนพัฒนาครู', description:'อบรม/สวัสดิการ/ลดภาระงาน',
    effects:{ studentQuality:4, enrollment:-1, wellbeing:5, reputation:2 }, cost:'งบประมาณสูง', tradeoff:'ลดรับใหม่เพื่ออัตราส่วน' },
  { id:'new_curriculum', title:'📚 สร้างหลักสูตรใหม่', description:'ทันสมัย เน้นทักษะศตวรรษที่ 21',
    effects:{ studentQuality:5, enrollment:3, wellbeing:-2, reputation:3 }, cost:'เวลาและทรัพยากร', tradeoff:'ภาระครูช่วงเปลี่ยน' },
  { id:'pr_marketing', title:'📢 ประชาสัมพันธ์โรงเรียน', description:'แคมเปญ/ชุมชน/โซเชียล',
    effects:{ studentQuality:-1, enrollment:5, wellbeing:-2, reputation:4 }, cost:'งบและเวลาครู', tradeoff:'เวลาพัฒนาการสอนลด' },
  { id:'technology_upgrade', title:'💻 อัพเกรดเทคโนโลยี', description:'ระบบ/อุปกรณ์/บริหาร',
    effects:{ studentQuality:3, enrollment:2, wellbeing:-1, reputation:3 }, cost:'งบสูงมาก', tradeoff:'ครูต้องเรียนรู้ระบบ' },
  { id:'student_support', title:'🎯 เสริมสร้างผู้เรียน', description:'โปรแกรมพิเศษ/กิจกรรม/แนะแนว',
    effects:{ studentQuality:4, enrollment:1, wellbeing:2, reputation:2 }, cost:'เวลาและบุคลากร', tradeoff:'—' },
  { id:'community_engagement', title:'🤝 เชื่อมโยงชุมชน', description:'เครือข่าย/โครงการร่วม',
    effects:{ studentQuality:2, enrollment:3, wellbeing:1, reputation:4 }, cost:'เวลาประสานงาน', tradeoff:'—' },
  { id:'cost_cutting', title:'💰 ลดค่าใช้จ่าย', description:'ปรับลดงบ/ประหยัด',
    effects:{ studentQuality:-2, enrollment:-3, wellbeing:-3, reputation:-1 }, cost:'เสี่ยงคุณภาพ', tradeoff:'ลดคุณภาพเพื่ออยู่รอด' },
  { id:'selective_admission', title:'🎯 คัดเลือกนักเรียน', description:'เพิ่มเกณฑ์รับ',
    effects:{ studentQuality:5, enrollment:-2, wellbeing:1, reputation:3 }, cost:'การเข้าถึง', tradeoff:'เด็กด้อยโอกาสลดลง' }
];

// ---- Evidence Pool (ตัดให้พอใช้งานและคงหมวดหมู่) ----
const evidencePool = [
  { id:'research_data', text:'📊 วิจัยพัฒนาครู', detail:'พัฒนาครูเพิ่มผลสัมฤทธิ์ ~23%', citation:'Darling-Hammond (2017)', bonus:3, categories:['teacher','quality'], contexts:['urban_public','rural_public','private_premium'] },
  { id:'neuroscience_research', text:'🧠 Active Learning', detail:'เพิ่มการจดจำ ~67%', citation:'Freeman et al. (2014)', bonus:4, categories:['innovation','quality'], contexts:['private_premium','international','urban_public'] },
  { id:'wellbeing_research', text:'😊 งานวิจัยความสุขครู', detail:'ความสุขครูสัมพันธ์ผลการสอน', citation:'Klusmann et al. (2016)', bonus:3, categories:['wellbeing','teacher'], contexts:['rural_public','private_affordable','urban_public'] },
  { id:'assessment_data', text:'📈 ใช้ข้อมูลประเมิน', detail:'Using assessment data ↑ผลสัมฤทธิ์', citation:'Black & Wiliam (2018)', bonus:3, categories:['quality','management'], contexts:['urban_public','private_premium','international'] },
  { id:'academic_standards', text:'🎓 มาตรฐานสากล', detail:'เพิ่มความเชื่อมั่นผู้ปกครอง', citation:'OECD (2019)', bonus:3, categories:['quality','reputation'], contexts:['international','private_premium','urban_public'] },
  { id:'parent_feedback', text:'👨‍👩‍👧‍👦 ผู้ปกครองมีส่วนร่วม', detail:'ช่วยผลลัพธ์และความไว้วางใจ', citation:'Henderson & Mapp (2002)', bonus:2, categories:['community','quality'], contexts:['rural_public','private_affordable','urban_public'] },
  { id:'budget_analysis', text:'💰 วิเคราะห์งบประมาณ', detail:'จัดสรรดี ↑คุณภาพ', citation:'Baker (2016)', bonus:2, categories:['finance','management'], contexts:['urban_public','rural_public','private_affordable'] },
  { id:'technology_trends', text:'🔬 เทคโนโลยีเพื่อการเรียน', detail:'ใช้เหมาะสม ↑ผลการเรียน', citation:'Clark & Mayer (2016)', bonus:3, categories:['technology','quality'], contexts:['private_premium','international','urban_public'] },
  { id:'community_needs', text:'🏘️ ความต้องการชุมชน', detail:'ตอบสนองชุมชน ↑การสนับสนุน', citation:'Epstein (2018)', bonus:2, categories:['community','support'], contexts:['rural_public','urban_public','private_affordable'] },
  { id:'accreditation_standards', text:'🏆 มาตรฐานรับรอง', detail:'↑ความเชื่อมั่น/ภาพลักษณ์', citation:'Eaton (2015)', bonus:4, categories:['accreditation','reputation'], contexts:['international','private_premium'] },
];

// ====== State ======
const gameState = {
  mode:'single',
  players:[],
  currentPlayerIndex:0,
  currentRound:1,
  maxRounds:8,
  selectedAction:null,
  selectedEvidence:[],
  currentScenarios:[], // per round: [ per player scenario ]
  usedScenariosByContext:{}, // { [contextId]: Set<string> }
  actions: baseActions,
  evidencePool: evidencePool
};

// ====== Helpers ======
const $ = sel => document.querySelector(sel);
function shuffle(arr){ return [...arr].sort(()=>Math.random()-0.5); }
function clamp(n,min,max){ return Math.max(min, Math.min(max,n)); }

// Mapping evidence categories -> dimensions
const evidenceToDims = {
  quality:['studentQuality'],
  teacher:['wellbeing','studentQuality'],
  community:['reputation','enrollment'],
  support:['wellbeing','reputation'],
  technology:['studentQuality','reputation'],
  innovation:['studentQuality','reputation'],
  finance:['enrollment','reputation'],
  management:['studentQuality'],
  accreditation:['reputation']
};

// ====== UI Setup Handlers ======
$('#gameMode').addEventListener('change', e=>{
  const multi = $('#multiplayerSetup'), single = $('#singlePlayerSetup');
  if(e.target.value==='multi'){ multi.classList.remove('hidden'); single.classList.add('hidden'); updatePlayersSetup(); }
  else { multi.classList.add('hidden'); single.classList.remove('hidden'); updateSinglePlayerSetup(); }
});
$('#playerCount').addEventListener('change', updatePlayersSetup);
$('#btnStart').addEventListener('click', startGame);
$('#btnReset').addEventListener('click', resetGame);
$('#btnPlayAgain').addEventListener('click', resetGame);
$('#submitTurn').addEventListener('click', submitTurn);
$('#btnSkip').addEventListener('click', skipTurn);

function updateSinglePlayerSetup(){
  // contexts
  const sel = $('#singleSchoolContext');
  sel.innerHTML = `<option value="">🎲 สุ่มประเภทโรงเรียน</option>` +
    schoolContexts.map(c=>`<option value="${c.id}">${c.name} - ${c.description}</option>`).join('');
  // avatars
  const wrap = $('#singleAvatarSelection');
  wrap.innerHTML = avatarOptions.map(a=>`
    <div class="avatar-option" data-avatar="${a.id}">
      <span class="avatar-emoji">${a.emoji}</span>
      <div class="avatar-name">${a.name}</div>
    </div>`).join('');
  wrap.querySelectorAll('.avatar-option').forEach(el=>{
    el.addEventListener('click', ()=>{
      wrap.querySelectorAll('.avatar-option').forEach(x=>x.classList.remove('selected'));
      el.classList.add('selected');
      const id = el.getAttribute('data-avatar');
      const obj = avatarOptions.find(v=>v.id===id);
      window.selectedSingleAvatar = { id: obj.id, emoji: obj.emoji };
    });
  });
  // default select first
  setTimeout(()=>{
    const first = wrap.querySelector('.avatar-option');
    if(first){ first.click(); }
  },0);
}

function updatePlayersSetup(){
  const count = parseInt($('#playerCount').value||'2');
  const container = $('#playersSetup');
  container.innerHTML = '';
  for(let i=0;i<count;i++){
    const div = document.createElement('div');
    div.className = 'player-setup';
    div.innerHTML = `
      <span>ผู้เล่น ${i+1}:</span>
      <input type="text" placeholder="ชื่อผู้เล่น" id="playerName${i}">
      <input type="text" placeholder="ชื่อโรงเรียน" id="schoolName${i}">
      <div class="form-group" style="margin-top:8px;">
        <select id="schoolContext${i}">
          <option value="">🎲 สุ่มประเภทโรงเรียน</option>
          ${schoolContexts.map(c=>`<option value="${c.id}">${c.name}</option>`).join('')}
        </select>
      </div>
      <div class="avatar-selection" id="avatarSelection${i}">
        ${avatarOptions.map(a=>`
          <div class="avatar-option" data-avatar="${a.id}">
            <span class="avatar-emoji">${a.emoji}</span>
            <div class="avatar-name">${a.name}</div>
          </div>`).join('')}
      </div>
    `;
    container.appendChild(div);
    // add avatar listeners
    div.querySelectorAll('.avatar-option').forEach(opt=>{
      opt.addEventListener('click', ()=>{
        div.querySelectorAll('.avatar-option').forEach(x=>x.classList.remove('selected'));
        opt.classList.add('selected');
        const id = opt.getAttribute('data-avatar');
        const obj = avatarOptions.find(v=>v.id===id);
        if(!window.selectedAvatars) window.selectedAvatars = {};
        window.selectedAvatars[i] = { id: obj.id, emoji: obj.emoji };
      });
    });
    // default
    setTimeout(()=>{ const first = div.querySelector('.avatar-option'); if(first) first.click(); },0);
  }
}

// ====== Scenario / Evidence Logic ======
function getRandomSchoolContext(){ return schoolContexts[Math.floor(Math.random()*schoolContexts.length)]; }

function getScenarioForPlayer(playerContext){
  const ctxId = playerContext.id;
  if(!gameState.usedScenariosByContext[ctxId]) gameState.usedScenariosByContext[ctxId] = new Set();
  const used = gameState.usedScenariosByContext[ctxId];

  const allForCtx = scenarioPool.filter(s=>s.contexts.includes(ctxId));
  const available = allForCtx.filter(s=>!used.has(s.id));
  const pickFrom = available.length ? available : allForCtx;
  const pick = pickFrom[Math.floor(Math.random()*pickFrom.length)];
  used.add(pick.id);
  return pick;
}

function getEvidenceForScenario(playerContext){
  const relevant = gameState.evidencePool.filter(e=>e.contexts.includes(playerContext.id));
  const shuffled = shuffle(relevant);
  return shuffled.slice(0, Math.floor(Math.random()*3)+6); // 6–8 ใบ
}

// ====== Game Flow ======
function startGame(){
  const mode = $('#gameMode').value;
  const rounds = parseInt($('#roundCount').value||'8');
  gameState.mode = mode;
  gameState.maxRounds = rounds;
  gameState.players = [];
  gameState.currentScenarios = [];
  gameState.usedScenariosByContext = {};
  gameState.currentPlayerIndex = 0;
  gameState.currentRound = 1;
  gameState.selectedAction = null;
  gameState.selectedEvidence = [];

  if(mode==='single'){
    const name = $('#singlePlayerName').value || 'ผู้เล่น';
    const school = $('#singleSchoolName').value || 'โรงเรียนของฉัน';
    const ctxId = $('#singleSchoolContext').value;
    const context = ctxId ? schoolContexts.find(c=>c.id===ctxId) : getRandomSchoolContext();
    const avatar = window.selectedSingleAvatar || avatarOptions[0];

    gameState.players.push({
      name, school,
      avatar: avatar.emoji, avatarId: avatar.id,
      context,
      scores:{
        studentQuality: Math.round(50*context.modifiers.studentQuality),
        enrollment: Math.round(50*context.modifiers.enrollment),
        wellbeing: Math.round(50*context.modifiers.wellbeing),
        reputation: Math.round(50*context.modifiers.reputation)
      },
      level:1, achievements:[]
    });
  }else{
    const count = parseInt($('#playerCount').value||'2');
    for(let i=0;i<count;i++){
      const name = ($('#playerName'+i).value)||`ผู้เล่น ${i+1}`;
      const school = ($('#schoolName'+i).value)||`โรงเรียน ${i+1}`;
      const ctxId = ($('#schoolContext'+i).value);
      const context = ctxId ? schoolContexts.find(c=>c.id===ctxId) : getRandomSchoolContext();
      const avatar = (window.selectedAvatars && window.selectedAvatars[i]) ? window.selectedAvatars[i] : avatarOptions[i%avatarOptions.length];

      gameState.players.push({
        name, school,
        avatar: avatar.emoji, avatarId: avatar.id,
        context,
        scores:{
          studentQuality: Math.round(50*context.modifiers.studentQuality),
          enrollment: Math.round(50*context.modifiers.enrollment),
          wellbeing: Math.round(50*context.modifiers.wellbeing),
          reputation: Math.round(50*context.modifiers.reputation)
        },
        level:1, achievements:[]
      });
    }
  }

  // Switch views
  $('#gameSetup').classList.add('hidden');
  $('#gameBoard').classList.remove('hidden');

  // Init order: load scenarios -> update displays
  loadCurrentScenario();
  updateGameDisplay();
  updatePlayersGrid();
  updateActionSelection();
}

function updateGameDisplay(){
  $('#currentRound').textContent = gameState.currentRound;
  $('#roundDisplay').textContent = gameState.currentRound;
  $('#maxRounds').textContent = gameState.maxRounds;

  const roundArr = gameState.currentScenarios[gameState.currentRound-1] || [];
  const curSc = roundArr[gameState.currentPlayerIndex];
  $('#globalEvent').textContent = curSc ? curSc.globalEvent : 'ปกติ';
}

function loadCurrentScenario(){
  if(!gameState.currentScenarios[gameState.currentRound-1]){
    gameState.currentScenarios[gameState.currentRound-1] = [];
    gameState.players.forEach((player, idx)=>{
      const sc = getScenarioForPlayer(player.context);
      const contextualText = `${sc.baseText} ${sc.contextVariations[player.context.id]||''}`.trim();
      gameState.currentScenarios[gameState.currentRound-1][idx] = {
        ...sc,
        contextualText,
        evidence: getEvidenceForScenario(player.context)
      };
    });
  }
  const cur = gameState.currentScenarios[gameState.currentRound-1][gameState.currentPlayerIndex];
  if(cur){
    $('#scenarioText').innerHTML = `
      <div style="background:linear-gradient(135deg,#f8fafc 0%,#f1f5f9 100%);border:2px solid #e2e8f0;border-radius:12px;padding:16px;margin-bottom:20px;">
        <div style="display:flex;align-items:center;gap:8px;margin-bottom:12px;"><span style="font-size:1.2rem;">🏫</span><strong style="color:#1a202c;">บริบทโรงเรียนของคุณ:</strong></div>
        <div style="margin-bottom:8px;"><strong style="color:#4a5568;">${gameState.players[gameState.currentPlayerIndex].context.name}</strong></div>
        <div style="font-size:.9rem;color:#666;margin-bottom:12px;line-height:1.5;">${gameState.players[gameState.currentPlayerIndex].context.description}</div>
        <div style="display:flex;flex-wrap:wrap;gap:6px;">
          ${gameState.players[gameState.currentPlayerIndex].context.characteristics.map(ch=>`<span style="background:#e2e8f0;color:#4a5568;padding:4px 8px;border-radius:6px;font-size:.8rem;font-weight:500;">${ch}</span>`).join('')}
        </div>
      </div>
      <div style="background:linear-gradient(135deg,#fef2f2 0%,#fee2e2 100%);border:2px solid #f87171;border-radius:12px;padding:20px;">
        <div style="display:flex;align-items:center;gap:8px;margin-bottom:16px;"><span style="font-size:1.2rem;">📊</span><strong style="color:#dc2626;">สถานการณ์ที่ต้องวิเคราะห์:</strong></div>
        <div style="font-size:1.05rem;line-height:1.6;color:#374151;">${cur.contextualText}</div>
      </div>`;
  }
}

function updatePlayersGrid(){
  const container = $('#playersGrid');
  container.innerHTML = '';
  gameState.players.forEach((p, idx)=>{
    const isTurn = idx===gameState.currentPlayerIndex;
    const total = Object.values(p.scores).reduce((a,b)=>a+b,0);
    p.level = Math.floor(total/50)+1;

    const el = document.createElement('div');
    el.className = `player-card ${isTurn?'current-turn':''}`;
    el.innerHTML = `
      <div class="player-header">
        <div class="player-info">
          <div class="player-avatar">${p.avatar}</div>
          <div class="player-details">
            <div class="player-name">${p.name}</div>
            <div class="player-school">${p.school}</div>
            <div style="font-size:.8rem;color:#666;margin:2px 0;">${p.context.name}</div>
            <div class="player-level">Level ${p.level}</div>
          </div>
        </div>
        ${isTurn?'<span style="color:#38a169;font-weight:bold;">🎯 รอบของคุณ</span>':''}
      </div>
      <div class="dimensions">
        ${renderDim('student-quality','🎓 คุณภาพผู้เรียน',p.scores.studentQuality)}
        ${renderDim('enrollment','👥 จำนวนผู้เรียน',p.scores.enrollment)}
        ${renderDim('wellbeing','😊 ความสุขครู',p.scores.wellbeing)}
        ${renderDim('reputation','🌟 ชื่อเสียง',p.scores.reputation)}
      </div>
      <div class="total-score">รวม: ${total} คะแนน</div>`;
    container.appendChild(el);
  });
  updateLeaderboard();
  function renderDim(css,label,val){
    return `<div class="dimension ${css}">
      <div class="dimension-label">${label}</div>
      <div class="dimension-score">${val}</div>
      <div class="progress-bar"><div class="progress-fill" style="width:${val}%"></div></div>
    </div>`;
  }
}

function updateActionSelection(){
  const currentPlayer = gameState.players[gameState.currentPlayerIndex];
  $('#currentPlayerName').textContent = `${currentPlayer.name} (${currentPlayer.context.name})`;

  // Actions
  const actionsWrap = $('#actionsGrid'); actionsWrap.innerHTML='';
  gameState.actions.forEach(a=>{
    const m = {
      studentQuality: Math.round(a.effects.studentQuality * currentPlayer.context.modifiers.studentQuality),
      enrollment: Math.round(a.effects.enrollment * currentPlayer.context.modifiers.enrollment),
      wellbeing: Math.round(a.effects.wellbeing * currentPlayer.context.modifiers.wellbeing),
      reputation: Math.round(a.effects.reputation * currentPlayer.context.modifiers.reputation)
    };
    const card = document.createElement('div');
    card.className='action-card';
    card.dataset.actionId=a.id;
    card.innerHTML=`
      <div class="action-title">${a.title}</div>
      <div style="font-size:.9rem;margin:4px 0;">${a.description}</div>
      <div class="action-effects">
        ผลกระทบ (ตามบริบท): 🎓${fmt(m.studentQuality)}  👥${fmt(m.enrollment)}  😊${fmt(m.wellbeing)}  🌟${fmt(m.reputation)}
      </div>
      <div style="font-size:.8rem;color:#d69e2e;margin-top:4px;">ต้นทุน: ${a.cost}</div>
      <div style="font-size:.8rem;color:#666;margin-top:4px;font-style:italic;">${a.tradeoff}</div>`;
    card.addEventListener('click', ()=>selectAction(a.id));
    actionsWrap.appendChild(card);
  });

  // Evidence (scenario-specific)
  const evWrap = $('#evidenceCards'); evWrap.innerHTML='';
  const curSc = gameState.currentScenarios[gameState.currentRound-1][gameState.currentPlayerIndex];
  (curSc?.evidence||[]).forEach(ev=>{
    const el = document.createElement('div');
    el.className='evidence-card';
    el.dataset.evidenceId=ev.id;
    el.innerHTML = `
      <div class="evidence-title">${ev.text}</div>
      <div class="evidence-detail">${ev.detail}</div>
      <div class="evidence-citation">${ev.citation}</div>
      <div class="evidence-bonus">โบนัส +${ev.bonus}</div>`;
    el.addEventListener('click', ()=>selectEvidence(ev.id));
    evWrap.appendChild(el);
  });

  // reset selection
  gameState.selectedAction=null;
  gameState.selectedEvidence=[];
  updateBonusPreview();
  updateSubmitButton();

  function fmt(n){ return (n>0?'+':'')+n; }
}

function selectAction(actionId){
  document.querySelectorAll('.action-card').forEach(c=>c.classList.remove('selected'));
  document.querySelector(`.action-card[data-action-id="${actionId}"]`)?.classList.add('selected');
  gameState.selectedAction = actionId;
  updateBonusPreview();
  updateSubmitButton();
}

function selectEvidence(evidenceId){
  const card = document.querySelector(`.evidence-card[data-evidence-id="${evidenceId}"]`);
  if(gameState.selectedEvidence.includes(evidenceId)){
    gameState.selectedEvidence = gameState.selectedEvidence.filter(id=>id!==evidenceId);
    card.classList.remove('selected');
  }else if(gameState.selectedEvidence.length<3){
    gameState.selectedEvidence.push(evidenceId);
    card.classList.add('selected');
  }
  updateBonusPreview();
  updateSubmitButton();
}

function updateBonusPreview(){
  const box = $('#bonusPreview'), details = $('#bonusDetails');
  if(gameState.selectedEvidence.length===0){ box.classList.add('hidden'); return; }
  box.classList.remove('hidden');

  const curSc = gameState.currentScenarios[gameState.currentRound-1][gameState.currentPlayerIndex];
  const available = curSc?.evidence||[];
  let total = 0;
  let text = '';
  gameState.selectedEvidence.forEach((id, i)=>{
    const ev = available.find(e=>e.id===id);
    if(ev){ total += ev.bonus; text += `${i? ' + ': ''}${ev.bonus} (${ev.text.replace(/^[^\wก-๙]+/,'')})`; }
  });
  text += ` = รวม ${total} คะแนน`;
  details.textContent = text;
}

function updateSubmitButton(){ $('#submitTurn').disabled = !gameState.selectedAction; }

// Apply evidence bonus by category → related dimensions
function applyEvidenceBonus(modifiedEffects, selectedEvidenceObjects){
  const bonus = { studentQuality:0, enrollment:0, wellbeing:0, reputation:0 };
  selectedEvidenceObjects.forEach(ev=>{
    (ev.categories||[]).forEach(cat=>{
      const dims = evidenceToDims[cat]||[];
      const add = Math.ceil(ev.bonus / (dims.length||1));
      dims.forEach(d=> bonus[d] += add);
    });
  });
  // Add bonus only to positive-effect dimensions (ตรรกะ: เสริมสิ่งที่กำลังผลักดัน)
  for(const k in bonus){ if(modifiedEffects[k]>0) modifiedEffects[k] += bonus[k]; }
  return modifiedEffects;
}

function submitTurn(){
  if(!gameState.selectedAction) return;

  const player = gameState.players[gameState.currentPlayerIndex];
  const action = gameState.actions.find(a=>a.id===gameState.selectedAction);

  // base effects (context-adjusted)
  let eff = {
    studentQuality: Math.round(action.effects.studentQuality * player.context.modifiers.studentQuality),
    enrollment: Math.round(action.effects.enrollment * player.context.modifiers.enrollment),
    wellbeing: Math.round(action.effects.wellbeing * player.context.modifiers.wellbeing),
    reputation: Math.round(action.effects.reputation * player.context.modifiers.reputation)
  };

  // evidence bonus by mapping
  const curSc = gameState.currentScenarios[gameState.currentRound-1][gameState.currentPlayerIndex];
  const available = curSc?.evidence||[];
  const selectedObjs = gameState.selectedEvidence.map(id=>available.find(e=>e.id===id)).filter(Boolean);
  eff = applyEvidenceBonus(eff, selectedObjs);

  // (optional) global event tweak: ถ้าชื่อเหตุการณ์มีคำว่า "เทคโนโลยี" boost reputation +1 สำหรับมิติที่เป็นบวก
  if((curSc?.globalEvent||'').includes('เทคโนโลยี')){
    if(eff.reputation>0) eff.reputation += 1;
  }

  // apply to scores
  Object.keys(eff).forEach(k=>{
    player.scores[k] = clamp(player.scores[k] + eff[k], 0, 100);
  });

  checkAchievements(player);

  // next player / round
  gameState.currentPlayerIndex++;
  if(gameState.currentPlayerIndex >= gameState.players.length){
    gameState.currentPlayerIndex = 0;
    gameState.currentRound++;
    if(gameState.currentRound > gameState.maxRounds){ endGame(); return; }
    loadCurrentScenario();
  }

  updateGameDisplay();
  updatePlayersGrid();
  updateActionSelection();
}

function skipTurn(){
  gameState.currentPlayerIndex++;
  if(gameState.currentPlayerIndex >= gameState.players.length){
    gameState.currentPlayerIndex = 0;
    gameState.currentRound++;
    if(gameState.currentRound > gameState.maxRounds){ endGame(); return; }
    loadCurrentScenario();
  }
  updateGameDisplay();
  updatePlayersGrid();
  updateActionSelection();
}

function checkAchievements(p){
  const total = Object.values(p.scores).reduce((a,b)=>a+b,0);
  if(total>=300 && !p.achievements.includes('high_performer')) p.achievements.push('high_performer');
  if(p.scores.studentQuality>=90 && !p.achievements.includes('quality_master')) p.achievements.push('quality_master');
  if(p.scores.wellbeing>=90 && !p.achievements.includes('happiness_guru')) p.achievements.push('happiness_guru');
  if(p.scores.reputation>=90 && !p.achievements.includes('reputation_king')) p.achievements.push('reputation_king');
}

function updateLeaderboard(){
  const wrap = $('#leaderboardList'); wrap.innerHTML='';
  const sorted = [...gameState.players].sort((a,b)=>{
    const ta = Object.values(a.scores).reduce((x,y)=>x+y,0);
    const tb = Object.values(b.scores).reduce((x,y)=>x+y,0);
    return tb-ta;
  });
  sorted.forEach((p,idx)=>{
    const total = Object.values(p.scores).reduce((x,y)=>x+y,0);
    const el = document.createElement('div');
    el.className = 'leaderboard-item';
    el.innerHTML = `
      <div class="player-info">
        <div class="player-avatar">${p.avatar}</div>
        <div class="player-details">
          <div style="font-weight:bold;">${idx+1}. ${p.name}</div>
          <div style="font-size:.9rem;opacity:.8;">${p.school}</div>
        </div>
      </div>
      <div style="font-weight:bold;">${total}</div>`;
    wrap.appendChild(el);
  });
}

function endGame(){
  $('#gameBoard').classList.add('hidden');
  $('#finalResults').classList.remove('hidden');

  const sorted = [...gameState.players].sort((a,b)=>{
    const ta = Object.values(a.scores).reduce((x,y)=>x+y,0);
    const tb = Object.values(b.scores).reduce((x,y)=>x+y,0);
    return tb-ta;
  });
  const winner = sorted[0];
  const winnerScore = Object.values(winner.scores).reduce((x,y)=>x+y,0);

  $('#winnerName').textContent = winner.name;
  $('#winnerSchool').textContent = winner.school;
  $('#winnerScore').textContent = winnerScore;
  $('#winnerAvatar').textContent = winner.avatar;

  // achievements
  const achWrap = $('#achievements'); achWrap.innerHTML='';
  const names = {
    high_performer:'🏆 นักบริหารมืออาชีพ',
    quality_master:'🎓 ผู้เชี่ยวชาญคุณภาพ',
    happiness_guru:'😊 กูรูความสุข',
    reputation_king:'🌟 ราชาชื่อเสียง'
  };
  winner.achievements.forEach(a=>{
    const b = document.createElement('span');
    b.className='achievement-badge';
    b.textContent = names[a]||a;
    achWrap.appendChild(b);
  });

  // final scores
  const list = $('#finalScoresList'); list.innerHTML='';
  sorted.forEach((p,idx)=>{
    const total = Object.values(p.scores).reduce((x,y)=>x+y,0);
    const item = document.createElement('div');
    item.className='final-score-item';
    item.innerHTML = `
      <div class="player-info">
        <div class="player-avatar">${p.avatar}</div>
        <div class="player-details">
          <div style="font-weight:bold;">${idx+1}. ${p.name}</div>
          <div style="opacity:.8;">${p.school}</div>
          <div style="font-size:1.2rem;font-weight:bold;margin-top:8px;">${total} คะแนน</div>
        </div>
      </div>
      <div style="display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-top:8px;font-size:.9rem;">
        <div>🎓 ${p.scores.studentQuality}</div>
        <div>👥 ${p.scores.enrollment}</div>
        <div>😊 ${p.scores.wellbeing}</div>
        <div>🌟 ${p.scores.reputation}</div>
      </div>`;
    list.appendChild(item);
  });
}

function resetGame(){
  // clear avatars
  window.selectedAvatars = {};
  // views
  $('#finalResults').classList.add('hidden');
  $('#gameBoard').classList.add('hidden');
  $('#gameSetup').classList.remove('hidden');

  // reset mode panel
  if($('#gameMode').value==='multi'){ updatePlayersSetup(); }
  else { updateSinglePlayerSetup(); }
}

// ====== Boot ======
document.addEventListener('DOMContentLoaded', ()=>{
  // default single
  $('#singlePlayerSetup').classList.remove('hidden');
  updateSinglePlayerSetup();
});
</script>
</body>
</html>
