<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>V2Ray Free Config Collector | دریافت کانفیگ رایگان</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Vazirmatn:wght@300;400;500;600;700;800;900&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --bg-primary: #0a0e1a;
            --bg-secondary: #111827;
            --bg-card: #1a2332;
            --bg-card-hover: #1f2b3d;
            --accent-blue: #3b82f6;
            --accent-purple: #8b5cf6;
            --accent-green: #10b981;
            --accent-orange: #f59e0b;
            --accent-red: #ef4444;
            --accent-cyan: #06b6d4;
            --accent-pink: #ec4899;
            --text-primary: #f1f5f9;
            --text-secondary: #94a3b8;
            --text-muted: #64748b;
            --border-color: #1e293b;
            --gradient-1: linear-gradient(135deg, #3b82f6, #8b5cf6);
            --gradient-2: linear-gradient(135deg, #10b981, #06b6d4);
            --gradient-3: linear-gradient(135deg, #f59e0b, #ef4444);
        }

        body {
            font-family: 'Vazirmatn', system-ui, -apple-system, sans-serif;
            background: var(--bg-primary);
            color: var(--text-primary);
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* Animated background */
        .bg-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            overflow: hidden;
            pointer-events: none;
        }

        .bg-animation .orb {
            position: absolute;
            border-radius: 50%;
            filter: blur(80px);
            opacity: 0.15;
            animation: float 20s infinite ease-in-out;
        }

        .bg-animation .orb:nth-child(1) {
            width: 400px; height: 400px;
            background: var(--accent-blue);
            top: -100px; left: -100px;
            animation-delay: 0s;
        }

        .bg-animation .orb:nth-child(2) {
            width: 500px; height: 500px;
            background: var(--accent-purple);
            bottom: -200px; right: -200px;
            animation-delay: -7s;
        }

        .bg-animation .orb:nth-child(3) {
            width: 300px; height: 300px;
            background: var(--accent-cyan);
            top: 50%; left: 50%;
            animation-delay: -14s;
        }

        @keyframes float {
            0%, 100% { transform: translate(0, 0) scale(1); }
            25% { transform: translate(50px, -80px) scale(1.1); }
            50% { transform: translate(-30px, 60px) scale(0.9); }
            75% { transform: translate(70px, 30px) scale(1.05); }
        }

        .container {
            position: relative;
            z-index: 1;
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Header */
        .header {
            text-align: center;
            padding: 40px 20px 30px;
            margin-bottom: 30px;
        }

        .header .logo {
            display: inline-flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 20px;
        }

        .header .logo-icon {
            width: 60px;
            height: 60px;
            background: var(--gradient-1);
            border-radius: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 28px;
            box-shadow: 0 8px 30px rgba(59, 130, 246, 0.3);
            animation: pulse-glow 3s infinite;
        }

        @keyframes pulse-glow {
            0%, 100% { box-shadow: 0 8px 30px rgba(59, 130, 246, 0.3); }
            50% { box-shadow: 0 8px 50px rgba(59, 130, 246, 0.5); }
        }

        .header h1 {
            font-size: 2.2em;
            font-weight: 900;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 10px;
        }

        .header p {
            color: var(--text-secondary);
            font-size: 1.05em;
            max-width: 600px;
            margin: 0 auto;
            line-height: 1.8;
        }

        /* Stats Bar */
        .stats-bar {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 15px;
            margin-bottom: 30px;
        }

        .stat-card {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            padding: 20px;
            text-align: center;
            transition: all 0.3s ease;
        }

        .stat-card:hover {
            transform: translateY(-3px);
            border-color: var(--accent-blue);
        }

        .stat-card .stat-value {
            font-size: 1.8em;
            font-weight: 800;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .stat-card:nth-child(2) .stat-value {
            background: var(--gradient-2);
            -webkit-background-clip: text;
            background-clip: text;
        }

        .stat-card:nth-child(3) .stat-value {
            background: var(--gradient-3);
            -webkit-background-clip: text;
            background-clip: text;
        }

        .stat-card:nth-child(4) .stat-value {
            background: linear-gradient(135deg, #ec4899, #8b5cf6);
            -webkit-background-clip: text;
            background-clip: text;
        }

        .stat-card .stat-label {
            color: var(--text-secondary);
            font-size: 0.85em;
            margin-top: 5px;
        }

        /* Controls */
        .controls {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            margin-bottom: 25px;
            align-items: center;
        }

        .filter-btn {
            padding: 10px 22px;
            border: 1px solid var(--border-color);
            background: var(--bg-card);
            color: var(--text-secondary);
            border-radius: 12px;
            cursor: pointer;
            font-family: inherit;
            font-size: 0.9em;
            font-weight: 500;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .filter-btn:hover {
            border-color: var(--accent-blue);
            color: var(--text-primary);
            background: var(--bg-card-hover);
        }

        .filter-btn.active {
            background: var(--accent-blue);
            border-color: var(--accent-blue);
            color: white;
            box-shadow: 0 4px 15px rgba(59, 130, 246, 0.3);
        }

        .filter-btn .count {
            background: rgba(255,255,255,0.15);
            padding: 2px 8px;
            border-radius: 8px;
            font-size: 0.8em;
        }

        .filter-btn.active .count {
            background: rgba(255,255,255,0.25);
        }

        .refresh-btn {
            padding: 10px 28px;
            background: var(--gradient-1);
            border: none;
            color: white;
            border-radius: 12px;
            cursor: pointer;
            font-family: inherit;
            font-size: 0.95em;
            font-weight: 600;
            margin-right: auto;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .refresh-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(59, 130, 246, 0.4);
        }

        .refresh-btn.loading .refresh-icon {
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            100% { transform: rotate(360deg); }
        }

        /* Sort controls */
        .sort-controls {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            flex-wrap: wrap;
            align-items: center;
        }

        .sort-controls label {
            color: var(--text-secondary);
            font-size: 0.9em;
        }

        .sort-select {
            padding: 8px 16px;
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            color: var(--text-primary);
            border-radius: 10px;
            font-family: inherit;
            font-size: 0.88em;
            cursor: pointer;
            outline: none;
        }

        .sort-select:focus {
            border-color: var(--accent-blue);
        }

        /* Source Sections */
        .source-section {
            margin-bottom: 35px;
        }

        .source-header {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 18px 22px;
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 16px 16px 0 0;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .source-header:hover {
            background: var(--bg-card-hover);
        }

        .source-header .source-icon {
            width: 42px;
            height: 42px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            flex-shrink: 0;
        }

        .source-header .source-info {
            flex: 1;
        }

        .source-header .source-name {
            font-weight: 700;
            font-size: 1.05em;
        }

        .source-header .source-desc {
            color: var(--text-secondary);
            font-size: 0.82em;
            margin-top: 3px;
        }

        .source-header .source-badge {
            padding: 5px 14px;
            border-radius: 10px;
            font-size: 0.8em;
            font-weight: 600;
        }

        .source-header .toggle-icon {
            color: var(--text-muted);
            font-size: 1.2em;
            transition: transform 0.3s ease;
        }

        .source-section.collapsed .toggle-icon {
            transform: rotate(-90deg);
        }

        .source-section.collapsed .source-configs {
            display: none;
        }

        .source-configs {
            border: 1px solid var(--border-color);
            border-top: none;
            border-radius: 0 0 16px 16px;
            overflow: hidden;
        }

        /* Config Cards */
        .config-card {
            display: grid;
            grid-template-columns: auto 1fr auto auto;
            gap: 15px;
            align-items: center;
            padding: 16px 22px;
            border-bottom: 1px solid var(--border-color);
            transition: all 0.2s ease;
            background: rgba(26, 35, 50, 0.5);
        }

        .config-card:last-child {
            border-bottom: none;
        }

        .config-card:hover {
            background: var(--bg-card-hover);
        }

        .config-protocol {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 4px;
        }

        .protocol-badge {
            padding: 5px 14px;
            border-radius: 8px;
            font-size: 0.75em;
            font-weight: 700;
            letter-spacing: 0.5px;
            text-transform: uppercase;
        }

        .protocol-badge.vmess {
            background: rgba(59, 130, 246, 0.15);
            color: #60a5fa;
            border: 1px solid rgba(59, 130, 246, 0.3);
        }

        .protocol-badge.vless {
            background: rgba(139, 92, 246, 0.15);
            color: #a78bfa;
            border: 1px solid rgba(139, 92, 246, 0.3);
        }

        .protocol-badge.trojan {
            background: rgba(245, 158, 11, 0.15);
            color: #fbbf24;
            border: 1px solid rgba(245, 158, 11, 0.3);
        }

        .protocol-badge.ss {
            background: rgba(16, 185, 129, 0.15);
            color: #34d399;
            border: 1px solid rgba(16, 185, 129, 0.3);
        }

        .protocol-badge.ssr {
            background: rgba(236, 72, 153, 0.15);
            color: #f472b6;
            border: 1px solid rgba(236, 72, 153, 0.3);
        }

        .protocol-badge.hysteria2, .protocol-badge.hy2 {
            background: rgba(6, 182, 212, 0.15);
            color: #22d3ee;
            border: 1px solid rgba(6, 182, 212, 0.3);
        }

        .protocol-badge.tuic {
            background: rgba(251, 146, 60, 0.15);
            color: #fb923c;
            border: 1px solid rgba(251, 146, 60, 0.3);
        }

        .config-details {
            min-width: 0;
        }

        .config-name {
            font-weight: 600;
            font-size: 0.92em;
            margin-bottom: 4px;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            direction: ltr;
            text-align: left;
        }

        .config-meta {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            direction: ltr;
        }

        .config-meta span {
            display: flex;
            align-items: center;
            gap: 4px;
            font-size: 0.78em;
            color: var(--text-secondary);
        }

        .config-quality {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 5px;
            min-width: 90px;
        }

        .quality-bar-container {
            width: 80px;
            height: 6px;
            background: rgba(255,255,255,0.08);
            border-radius: 3px;
            overflow: hidden;
        }

        .quality-bar {
            height: 100%;
            border-radius: 3px;
            transition: width 0.5s ease;
        }

        .quality-label {
            font-size: 0.72em;
            font-weight: 600;
        }

        .quality-excellent .quality-bar { background: var(--accent-green); width: 100%; }
        .quality-excellent .quality-label { color: var(--accent-green); }

        .quality-good .quality-bar { background: #22c55e; width: 75%; }
        .quality-good .quality-label { color: #22c55e; }

        .quality-medium .quality-bar { background: var(--accent-orange); width: 50%; }
        .quality-medium .quality-label { color: var(--accent-orange); }

        .quality-poor .quality-bar { background: var(--accent-red); width: 25%; }
        .quality-poor .quality-label { color: var(--accent-red); }

        .quality-unknown .quality-bar { background: var(--text-muted); width: 40%; }
        .quality-unknown .quality-label { color: var(--text-muted); }

        .config-actions {
            display: flex;
            gap: 8px;
        }

        .copy-btn, .qr-btn {
            padding: 8px 16px;
            border: 1px solid var(--border-color);
            background: var(--bg-card);
            color: var(--text-secondary);
            border-radius: 10px;
            cursor: pointer;
            font-family: inherit;
            font-size: 0.82em;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .copy-btn:hover {
            background: var(--accent-blue);
            border-color: var(--accent-blue);
            color: white;
        }

        .copy-btn.copied {
            background: var(--accent-green);
            border-color: var(--accent-green);
            color: white;
        }

        .qr-btn:hover {
            background: var(--accent-purple);
            border-color: var(--accent-purple);
            color: white;
        }

        /* Loading State */
        .loading-state {
            text-align: center;
            padding: 60px 20px;
        }

        .loading-spinner {
            width: 50px;
            height: 50px;
            border: 3px solid var(--border-color);
            border-top-color: var(--accent-blue);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 0 auto 20px;
        }

        .loading-state p {
            color: var(--text-secondary);
            font-size: 0.95em;
        }

        .loading-progress {
            width: 300px;
            max-width: 90%;
            height: 4px;
            background: var(--border-color);
            border-radius: 2px;
            margin: 15px auto 0;
            overflow: hidden;
        }

        .loading-progress-bar {
            height: 100%;
            background: var(--gradient-1);
            border-radius: 2px;
            transition: width 0.5s ease;
            width: 0%;
        }

        /* Empty State */
        .empty-state {
            text-align: center;
            padding: 60px 20px;
            color: var(--text-secondary);
        }

        .empty-state .empty-icon {
            font-size: 3em;
            margin-bottom: 15px;
        }

        /* Toast */
        .toast {
            position: fixed;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%) translateY(100px);
            background: var(--bg-card);
            border: 1px solid var(--accent-green);
            color: var(--text-primary);
            padding: 14px 28px;
            border-radius: 14px;
            font-family: inherit;
            font-size: 0.9em;
            z-index: 1000;
            transition: transform 0.4s ease;
            box-shadow: 0 10px 40px rgba(0,0,0,0.4);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .toast.show {
            transform: translateX(-50%) translateY(0);
        }

        /* QR Modal */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.7);
            backdrop-filter: blur(5px);
            z-index: 999;
            display: none;
            align-items: center;
            justify-content: center;
        }

        .modal-overlay.show {
            display: flex;
        }

        .modal {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            padding: 30px;
            max-width: 400px;
            width: 90%;
            text-align: center;
        }

        .modal h3 {
            margin-bottom: 20px;
            font-size: 1.1em;
        }

        .modal .qr-placeholder {
            width: 250px;
            height: 250px;
            margin: 0 auto 20px;
            background: white;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 15px;
        }

        .modal .qr-placeholder canvas {
            width: 100% !important;
            height: 100% !important;
        }

        .modal .close-btn {
            padding: 10px 30px;
            background: var(--gradient-1);
            border: none;
            color: white;
            border-radius: 12px;
            cursor: pointer;
            font-family: inherit;
            font-size: 0.9em;
            font-weight: 600;
        }

        /* Sub link section */
        .sub-section {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            padding: 25px;
            margin-bottom: 30px;
        }

        .sub-section h3 {
            font-size: 1.1em;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .sub-links-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 12px;
        }

        .sub-link-item {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 12px 16px;
            background: rgba(255,255,255,0.03);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            transition: all 0.2s ease;
        }

        .sub-link-item:hover {
            border-color: var(--accent-blue);
            background: rgba(59, 130, 246, 0.05);
        }

        .sub-link-item .sub-name {
            font-weight: 600;
            font-size: 0.85em;
            min-width: 100px;
        }

        .sub-link-item .sub-url {
            flex: 1;
            font-size: 0.72em;
            color: var(--text-muted);
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            direction: ltr;
            text-align: left;
        }

        .sub-link-item .copy-sub-btn {
            padding: 6px 14px;
            background: var(--accent-blue);
            border: none;
            color: white;
            border-radius: 8px;
            cursor: pointer;
            font-family: inherit;
            font-size: 0.78em;
            font-weight: 600;
            white-space: nowrap;
            transition: all 0.2s ease;
        }

        .sub-link-item .copy-sub-btn:hover {
            background: #2563eb;
        }

        /* Footer */
        .footer {
            text-align: center;
            padding: 40px 20px;
            border-top: 1px solid var(--border-color);
            margin-top: 40px;
        }

        .footer p {
            color: var(--text-muted);
            font-size: 0.85em;
            margin-bottom: 8px;
        }

        .footer .disclaimer {
            color: var(--accent-orange);
            font-size: 0.78em;
            max-width: 600px;
            margin: 15px auto 0;
            line-height: 1.8;
            padding: 15px;
            background: rgba(245, 158, 11, 0.05);
            border: 1px solid rgba(245, 158, 11, 0.15);
            border-radius: 12px;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .header h1 { font-size: 1.6em; }
            .config-card {
                grid-template-columns: 1fr;
                gap: 10px;
            }
            .config-protocol { flex-direction: row; justify-content: flex-start; }
            .config-quality { flex-direction: row; }
            .config-actions { justify-content: flex-end; }
            .controls { justify-content: center; }
            .sub-links-grid { grid-template-columns: 1fr; }
            .stats-bar { grid-template-columns: repeat(3, 1fr); }
        }

        /* Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: var(--bg-primary);
        }
        ::-webkit-scrollbar-thumb {
            background: var(--border-color);
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: var(--text-muted);
        }

        .config-link-raw {
            font-family: monospace;
            font-size: 0.7em;
            color: var(--text-muted);
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            max-width: 400px;
            direction: ltr;
            text-align: left;
            margin-top: 3px;
        }

        .country-flag {
            font-size: 1.2em;
        }

        .config-card.highlight {
            animation: highlight-flash 1s ease;
        }

        @keyframes highlight-flash {
            0% { background: rgba(59, 130, 246, 0.15); }
            100% { background: transparent; }
        }

        .search-box {
            flex: 1;
            min-width: 200px;
            max-width: 350px;
            padding: 10px 18px;
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            color: var(--text-primary);
            border-radius: 12px;
            font-family: inherit;
            font-size: 0.9em;
            outline: none;
            transition: border-color 0.3s ease;
        }

        .search-box:focus {
            border-color: var(--accent-blue);
        }

        .search-box::placeholder {
            color: var(--text-muted);
        }

        .copy-all-btn {
            padding: 10px 22px;
            background: var(--gradient-2);
            border: none;
            color: white;
            border-radius: 12px;
            cursor: pointer;
            font-family: inherit;
            font-size: 0.9em;
            font-weight: 600;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .copy-all-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(16, 185, 129, 0.4);
        }

        /* Last update badge */
        .last-update {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            padding: 6px 14px;
            background: rgba(16, 185, 129, 0.1);
            border: 1px solid rgba(16, 185, 129, 0.2);
            border-radius: 10px;
            font-size: 0.8em;
            color: var(--accent-green);
            margin-top: 15px;
        }

        .last-update .dot {
            width: 8px;
            height: 8px;
            background: var(--accent-green);
            border-radius: 50%;
            animation: blink 2s infinite;
        }

        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.3; }
        }
    </style>
</head>
<body>
    <div class="bg-animation">
        <div class="orb"></div>
        <div class="orb"></div>
        <div class="orb"></div>
    </div>

    <div class="container">
        <!-- Header -->
        <div class="header">
            <div class="logo">
                <div class="logo-icon">⚡</div>
            </div>
            <h1>V2Ray Free Config Collector</h1>
            <p>جمع‌آوری خودکار کانفیگ‌های رایگان V2Ray از مخازن معتبر GitHub<br>با نمایش کیفیت اتصال و دسته‌بندی بر اساس پروتکل</p>
            <div class="last-update" id="lastUpdate">
                <span class="dot"></span>
                <span>در حال بارگذاری...</span>
            </div>
        </div>

        <!-- Stats -->
        <div class="stats-bar" id="statsBar">
            <div class="stat-card">
                <div class="stat-value" id="totalConfigs">-</div>
                <div class="stat-label">کل کانفیگ‌ها</div>
            </div>
            <div class="stat-card">
                <div class="stat-value" id="totalSources">-</div>
                <div class="stat-label">تعداد منابع</div>
            </div>
            <div class="stat-card">
                <div class="stat-value" id="activeConfigs">-</div>
                <div class="stat-label">پروتکل‌های متنوع</div>
            </div>
            <div class="stat-card">
                <div class="stat-value" id="countriesCount">-</div>
                <div class="stat-label">تعداد کشورها</div>
            </div>
            <div class="stat-card">
                <div class="stat-value" id="aliveCount" style="background:linear-gradient(135deg,#10b981,#22c55e);-webkit-background-clip:text;background-clip:text;">-</div>
                <div class="stat-label">🟢 سرورهای آنلاین</div>
            </div>
            <div class="stat-card">
                <div class="stat-value" id="avgPing" style="background:linear-gradient(135deg,#06b6d4,#3b82f6);-webkit-background-clip:text;background-clip:text;">-</div>
                <div class="stat-label">⚡ میانگین پینگ</div>
            </div>
        </div>

        <!-- Subscription Links -->
        <div class="sub-section">
            <h3>🔗 لینک‌های اشتراک (Subscription URLs)</h3>
            <div class="sub-links-grid" id="subLinksGrid"></div>
        </div>

        <!-- Controls -->
        <div class="controls" id="filterControls">
            <button class="refresh-btn" onclick="fetchAllConfigs()">
                <span class="refresh-icon">🔄</span>
                بارگذاری مجدد
            </button>
            <input type="text" class="search-box" id="searchBox" placeholder="🔍 جستجو در کانفیگ‌ها..." oninput="applyFilters()">
            <button class="copy-all-btn" onclick="copyAllFiltered()">
                📋 کپی همه
            </button>
        </div>

        <div class="controls" id="protocolFilters">
            <button class="filter-btn active" data-filter="all" onclick="setFilter('all', this)">
                همه <span class="count" id="count-all">0</span>
            </button>
        </div>

        <!-- Sort -->
        <div class="sort-controls">
            <label>مرتب‌سازی:</label>
            <select class="sort-select" id="sortSelect" onchange="applyFilters()">
                <option value="quality-desc">کیفیت (بهترین)</option>
                <option value="quality-asc">کیفیت (کمترین)</option>
                <option value="ping-asc">پینگ (کمترین)</option>
                <option value="ping-desc">پینگ (بیشترین)</option>
                <option value="protocol">پروتکل</option>
                <option value="country">کشور</option>
                <option value="alive-first">آنلاین‌ها اول</option>
            </select>
            <button class="filter-btn" onclick="startPingTest()" id="pingTestBtn" style="background:linear-gradient(135deg,#06b6d4,#10b981);color:white;border:none;font-weight:600;">
                🔍 تست پینگ واقعی
            </button>
        </div>

        <!-- Ping Progress -->
        <div id="pingProgressContainer"></div>

        <!-- Quality Legend -->
        <div style="display:flex;flex-wrap:wrap;gap:15px;margin-bottom:20px;padding:14px 18px;background:var(--bg-card);border:1px solid var(--border-color);border-radius:12px;font-size:0.78em;">
            <span style="color:var(--text-secondary);font-weight:600;">📊 معیارهای کیفیت:</span>
            <span style="color:var(--accent-purple);">🔌 پروتکل (۲۰)</span>
            <span style="color:var(--accent-green);">🔒 امنیت/TLS (۲۵)</span>
            <span style="color:var(--accent-blue);">🌐 نوع انتقال (۱۵)</span>
            <span style="color:var(--accent-orange);">🖥️ آدرس (۱۰)</span>
            <span style="color:var(--accent-pink);">🔌 پورت (۱۰)</span>
            <span style="color:var(--accent-cyan);">⭐ اعتبار منبع (۱۰)</span>
            <span style="color:var(--text-muted);">📋 کامل بودن (۱۰)</span>
            <span style="color:#22c55e;">📡 پینگ واقعی (+۱۵)</span>
        </div>

        <!-- Configs Container -->
        <div id="configsContainer">
            <div class="loading-state" id="loadingState">
                <div class="loading-spinner"></div>
                <p>در حال دریافت کانفیگ‌ها از مخازن GitHub...</p>
                <div class="loading-progress">
                    <div class="loading-progress-bar" id="loadingProgressBar"></div>
                </div>
                <p style="margin-top: 10px; font-size: 0.8em; color: var(--text-muted);" id="loadingStatus">آماده‌سازی...</p>
            </div>
        </div>

        <!-- Footer -->
        <div class="footer">
            <p>V2Ray Free Config Collector © 2025</p>
            <p>تمامی کانفیگ‌ها از مخازن عمومی GitHub جمع‌آوری شده‌اند</p>
            <div class="disclaimer">
                ⚠️ توجه: این کانفیگ‌ها از منابع عمومی جمع‌آوری شده‌اند و هیچ تضمینی برای عملکرد یا امنیت آنها وجود ندارد. استفاده از کانفیگ‌های عمومی ریسک‌های امنیتی دارد. با مسئولیت خودتان استفاده کنید.
            </div>
        </div>
    </div>

    <!-- Toast -->
    <div class="toast" id="toast">
        <span>✅</span>
        <span id="toastMessage">کپی شد!</span>
    </div>

    <!-- QR Modal -->
    <div class="modal-overlay" id="qrModal">
        <div class="modal">
            <h3>📱 QR Code</h3>
            <div class="qr-placeholder" id="qrContainer"></div>
            <button class="close-btn" onclick="closeQR()">بستن</button>
        </div>
    </div>

    <!-- QR Code Library - Inline for reliability -->
    <script src="https://cdn.jsdelivr.net/npm/qrcode@1.5.3/build/qrcode.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>

    <script>
    // ============================================================
    // GitHub Sources Configuration
    // ============================================================
    const SOURCES = [
        {
            name: "EbraSha",
            desc: "به‌روزرسانی هر ۳۰ دقیقه — تست‌شده و فعال",
            icon: "🔥",
            color: "#ef4444",
            urls: [
                "https://raw.githubusercontent.com/ebrasha/free-v2ray-public-list/refs/heads/main/V2Ray-Config-By-EbraSha.txt"
            ]
        },
        {
            name: "Epodonios",
            desc: "کانفیگ‌های تفکیک‌شده بر اساس پروتکل",
            icon: "🌐",
            color: "#3b82f6",
            urls: [
                "https://raw.githubusercontent.com/Epodonios/v2ray-configs/main/Splitted-By-Protocol/vmess.txt",
                "https://raw.githubusercontent.com/Epodonios/v2ray-configs/main/Splitted-By-Protocol/vless.txt",
                "https://raw.githubusercontent.com/Epodonios/v2ray-configs/main/Splitted-By-Protocol/trojan.txt",
                "https://raw.githubusercontent.com/Epodonios/v2ray-configs/main/Splitted-By-Protocol/ss.txt"
            ]
        },
        {
            name: "MatinGhanbari",
            desc: "مجموعه فیلترشده و بهینه",
            icon: "⭐",
            color: "#f59e0b",
            urls: [
                "https://raw.githubusercontent.com/MatinGhanbari/v2ray-configs/main/subscriptions/filtered/subs/vmess.txt",
                "https://raw.githubusercontent.com/MatinGhanbari/v2ray-configs/main/subscriptions/filtered/subs/vless.txt"
            ]
        },
        {
            name: "barry-far",
            desc: "تفکیک بر اساس پروتکل — به‌روزرسانی مداوم",
            icon: "🚀",
            color: "#8b5cf6",
            urls: [
                "https://raw.githubusercontent.com/barry-far/V2ray-config/main/Splitted-By-Protocol/vmess.txt",
                "https://raw.githubusercontent.com/barry-far/V2ray-config/main/Splitted-By-Protocol/vless.txt",
                "https://raw.githubusercontent.com/barry-far/V2ray-config/main/Splitted-By-Protocol/ss.txt"
            ]
        },
        {
            name: "MahdiBland (Eternity)",
            desc: "ShadowsocksAggregator — تست سرعت خودکار",
            icon: "♾️",
            color: "#10b981",
            urls: [
                "https://raw.githubusercontent.com/mahdibland/ShadowsocksAggregator/master/Eternity.txt"
            ]
        },
        {
            name: "MrMohebi (Telegram Grabber)",
            desc: "جمع‌آوری از کانال‌های تلگرام — فقط فعال‌ها",
            icon: "📡",
            color: "#06b6d4",
            urls: [
                "https://raw.githubusercontent.com/MrMohebi/xray-proxy-grabber-telegram/master/collected-proxies/row-url/actives.txt"
            ]
        },
        {
            name: "ShatakVPN (ConfigForge)",
            desc: "بهینه‌سازی‌شده با تست Check-Host API",
            icon: "🛡️",
            color: "#ec4899",
            urls: [
                "https://raw.githubusercontent.com/ShatakVPN/ConfigForge-V2Ray/main/configs/all.txt"
            ]
        },
        {
            name: "4n0nymou3",
            desc: "Multi-proxy config fetcher",
            icon: "🎭",
            color: "#14b8a6",
            urls: [
                "https://raw.githubusercontent.com/4n0nymou3/multi-proxy-config-fetcher/refs/heads/main/configs/proxy_configs.txt"
            ]
        },
        {
            name: "Argh94 (V2RayAutoConfig)",
            desc: "کانفیگ خودکار با پروتکل‌های متنوع",
            icon: "⚙️",
            color: "#a855f7",
            urls: [
                "https://raw.githubusercontent.com/Argh94/V2RayAutoConfig/refs/heads/main/configs/Vmess.txt",
                "https://raw.githubusercontent.com/Argh94/V2RayAutoConfig/refs/heads/main/configs/ShadowSocks.txt"
            ]
        },
        {
            name: "Pawdroid",
            desc: "سرورهای رایگان بین‌المللی",
            icon: "🌍",
            color: "#f97316",
            urls: [
                "https://raw.githubusercontent.com/Pawdroid/Free-servers/main/sub"
            ]
        }
    ];

    // ============================================================
    // State
    // ============================================================
    let allConfigs = [];
    let currentFilter = 'all';
    let protocolCounts = {};

    // ============================================================
    // Country Detection
    // ============================================================
    const COUNTRY_MAP = {
        'US': { flag: '🇺🇸', name: 'آمریکا' },
        'GB': { flag: '🇬🇧', name: 'انگلستان' },
        'UK': { flag: '🇬🇧', name: 'انگلستان' },
        'DE': { flag: '🇩🇪', name: 'آلمان' },
        'FR': { flag: '🇫🇷', name: 'فرانسه' },
        'NL': { flag: '🇳🇱', name: 'هلند' },
        'JP': { flag: '🇯🇵', name: 'ژاپن' },
        'SG': { flag: '🇸🇬', name: 'سنگاپور' },
        'HK': { flag: '🇭🇰', name: 'هنگ‌کنگ' },
        'KR': { flag: '🇰🇷', name: 'کره جنوبی' },
        'CA': { flag: '🇨🇦', name: 'کانادا' },
        'AU': { flag: '🇦🇺', name: 'استرالیا' },
        'FI': { flag: '🇫🇮', name: 'فنلاند' },
        'SE': { flag: '🇸🇪', name: 'سوئد' },
        'NO': { flag: '🇳🇴', name: 'نروژ' },
        'CH': { flag: '🇨🇭', name: 'سوئیس' },
        'RU': { flag: '🇷🇺', name: 'روسیه' },
        'IN': { flag: '🇮🇳', name: 'هند' },
        'BR': { flag: '🇧🇷', name: 'برزیل' },
        'TR': { flag: '🇹🇷', name: 'ترکیه' },
        'IR': { flag: '🇮🇷', name: 'ایران' },
        'CN': { flag: '🇨🇳', name: 'چین' },
        'TW': { flag: '🇹🇼', name: 'تایوان' },
        'IE': { flag: '🇮🇪', name: 'ایرلند' },
        'PL': { flag: '🇵🇱', name: 'لهستان' },
        'IT': { flag: '🇮🇹', name: 'ایتالیا' },
        'ES': { flag: '🇪🇸', name: 'اسپانیا' },
        'AT': { flag: '🇦🇹', name: 'اتریش' },
        'CZ': { flag: '🇨🇿', name: 'چک' },
        'RO': { flag: '🇷🇴', name: 'رومانی' },
        'BG': { flag: '🇧🇬', name: 'بلغارستان' },
        'UA': { flag: '🇺🇦', name: 'اوکراین' },
        'LT': { flag: '🇱🇹', name: 'لیتوانی' },
        'LV': { flag: '🇱🇻', name: 'لتونی' },
        'EE': { flag: '🇪🇪', name: 'استونی' },
        'MD': { flag: '🇲🇩', name: 'مولداوی' },
        'LU': { flag: '🇱🇺', name: 'لوکزامبورگ' },
    };

    function detectCountryFromConfig(line, parsed) {
        // Check for country flag emoji in the line
        const flagRegex = /[\u{1F1E6}-\u{1F1FF}]{2}/gu;
        const flags = line.match(flagRegex);
        if (flags && flags.length > 0) {
            const cp1 = flags[0].codePointAt(0) - 0x1F1E6 + 65;
            const cp2 = flags[0].codePointAt(2) - 0x1F1E6 + 65;
            const code = String.fromCharCode(cp1) + String.fromCharCode(cp2);
            if (COUNTRY_MAP[code]) return { code, ...COUNTRY_MAP[code] };
        }

        // Check for country code in the name/remark
        const nameStr = (parsed.name || parsed.ps || '').toUpperCase();
        for (const [code, info] of Object.entries(COUNTRY_MAP)) {
            if (nameStr.includes(code + '-') || nameStr.includes(code + ' ') || nameStr.startsWith(code)) {
                return { code, ...info };
            }
        }

        // Check address for common TLDs
        const addr = (parsed.address || parsed.add || '').toLowerCase();
        if (addr.includes('.jp') || addr.includes('japan')) return { code: 'JP', ...COUNTRY_MAP['JP'] };
        if (addr.includes('.de') || addr.includes('germany')) return { code: 'DE', ...COUNTRY_MAP['DE'] };
        if (addr.includes('.sg') || addr.includes('singapore')) return { code: 'SG', ...COUNTRY_MAP['SG'] };
        if (addr.includes('.us') || addr.includes('america')) return { code: 'US', ...COUNTRY_MAP['US'] };

        return { code: '??', flag: '🌍', name: 'نامشخص' };
    }

    // ============================================================
    // Config Parser
    // ============================================================
    function parseConfigLine(line) {
        line = line.trim();
        if (!line || line.startsWith('#') || line.startsWith('//') || line.length < 10) return null;

        let protocol = '';
        let parsed = {};

        try {
            if (line.startsWith('vmess://')) {
                protocol = 'vmess';
                const encoded = line.substring(8);
                try {
                    const json = JSON.parse(atob(encoded));
                    parsed = {
                        name: json.ps || json.remark || '',
                        address: json.add || '',
                        port: json.port || '',
                        network: json.net || '',
                        tls: json.tls || '',
                        ps: json.ps || '',
                        add: json.add || ''
                    };
                } catch {
                    parsed = { name: 'VMess Config', address: '' };
                }
            } else if (line.startsWith('vless://')) {
                protocol = 'vless';
                try {
                    const url = new URL(line);
                    parsed = {
                        name: decodeURIComponent(url.hash.substring(1) || ''),
                        address: url.hostname,
                        port: url.port,
                        network: url.searchParams.get('type') || '',
                        tls: url.searchParams.get('security') || ''
                    };
                } catch {
                    parsed = { name: 'VLESS Config', address: '' };
                }
            } else if (line.startsWith('trojan://')) {
                protocol = 'trojan';
                try {
                    const url = new URL(line);
                    parsed = {
                        name: decodeURIComponent(url.hash.substring(1) || ''),
                        address: url.hostname,
                        port: url.port,
                        network: url.searchParams.get('type') || '',
                        tls: 'tls'
                    };
                } catch {
                    parsed = { name: 'Trojan Config', address: '' };
                }
            } else if (line.startsWith('ss://')) {
                protocol = 'ss';
                try {
                    let rest = line.substring(5);
                    let name = '';
                    const hashIdx = rest.indexOf('#');
                    if (hashIdx !== -1) {
                        name = decodeURIComponent(rest.substring(hashIdx + 1));
                        rest = rest.substring(0, hashIdx);
                    }
                    // Try to extract host
                    let address = '';
                    let port = '';
                    const atIdx = rest.lastIndexOf('@');
                    if (atIdx !== -1) {
                        const hostPart = rest.substring(atIdx + 1);
                        const colonIdx = hostPart.lastIndexOf(':');
                        if (colonIdx !== -1) {
                            address = hostPart.substring(0, colonIdx);
                            port = hostPart.substring(colonIdx + 1);
                        }
                    }
                    parsed = { name: name || 'SS Config', address, port, network: 'tcp', tls: '' };
                } catch {
                    parsed = { name: 'SS Config', address: '' };
                }
            } else if (line.startsWith('ssr://')) {
                protocol = 'ssr';
                parsed = { name: 'SSR Config', address: '', network: 'tcp', tls: '' };
            } else if (line.startsWith('hysteria2://') || line.startsWith('hy2://')) {
                protocol = 'hysteria2';
                try {
                    const url = new URL(line);
                    parsed = {
                        name: decodeURIComponent(url.hash.substring(1) || ''),
                        address: url.hostname,
                        port: url.port,
                        network: 'udp',
                        tls: 'tls'
                    };
                } catch {
                    parsed = { name: 'Hysteria2 Config', address: '' };
                }
            } else if (line.startsWith('tuic://')) {
                protocol = 'tuic';
                try {
                    const url = new URL(line);
                    parsed = {
                        name: decodeURIComponent(url.hash.substring(1) || ''),
                        address: url.hostname,
                        port: url.port,
                        network: 'udp',
                        tls: 'tls'
                    };
                } catch {
                    parsed = { name: 'TUIC Config', address: '' };
                }
            } else {
                return null;
            }
        } catch {
            return null;
        }

        const country = detectCountryFromConfig(line, parsed);

        return {
            protocol,
            raw: line,
            name: parsed.name || `${protocol.toUpperCase()} Config`,
            address: parsed.address || 'Unknown',
            port: parsed.port || '-',
            network: parsed.network || '-',
            tls: parsed.tls || 'none',
            country,
            quality: estimateQuality(parsed, protocol)
        };
    }

    // ============================================================
    // Quality Estimation (Hybrid: Technical + Real Ping)
    // ============================================================
    function estimateQuality(parsed, protocol) {
        let score = 0;
        const breakdown = {};

        // ── 1. Protocol Score (0-20) ──
        const protoScores = { hysteria2: 20, tuic: 18, vless: 15, trojan: 12, vmess: 10, ss: 8, ssr: 5 };
        const protoScore = protoScores[protocol] || 5;
        score += protoScore;
        breakdown.protocol = protoScore;

        // ── 2. Security Score (0-25) ──
        let secScore = 0;
        if (parsed.tls === 'reality') secScore = 25;
        else if (parsed.tls === 'tls') secScore = 18;
        else secScore = 3;
        score += secScore;
        breakdown.security = secScore;

        // ── 3. Transport/Network Score (0-15) ──
        const netScores = { grpc: 15, h2: 13, ws: 10, websocket: 10, tcp: 7, kcp: 5, quic: 12, httpupgrade: 11, xhttp: 11 };
        const netScore = netScores[(parsed.network || '').toLowerCase()] || 5;
        score += netScore;
        breakdown.transport = netScore;

        // ── 4. Address Quality (0-10) ──
        let addrScore = 5;
        const addr = (parsed.address || parsed.add || '').toLowerCase();
        if (addr && addr !== 'unknown') {
            // CDN/Cloudflare addresses = good anti-censorship
            if (addr.includes('workers.dev') || addr.includes('pages.dev') || addr.includes('cloudflare')) addrScore = 10;
            // Domain names are generally better than raw IPs
            else if (addr.match(/[a-z]/)) addrScore = 8;
            // IPv4
            else if (addr.match(/^\d+\.\d+\.\d+\.\d+$/)) addrScore = 6;
            // IPv6
            else if (addr.includes(':')) addrScore = 5;
        } else {
            addrScore = 2;
        }
        score += addrScore;
        breakdown.address = addrScore;

        // ── 5. Port Score (0-10) ──
        let portScore = 5;
        const port = parseInt(parsed.port);
        if (port === 443) portScore = 10;        // HTTPS - best for bypassing
        else if (port === 80) portScore = 8;      // HTTP - common
        else if (port === 8443 || port === 2053 || port === 2083 || port === 2087 || port === 2096) portScore = 9; // CF ports
        else if (port === 8080 || port === 8880 || port === 2052 || port === 2082 || port === 2086 || port === 2095) portScore = 8;
        else if (port > 0 && port < 1024) portScore = 6;
        else if (port >= 1024) portScore = 5;
        score += portScore;
        breakdown.port = portScore;

        // ── 6. Source Reputation (0-10) ──
        // Will be filled after source is assigned
        breakdown.sourceReputation = 0;

        // ── 7. Config Completeness (0-10) ──
        let completeScore = 0;
        if (parsed.name && parsed.name.length > 2) completeScore += 2;
        if (parsed.address && parsed.address !== 'Unknown') completeScore += 3;
        if (parsed.port && parsed.port !== '-') completeScore += 2;
        if (parsed.network && parsed.network !== '-') completeScore += 2;
        if (parsed.tls) completeScore += 1;
        score += completeScore;
        breakdown.completeness = completeScore;

        // Clamp to 100
        score = Math.max(5, Math.min(100, score));

        let level, label;
        if (score >= 75) { level = 'excellent'; label = 'عالی'; }
        else if (score >= 55) { level = 'good'; label = 'خوب'; }
        else if (score >= 35) { level = 'medium'; label = 'متوسط'; }
        else { level = 'poor'; label = 'ضعیف'; }

        return { score, level, label, breakdown, pingStatus: 'pending', pingMs: null };
    }

    // ============================================================
    // Source Reputation Scores
    // ============================================================
    const SOURCE_REPUTATION = {
        "EbraSha": 10,                    // Auto-tested every 30min
        "MrMohebi (Telegram Grabber)": 9, // Only active proxies
        "ShatakVPN (ConfigForge)": 9,     // Check-Host API tested
        "MahdiBland (Eternity)": 8,       // Speed-tested
        "MatinGhanbari": 7,
        "Epodonios": 7,
        "barry-far": 6,
        "4n0nymou3": 6,
        "Argh94 (V2RayAutoConfig)": 6,
        "Pawdroid": 5
    };

    function applySourceReputation(config) {
        const rep = SOURCE_REPUTATION[config.source] || 5;
        config.quality.breakdown.sourceReputation = rep;
        config.quality.score = Math.min(100, config.quality.score + rep);
        // Recalculate level
        const s = config.quality.score;
        if (s >= 75) { config.quality.level = 'excellent'; config.quality.label = 'عالی'; }
        else if (s >= 55) { config.quality.level = 'good'; config.quality.label = 'خوب'; }
        else if (s >= 35) { config.quality.level = 'medium'; config.quality.label = 'متوسط'; }
        else { config.quality.level = 'poor'; config.quality.label = 'ضعیف'; }
    }

    // ============================================================
    // Real TCP Ping Test
    // ============================================================
    async function pingServer(host, port, timeout = 5000) {
        // We test reachability by trying to fetch/connect
        // Using image load trick for TCP connectivity test
        if (!host || host === 'Unknown' || host === '') return { alive: false, ms: null };

        const portNum = parseInt(port) || 443;
        const start = performance.now();

        try {
            // Method 1: WebSocket test (works for ws/wss ports)
            if (portNum === 443 || portNum === 8443) {
                const controller = new AbortController();
                const timer = setTimeout(() => controller.abort(), timeout);

                try {
                    await fetch(`https://${host}:${portNum}/`, {
                        method: 'HEAD',
                        mode: 'no-cors',
                        signal: controller.signal
                    });
                    clearTimeout(timer);
                    const ms = Math.round(performance.now() - start);
                    return { alive: true, ms };
                } catch (e) {
                    clearTimeout(timer);
                    if (e.name === 'AbortError') {
                        return { alive: false, ms: null };
                    }
                    // Connection refused/blocked = server exists but port might not serve HTTP
                    const ms = Math.round(performance.now() - start);
                    if (ms < timeout - 100) {
                        return { alive: true, ms }; // Got a quick response (even error = alive)
                    }
                    return { alive: false, ms: null };
                }
            }

            // Method 2: HTTP test for port 80
            if (portNum === 80 || portNum === 8080 || portNum === 8880) {
                const controller = new AbortController();
                const timer = setTimeout(() => controller.abort(), timeout);

                try {
                    await fetch(`http://${host}:${portNum}/`, {
                        method: 'HEAD',
                        mode: 'no-cors',
                        signal: controller.signal
                    });
                    clearTimeout(timer);
                    const ms = Math.round(performance.now() - start);
                    return { alive: true, ms };
                } catch (e) {
                    clearTimeout(timer);
                    if (e.name === 'AbortError') return { alive: false, ms: null };
                    const ms = Math.round(performance.now() - start);
                    if (ms < timeout - 100) return { alive: true, ms };
                    return { alive: false, ms: null };
                }
            }

            // Method 3: Generic fetch for other ports
            const controller = new AbortController();
            const timer = setTimeout(() => controller.abort(), timeout);
            try {
                await fetch(`https://${host}:${portNum}/`, {
                    method: 'HEAD',
                    mode: 'no-cors',
                    signal: controller.signal
                });
                clearTimeout(timer);
                const ms = Math.round(performance.now() - start);
                return { alive: true, ms };
            } catch (e) {
                clearTimeout(timer);
                if (e.name === 'AbortError') return { alive: false, ms: null };
                const ms = Math.round(performance.now() - start);
                if (ms < timeout - 100) return { alive: true, ms };
                return { alive: false, ms: null };
            }

        } catch {
            return { alive: false, ms: null };
        }
    }

    // Batch ping configs (limited concurrency)
    let pingProgress = 0;
    let pingTotal = 0;

    async function batchPingConfigs(configs, concurrency = 15) {
        pingProgress = 0;
        pingTotal = configs.length;
        updatePingProgressUI();

        const queue = [...configs];
        const workers = [];

        for (let i = 0; i < concurrency; i++) {
            workers.push((async () => {
                while (queue.length > 0) {
                    const config = queue.shift();
                    if (!config) break;

                    try {
                        const result = await pingServer(config.address, config.port, 4000);
                        config.quality.pingStatus = result.alive ? 'alive' : 'dead';
                        config.quality.pingMs = result.ms;

                        // Adjust score based on ping
                        if (result.alive) {
                            if (result.ms <= 100) config.quality.score = Math.min(100, config.quality.score + 15);
                            else if (result.ms <= 300) config.quality.score = Math.min(100, config.quality.score + 10);
                            else if (result.ms <= 800) config.quality.score = Math.min(100, config.quality.score + 5);
                            else config.quality.score = Math.min(100, config.quality.score + 2);
                        } else {
                            config.quality.score = Math.max(5, config.quality.score - 20);
                        }

                        // Recalculate level
                        const s = config.quality.score;
                        if (s >= 75) { config.quality.level = 'excellent'; config.quality.label = 'عالی'; }
                        else if (s >= 55) { config.quality.level = 'good'; config.quality.label = 'خوب'; }
                        else if (s >= 35) { config.quality.level = 'medium'; config.quality.label = 'متوسط'; }
                        else { config.quality.level = 'poor'; config.quality.label = 'ضعیف'; }
                    } catch {}

                    pingProgress++;
                    if (pingProgress % 10 === 0 || pingProgress === pingTotal) {
                        updatePingProgressUI();
                    }
                }
            })());
        }

        await Promise.all(workers);

        // Final re-render
        applyFilters();
        updateStats();
        showToast(`تست پینگ ${pingTotal} کانفیگ تمام شد ✅`);
        hidePingProgress();
    }

    function updatePingProgressUI() {
        const el = document.getElementById('pingProgressContainer');
        if (!el) return;
        const pct = pingTotal > 0 ? Math.round((pingProgress / pingTotal) * 100) : 0;
        el.innerHTML = `
            <div style="display:flex; align-items:center; gap:12px; padding:14px 22px; background:var(--bg-card); border:1px solid var(--accent-cyan); border-radius:14px; margin-bottom:20px;">
                <div class="loading-spinner" style="width:24px;height:24px;border-width:2px;margin:0;flex-shrink:0;"></div>
                <div style="flex:1;">
                    <div style="font-size:0.88em;color:var(--text-primary);margin-bottom:6px;">🔍 تست پینگ واقعی سرورها... (${pingProgress}/${pingTotal})</div>
                    <div style="width:100%;height:4px;background:var(--border-color);border-radius:2px;overflow:hidden;">
                        <div style="width:${pct}%;height:100%;background:var(--gradient-2);border-radius:2px;transition:width 0.3s;"></div>
                    </div>
                </div>
                <span style="font-size:0.82em;color:var(--accent-cyan);font-weight:700;">${pct}%</span>
            </div>
        `;
    }

    function hidePingProgress() {
        const el = document.getElementById('pingProgressContainer');
        if (el) el.innerHTML = '';
    }

    // ============================================================
    // Start Ping Test Button Handler
    // ============================================================
    async function startPingTest() {
        if (allConfigs.length === 0) {
            showToast('ابتدا کانفیگ‌ها رو بارگذاری کنید!');
            return;
        }
        const btn = document.getElementById('pingTestBtn');
        btn.disabled = true;
        btn.innerHTML = '⏳ در حال تست...';
        btn.style.opacity = '0.6';

        await batchPingConfigs(allConfigs, 20);

        btn.disabled = false;
        btn.innerHTML = '🔍 تست پینگ واقعی';
        btn.style.opacity = '1';
    }

    // ============================================================
    // Fetch Configs from a URL using multiple CORS proxies
    // ============================================================
    const CORS_PROXIES = [
        url => `https://api.allorigins.win/raw?url=${encodeURIComponent(url)}`,
        url => `https://corsproxy.io/?${encodeURIComponent(url)}`,
        url => `https://api.codetabs.com/v1/proxy?quest=${encodeURIComponent(url)}`,
    ];

    async function fetchWithProxy(url, timeout = 12000) {
        // First try direct
        const attempts = [
            () => fetch(url, { signal: AbortSignal.timeout(timeout) }),
            ...CORS_PROXIES.map(proxy => () => fetch(proxy(url), { signal: AbortSignal.timeout(timeout) }))
        ];

        for (const attempt of attempts) {
            try {
                const resp = await attempt();
                if (resp.ok) {
                    const text = await resp.text();
                    if (text && text.length > 10) return text;
                }
            } catch {}
        }
        return null;
    }

    // ============================================================
    // Fetch all configs
    // ============================================================
    async function fetchAllConfigs() {
        const container = document.getElementById('configsContainer');
        const refreshBtn = document.querySelector('.refresh-btn');
        refreshBtn.classList.add('loading');

        container.innerHTML = `
            <div class="loading-state" id="loadingState">
                <div class="loading-spinner"></div>
                <p>در حال دریافت کانفیگ‌ها از مخازن GitHub...</p>
                <div class="loading-progress">
                    <div class="loading-progress-bar" id="loadingProgressBar"></div>
                </div>
                <p style="margin-top: 10px; font-size: 0.8em; color: var(--text-muted);" id="loadingStatus">آماده‌سازی...</p>
            </div>
        `;

        allConfigs = [];
        const totalURLs = SOURCES.reduce((sum, s) => sum + s.urls.length, 0);
        let completedURLs = 0;
        let sourceResults = {};

        // Initialize subscription links
        renderSubLinks();

        // Fetch all sources concurrently
        const sourcePromises = SOURCES.map(async (source) => {
            sourceResults[source.name] = [];

            const urlPromises = source.urls.map(async (url) => {
                try {
                    const text = await fetchWithProxy(url);
                    if (text) {
                        // Check if base64 encoded
                        let content = text;
                        if (!text.includes('://') && text.length > 50) {
                            try {
                                const decoded = atob(text.trim());
                                if (decoded.includes('://')) content = decoded;
                            } catch {}
                        }

                        const lines = content.split('\n');
                        for (const line of lines) {
                            const config = parseConfigLine(line);
                            if (config) {
                                config.source = source.name;
                                config.sourceColor = source.color;
                                config.sourceIcon = source.icon;
                                sourceResults[source.name].push(config);
                            }
                        }
                    }
                } catch {}

                completedURLs++;
                const progress = (completedURLs / totalURLs) * 100;
                const progressBar = document.getElementById('loadingProgressBar');
                const statusEl = document.getElementById('loadingStatus');
                if (progressBar) progressBar.style.width = progress + '%';
                if (statusEl) statusEl.textContent = `دریافت از ${source.name}... (${completedURLs}/${totalURLs})`;
            });

            await Promise.all(urlPromises);
        });

        await Promise.all(sourcePromises);

        // Combine all configs
        for (const [sourceName, configs] of Object.entries(sourceResults)) {
            allConfigs.push(...configs);
        }

        // Deduplicate based on raw config
        const seen = new Set();
        allConfigs = allConfigs.filter(c => {
            if (seen.has(c.raw)) return false;
            seen.add(c.raw);
            return true;
        });

        // Apply source reputation to quality scores
        allConfigs.forEach(c => applySourceReputation(c));

        refreshBtn.classList.remove('loading');
        updateStats();
        updateProtocolFilters();
        applyFilters();

        // Update last update time
        const now = new Date();
        document.getElementById('lastUpdate').innerHTML = `
            <span class="dot"></span>
            <span>آخرین بارگذاری: ${now.toLocaleTimeString('fa-IR')} — ${allConfigs.length} کانفیگ یافت شد</span>
        `;
    }

    // ============================================================
    // Update Stats
    // ============================================================
    function updateStats() {
        document.getElementById('totalConfigs').textContent = allConfigs.length.toLocaleString('fa-IR');
        
        const sourcesUsed = new Set(allConfigs.map(c => c.source));
        document.getElementById('totalSources').textContent = sourcesUsed.size.toLocaleString('fa-IR');
        
        const protocols = new Set(allConfigs.map(c => c.protocol));
        document.getElementById('activeConfigs').textContent = protocols.size.toLocaleString('fa-IR');

        const countries = new Set(allConfigs.map(c => c.country.code).filter(c => c !== '??'));
        document.getElementById('countriesCount').textContent = countries.size.toLocaleString('fa-IR');

        // Ping stats
        const alive = allConfigs.filter(c => c.quality.pingStatus === 'alive');
        const aliveEl = document.getElementById('aliveCount');
        if (aliveEl) {
            aliveEl.textContent = alive.length > 0 ? alive.length.toLocaleString('fa-IR') : '-';
        }

        const pingsWithMs = alive.filter(c => c.quality.pingMs !== null);
        const avgPingEl = document.getElementById('avgPing');
        if (avgPingEl) {
            if (pingsWithMs.length > 0) {
                const avg = Math.round(pingsWithMs.reduce((sum, c) => sum + c.quality.pingMs, 0) / pingsWithMs.length);
                avgPingEl.textContent = avg + 'ms';
            } else {
                avgPingEl.textContent = '-';
            }
        }
    }

    // ============================================================
    // Protocol Filters
    // ============================================================
    function updateProtocolFilters() {
        protocolCounts = {};
        allConfigs.forEach(c => {
            protocolCounts[c.protocol] = (protocolCounts[c.protocol] || 0) + 1;
        });

        const container = document.getElementById('protocolFilters');
        let html = `
            <button class="filter-btn ${currentFilter === 'all' ? 'active' : ''}" data-filter="all" onclick="setFilter('all', this)">
                همه <span class="count">${allConfigs.length}</span>
            </button>
        `;

        const protocolLabels = {
            vmess: 'VMess',
            vless: 'VLESS',
            trojan: 'Trojan',
            ss: 'Shadowsocks',
            ssr: 'SSR',
            hysteria2: 'Hysteria2',
            tuic: 'TUIC'
        };

        for (const [proto, count] of Object.entries(protocolCounts).sort((a, b) => b[1] - a[1])) {
            html += `
                <button class="filter-btn ${currentFilter === proto ? 'active' : ''}" 
                        data-filter="${proto}" onclick="setFilter('${proto}', this)">
                    ${protocolLabels[proto] || proto.toUpperCase()} 
                    <span class="count">${count}</span>
                </button>
            `;
        }

        container.innerHTML = html;
    }

    function setFilter(filter, btn) {
        currentFilter = filter;
        document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
        applyFilters();
    }

    // ============================================================
    // Apply Filters & Sorting & Render
    // ============================================================
    function applyFilters() {
        let filtered = [...allConfigs];

        // Protocol filter
        if (currentFilter !== 'all') {
            filtered = filtered.filter(c => c.protocol === currentFilter);
        }

        // Search filter
        const search = document.getElementById('searchBox').value.toLowerCase().trim();
        if (search) {
            filtered = filtered.filter(c =>
                c.name.toLowerCase().includes(search) ||
                c.address.toLowerCase().includes(search) ||
                c.country.name.includes(search) ||
                c.protocol.includes(search) ||
                c.network.toLowerCase().includes(search)
            );
        }

        // Sort
        const sortBy = document.getElementById('sortSelect').value;
        switch (sortBy) {
            case 'quality-desc':
                filtered.sort((a, b) => b.quality.score - a.quality.score);
                break;
            case 'quality-asc':
                filtered.sort((a, b) => a.quality.score - b.quality.score);
                break;
            case 'ping-asc':
                filtered.sort((a, b) => {
                    const aMs = a.quality.pingMs ?? 99999;
                    const bMs = b.quality.pingMs ?? 99999;
                    return aMs - bMs;
                });
                break;
            case 'ping-desc':
                filtered.sort((a, b) => {
                    const aMs = a.quality.pingMs ?? 0;
                    const bMs = b.quality.pingMs ?? 0;
                    return bMs - aMs;
                });
                break;
            case 'protocol':
                filtered.sort((a, b) => a.protocol.localeCompare(b.protocol));
                break;
            case 'country':
                filtered.sort((a, b) => a.country.name.localeCompare(b.country.name));
                break;
            case 'alive-first':
                filtered.sort((a, b) => {
                    const aAlive = a.quality.pingStatus === 'alive' ? 0 : a.quality.pingStatus === 'pending' ? 1 : 2;
                    const bAlive = b.quality.pingStatus === 'alive' ? 0 : b.quality.pingStatus === 'pending' ? 1 : 2;
                    if (aAlive !== bAlive) return aAlive - bAlive;
                    return b.quality.score - a.quality.score;
                });
                break;
        }

        renderConfigs(filtered);
    }

    // ============================================================
    // Render
    // ============================================================
    function renderConfigs(configs) {
        const container = document.getElementById('configsContainer');

        if (configs.length === 0) {
            container.innerHTML = `
                <div class="empty-state">
                    <div class="empty-icon">📭</div>
                    <p>هیچ کانفیگی یافت نشد</p>
                </div>
            `;
            return;
        }

        // Reset rendered configs index
        renderedConfigs = [];

        // Group by source
        const bySource = {};
        configs.forEach(c => {
            if (!bySource[c.source]) bySource[c.source] = [];
            bySource[c.source].push(c);
        });

        let html = '';

        for (const [sourceName, sourceConfigs] of Object.entries(bySource)) {
            const source = SOURCES.find(s => s.name === sourceName) || { icon: '📦', color: '#64748b', desc: '' };

            html += `
                <div class="source-section" id="source-${sourceName.replace(/[^a-zA-Z0-9]/g, '')}">
                    <div class="source-header" onclick="toggleSource(this)" style="border-right: 3px solid ${source.color}">
                        <div class="source-icon" style="background: ${source.color}22; color: ${source.color}">
                            ${source.icon}
                        </div>
                        <div class="source-info">
                            <div class="source-name">${sourceName}</div>
                            <div class="source-desc">${source.desc}</div>
                        </div>
                        <div class="source-badge" style="background: ${source.color}22; color: ${source.color}">
                            ${sourceConfigs.length} کانفیگ
                        </div>
                        <div class="toggle-icon">▼</div>
                    </div>
                    <div class="source-configs">
            `;

            sourceConfigs.forEach((config, idx) => {
                html += renderConfigCard(config, idx);
            });

            html += `
                    </div>
                </div>
            `;
        }

        container.innerHTML = html;
    }

    // Store configs for safe reference by index
    let renderedConfigs = [];

    function renderConfigCard(config, idx) {
        const displayName = config.name || `${config.protocol.toUpperCase()} #${idx + 1}`;
        const truncatedName = displayName.length > 60 ? displayName.substring(0, 60) + '...' : displayName;

        // Store config by global index for safe onclick access
        const globalIdx = renderedConfigs.length;
        renderedConfigs.push(config);

        let pingHtml = '';
        if (config.quality.pingStatus === 'alive') {
            pingHtml = '<span style="font-size:0.68em;color:var(--accent-green);">🟢 ' + config.quality.pingMs + 'ms</span>';
        } else if (config.quality.pingStatus === 'dead') {
            pingHtml = '<span style="font-size:0.68em;color:var(--accent-red);">🔴 آفلاین</span>';
        } else {
            pingHtml = '<span style="font-size:0.68em;color:var(--text-muted);">⏳ تست نشده</span>';
        }

        return `
            <div class="config-card">
                <div class="config-protocol">
                    <span class="protocol-badge ${config.protocol}">${config.protocol.toUpperCase()}</span>
                    <span class="country-flag" title="${config.country.name}">${config.country.flag}</span>
                </div>
                <div class="config-details">
                    <div class="config-name" title="${escapeHtml(displayName)}">${escapeHtml(truncatedName)}</div>
                    <div class="config-meta">
                        <span>🖥️ ${escapeHtml(config.address)}</span>
                        <span>🔌 ${config.port}</span>
                        <span>🌐 ${config.network}</span>
                        <span>${config.tls === 'tls' || config.tls === 'reality' ? '🔒 ' + config.tls : '🔓 بدون TLS'}</span>
                        <span>🏳️ ${config.country.name}</span>
                    </div>
                </div>
                <div class="config-quality quality-${config.quality.level}">
                    <div class="quality-bar-container">
                        <div class="quality-bar" style="width: ${config.quality.score}%"></div>
                    </div>
                    <span class="quality-label">${config.quality.label} (${config.quality.score}%)</span>
                    ${pingHtml}
                </div>
                <div class="config-actions">
                    <button class="copy-btn" onclick="copyByIndex(this, ${globalIdx})">
                        📋 کپی
                    </button>
                    <button class="qr-btn" onclick="showQRByIndex(${globalIdx})">
                        📱 QR
                    </button>
                </div>
            </div>
        `;
    }

    // ============================================================
    // Toggle Source
    // ============================================================
    function toggleSource(header) {
        const section = header.parentElement;
        section.classList.toggle('collapsed');
    }

    // ============================================================
    // Copy & QR by Index (safe - no special char issues)
    // ============================================================
    function copyByIndex(btn, idx) {
        const text = renderedConfigs[idx]?.raw || '';
        copyToClipboard(text, btn);
    }

    function showQRByIndex(idx) {
        const text = renderedConfigs[idx]?.raw || '';
        if (text) showQR(text);
    }

    function copyToClipboard(text, btn) {
        if (!text) return;
        navigator.clipboard.writeText(text).then(() => {
            onCopySuccess(btn);
        }).catch(() => {
            // Fallback
            const ta = document.createElement('textarea');
            ta.value = text;
            ta.style.position = 'fixed';
            ta.style.left = '-9999px';
            document.body.appendChild(ta);
            ta.select();
            try { document.execCommand('copy'); } catch {}
            document.body.removeChild(ta);
            onCopySuccess(btn);
        });
    }

    function onCopySuccess(btn) {
        if (!btn) return;
        btn.classList.add('copied');
        btn.innerHTML = '✅ کپی شد';
        showToast('کانفیگ با موفقیت کپی شد!');
        setTimeout(() => {
            btn.classList.remove('copied');
            btn.innerHTML = '📋 کپی';
        }, 2000);
    }

    function copyAllFiltered() {
        let filtered = [...allConfigs];
        if (currentFilter !== 'all') {
            filtered = filtered.filter(c => c.protocol === currentFilter);
        }
        const search = document.getElementById('searchBox').value.toLowerCase().trim();
        if (search) {
            filtered = filtered.filter(c =>
                c.name.toLowerCase().includes(search) ||
                c.address.toLowerCase().includes(search) ||
                c.country.name.includes(search)
            );
        }

        const allRaw = filtered.map(c => c.raw).join('\n');
        navigator.clipboard.writeText(allRaw).then(() => {
            showToast(`${filtered.length} کانفیگ کپی شد!`);
        }).catch(() => {
            const ta = document.createElement('textarea');
            ta.value = allRaw;
            document.body.appendChild(ta);
            ta.select();
            document.execCommand('copy');
            document.body.removeChild(ta);
            showToast(`${filtered.length} کانفیگ کپی شد!`);
        });
    }

    function copySubLink(btn, url) {
        navigator.clipboard.writeText(url).then(() => {
            btn.textContent = '✅ کپی شد';
            showToast('لینک اشتراک کپی شد!');
            setTimeout(() => { btn.textContent = '📋 کپی'; }, 2000);
        });
    }

    // ============================================================
    // QR Code (supports both qrcode.js libraries)
    // ============================================================
    function showQR(text) {
        const modal = document.getElementById('qrModal');
        const container = document.getElementById('qrContainer');
        modal.classList.add('show');
        container.innerHTML = '';

        let generated = false;

        // Method 1: qrcode npm package (QRCode.toCanvas)
        if (typeof QRCode !== 'undefined' && typeof QRCode.toCanvas === 'function') {
            try {
                const canvas = document.createElement('canvas');
                container.appendChild(canvas);
                QRCode.toCanvas(canvas, text, {
                    width: 220,
                    margin: 2,
                    color: { dark: '#000000', light: '#ffffff' }
                }, function(error) {
                    if (error) {
                        console.error('QR Error:', error);
                        container.innerHTML = '';
                        fallbackQR(container, text);
                    }
                });
                generated = true;
            } catch(e) {
                console.error('QR Method 1 failed:', e);
                container.innerHTML = '';
            }
        }

        // Method 2: qrcodejs library (new QRCode(element, text))
        if (!generated && typeof QRCode !== 'undefined' && typeof QRCode.toCanvas !== 'function') {
            try {
                const div = document.createElement('div');
                container.appendChild(div);
                new QRCode(div, {
                    text: text,
                    width: 220,
                    height: 220,
                    colorDark: '#000000',
                    colorLight: '#ffffff',
                    correctLevel: QRCode.CorrectLevel ? QRCode.CorrectLevel.L : 1
                });
                generated = true;
            } catch(e) {
                console.error('QR Method 2 failed:', e);
                container.innerHTML = '';
            }
        }

        // Method 3: API Fallback (always works)
        if (!generated) {
            fallbackQR(container, text);
        }
    }

    function fallbackQR(container, text) {
        // Use free QR code API as last resort
        const encodedText = encodeURIComponent(text);
        
        // Try multiple QR APIs
        const apis = [
            `https://api.qrserver.com/v1/create-qr-code/?size=220x220&data=${encodedText}`,
            `https://chart.googleapis.com/chart?cht=qr&chs=220x220&chl=${encodedText}`,
            `https://quickchart.io/qr?text=${encodedText}&size=220`
        ];

        const img = document.createElement('img');
        img.style.width = '220px';
        img.style.height = '220px';
        img.style.borderRadius = '8px';
        img.alt = 'QR Code';
        
        let apiIndex = 0;
        img.onerror = function() {
            apiIndex++;
            if (apiIndex < apis.length) {
                img.src = apis[apiIndex];
            } else {
                container.innerHTML = `
                    <div style="padding:20px;text-align:center;">
                        <p style="color:#666;font-size:0.85em;margin-bottom:10px;">QR Code در دسترس نیست</p>
                        <p style="color:#999;font-size:0.75em;">لینک رو کپی کنید و در اپ اسکن کنید</p>
                    </div>
                `;
            }
        };
        img.src = apis[0];
        container.appendChild(img);
    }

    function closeQR() {
        document.getElementById('qrModal').classList.remove('show');
    }

    // ============================================================
    // Toast
    // ============================================================
    function showToast(message) {
        const toast = document.getElementById('toast');
        document.getElementById('toastMessage').textContent = message;
        toast.classList.add('show');
        setTimeout(() => toast.classList.remove('show'), 3000);
    }

    // ============================================================
    // Subscription Links
    // ============================================================
    function renderSubLinks() {
        const subLinks = [
            { name: 'EbraSha (All)', url: 'https://raw.githubusercontent.com/ebrasha/free-v2ray-public-list/refs/heads/main/V2Ray-Config-By-EbraSha.txt' },
            { name: 'Epodonios (VMess)', url: 'https://raw.githubusercontent.com/Epodonios/v2ray-configs/main/Splitted-By-Protocol/vmess.txt' },
            { name: 'Epodonios (VLESS)', url: 'https://raw.githubusercontent.com/Epodonios/v2ray-configs/main/Splitted-By-Protocol/vless.txt' },
            { name: 'MatinGhanbari', url: 'https://raw.githubusercontent.com/MatinGhanbari/v2ray-configs/main/subscriptions/v2ray/super-sub.txt' },
            { name: 'barry-far (VLESS)', url: 'https://raw.githubusercontent.com/barry-far/V2ray-config/main/Splitted-By-Protocol/vless.txt' },
            { name: 'MahdiBland (Eternity)', url: 'https://raw.githubusercontent.com/mahdibland/ShadowsocksAggregator/master/Eternity.txt' },
            { name: 'ShatakVPN', url: 'https://raw.githubusercontent.com/ShatakVPN/ConfigForge-V2Ray/main/configs/all.txt' },
            { name: 'MrMohebi (Active)', url: 'https://raw.githubusercontent.com/MrMohebi/xray-proxy-grabber-telegram/master/collected-proxies/row-url/actives.txt' },
            { name: '4n0nymou3', url: 'https://raw.githubusercontent.com/4n0nymou3/multi-proxy-config-fetcher/refs/heads/main/configs/proxy_configs.txt' },
            { name: 'Pawdroid', url: 'https://raw.githubusercontent.com/Pawdroid/Free-servers/main/sub' },
        ];

        const grid = document.getElementById('subLinksGrid');
        grid.innerHTML = subLinks.map(link => `
            <div class="sub-link-item">
                <span class="sub-name">${link.name}</span>
                <span class="sub-url">${link.url}</span>
                <button class="copy-sub-btn" onclick="copySubLink(this, '${link.url}')">📋 کپی</button>
            </div>
        `).join('');
    }

    // ============================================================
    // Helpers
    // ============================================================
    function escapeHtml(str) {
        if (!str) return '';
        return str.replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;').replace(/"/g, '&quot;');
    }

    function escapeForAttr(str) {
        if (!str) return '';
        return str.replace(/\\/g, '\\\\').replace(/`/g, '\\`').replace(/\$/g, '\\$');
    }

    // ============================================================
    // Click outside modal
    // ============================================================
    document.getElementById('qrModal').addEventListener('click', function(e) {
        if (e.target === this) closeQR();
    });

    // ============================================================
    // Init
    // ============================================================
    document.addEventListener('DOMContentLoaded', () => {
        renderSubLinks();
        fetchAllConfigs();
    });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'a07ada924be323df',t:'MTc4MDc4NDk0NQ=='};var a=document.createElement('script');a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
