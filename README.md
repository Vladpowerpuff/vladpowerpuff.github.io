# vladpowerpuff.github.io
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Дисциплина — панель управления</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500;1,600&family=EB+Garamond:ital,wght@0,400;0,500;0,600;1,400;1,500&family=Cormorant:ital,wght@0,400;0,500;0,600;1,400;1,500&display=swap" rel="stylesheet">
    <style>
        :root {
			--green: #2E7D32;
            --bg: #FDFBF7;
            --surface: #FFFFFF;
            --surface-beige: #F5EFE6;
            --surface-beige-light: #FAF6EF;
            --surface-pink: #F8E5E5;
            --accent-gold: #A67C00;
            --accent-gold-dark: #8B6508;
            --accent-gold-light: #C49A2A;
            --accent-red: #CC0000;
            --text-primary: #333333;
            --text-secondary: #6B6560;
            --text-muted: #9A948C;
            --text-on-dark: #FDFBF7;
            --border-subtle: #E8E2D8;
            --border-strong: #D5CEC2;
            --shadow-sm: 0 1px 3px rgba(51, 51, 51, 0.04), 0 1px 2px rgba(51, 51, 51, 0.03);
            --shadow-md: 0 4px 12px rgba(51, 51, 51, 0.06), 0 2px 4px rgba(51, 51, 51, 0.04);
            --shadow-lg: 0 8px 24px rgba(51, 51, 51, 0.08), 0 4px 8px rgba(51, 51, 51, 0.05);
            --radius-sm: 8px;
            --radius-md: 10px;
            --radius-lg: 12px;
            --font-display: 'Playfair Display', 'EB Garamond', 'Cormorant', Georgia, 'Times New Roman', serif;
            --font-body: 'EB Garamond', 'Cormorant', Georgia, 'Times New Roman', serif;
            --letter-spacing-wide: 0.08em;
            --letter-spacing-wider: 0.12em;
            --letter-spacing-widest: 0.18em;
            --transition: 0.25s cubic-bezier(0.4, 0, 0.2, 1);
            --blue: #6B8CAE;
            --blue-dark: #55708A;
        }

        *,
        *::before,
        *::after {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            font-size: 16px;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        body {
            font-family: var(--font-body);
            background-color: var(--bg);
            color: var(--text-primary);
            min-height: 100vh;
            line-height: 1.5;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        ::-webkit-scrollbar {
            width: 6px;
        }
        ::-webkit-scrollbar-track {
            background: var(--bg);
        }
        ::-webkit-scrollbar-thumb {
            background: var(--border-strong);
            border-radius: 3px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: var(--text-muted);
        }

        .container {
            width: 100%;
            max-width: 720px;
            padding: 32px 28px 48px;
            display: flex;
            flex-direction: column;
            gap: 24px;
            transition: opacity 0.3s ease;
        }

        @media (max-width: 600px) {
            .container {
                padding: 20px 16px 36px;
                gap: 18px;
            }
        }

        .page {
            display: none;
            flex-direction: column;
            gap: 20px;
        }

        .page.active {
            display: flex;
            animation: fadeInPage 0.3s ease-out;
        }

        @keyframes fadeInPage {
            from { opacity: 0; transform: translateY(8px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding-bottom: 18px;
            border-bottom: 1px solid var(--border-subtle);
        }

        .logo {
            font-family: var(--font-display);
            font-size: 1.6rem;
            font-weight: 600;
            letter-spacing: 0.04em;
            color: var(--accent-gold);
            cursor: pointer;
            user-select: none;
            transition: var(--transition);
        }
        .logo:hover { color: var(--accent-gold-dark); }

        .header-icons {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .header-icon-btn {
            background: none;
            border: 1px solid var(--border-subtle);
            border-radius: 50%;
            width: 36px;
            height: 36px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            color: var(--text-secondary);
            transition: var(--transition);
            font-size: 0;
        }

        .header-icon-btn:hover {
            border-color: var(--accent-gold);
            color: var(--accent-gold);
            background: var(--surface);
            box-shadow: var(--shadow-sm);
        }
        .header-icon-btn svg {
            width: 16px;
            height: 16px;
            stroke: currentColor;
            fill: none;
            stroke-width: 1.8;
            stroke-linecap: round;
            stroke-linejoin: round;
        }

        .nav {
            display: flex;
            align-items: center;
            gap: 4px;
            flex-wrap: wrap;
            padding: 4px 0;
            border-bottom: 1px solid var(--border-subtle);
            padding-bottom: 12px;
        }

        .nav-item {
            display: flex;
            align-items: center;
            gap: 6px;
            padding: 8px 12px;
            border-radius: 6px;
            font-family: var(--font-display);
            font-size: 0.65rem;
            font-weight: 600;
            letter-spacing: var(--letter-spacing-wide);
            text-transform: uppercase;
            color: var(--text-muted);
            cursor: pointer;
            transition: var(--transition);
            position: relative;
            white-space: nowrap;
            background: none;
            border: none;
            font-family: var(--font-display);
            font-size: 0.65rem;
            font-weight: 600;
            letter-spacing: var(--letter-spacing-wide);
            text-transform: uppercase;
        }

        .nav-item svg {
            width: 14px;
            height: 14px;
            stroke: currentColor;
            fill: none;
            stroke-width: 1.6;
            stroke-linecap: round;
            stroke-linejoin: round;
            flex-shrink: 0;
        }

        .nav-item:hover {
            color: var(--text-primary);
            background: var(--surface-beige-light);
        }
        .nav-item.active {
            color: var(--accent-gold);
            background: transparent;
        }
        .nav-item.active::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 12px;
            right: 12px;
            height: 2px;
            background: var(--accent-gold);
            border-radius: 1px;
        }

        .card {
            background: var(--surface);
            border-radius: var(--radius-lg);
            border: 1px solid var(--border-subtle);
            box-shadow: var(--shadow-md);
            padding: 24px 28px;
            transition: var(--transition);
        }

        .section-title {
            font-family: var(--font-display);
            font-size: 0.6rem;
            font-weight: 600;
            letter-spacing: var(--letter-spacing-widest);
            text-transform: uppercase;
            color: var(--text-muted);
            margin-bottom: 14px;
        }

        .btn {
            background: var(--accent-gold);
            color: var(--text-on-dark);
            border: none;
            border-radius: var(--radius-sm);
            padding: 10px 22px;
            font-family: var(--font-display);
            font-size: 0.65rem;
            font-weight: 600;
            letter-spacing: var(--letter-spacing-wide);
            text-transform: uppercase;
            cursor: pointer;
            transition: var(--transition);
            white-space: nowrap;
            box-shadow: 0 2px 6px rgba(166, 124, 0, 0.25);
        }
        .btn:hover {
            background: var(--accent-gold-dark);
            box-shadow: 0 4px 12px rgba(166, 124, 0, 0.35);
            transform: translateY(-1px);
        }
        .btn:active { transform: translateY(0); }
        .btn-outline {
            background: transparent;
            border: 1px solid var(--border-strong);
            color: var(--text-secondary);
            box-shadow: none;
        }
        .btn-outline:hover {
            background: var(--surface-beige-light);
            border-color: var(--accent-gold);
            color: var(--accent-gold);
            box-shadow: none;
            transform: translateY(-1px);
        }
        .btn-danger {
            background: var(--accent-red);
            box-shadow: 0 2px 6px rgba(204, 0, 0, 0.25);
        }
        .btn-danger:hover { background: #A00000; }

        .today-card {
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 16px;
        }
        .today-left { display: flex; flex-direction: column; gap: 4px; }
        .today-label {
            font-family: var(--font-display);
            font-size: 0.6rem;
            font-weight: 600;
            letter-spacing: var(--letter-spacing-widest);
            text-transform: uppercase;
            color: var(--text-muted);
        }
        .today-date {
            font-family: var(--font-display);
            font-size: 1.2rem;
            font-weight: 500;
            color: var(--text-primary);
        }
        .status-pill {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            background: var(--surface-beige);
            border: 1px solid var(--border-subtle);
            border-radius: 100px;
            padding: 5px 14px;
            font-family: var(--font-display);
            font-size: 0.58rem;
            font-weight: 600;
            letter-spacing: var(--letter-spacing-wide);
            text-transform: uppercase;
            color: var(--text-secondary);
            cursor: pointer;
            transition: var(--transition);
            white-space: nowrap;
            user-select: none;
        }
        .status-pill .dot {
            width: 6px;
            height: 6px;
            border-radius: 50%;
            background: var(--text-muted);
            flex-shrink: 0;
        }
        .status-pill.locked .dot {
            background: var(--accent-gold);
            box-shadow: 0 0 0 2px rgba(166, 124, 0, 0.15);
        }
        .status-pill.partial .dot {
            background: linear-gradient(135deg, var(--accent-gold) 50%, var(--text-muted) 50%);
        }

        .banner {
            background: var(--surface-pink);
            border-radius: var(--radius-lg);
            padding: 36px 32px;
            text-align: center;
            border: 1px solid rgba(204, 0, 0, 0.06);
            box-shadow: var(--shadow-sm);
        }
        .banner-text {
            font-family: var(--font-display);
            font-size: 1.5rem;
            font-weight: 500;
            line-height: 1.4;
            color: var(--text-primary);
        }
        .banner-number {
            color: var(--accent-red);
            font-weight: 700;
            font-size: 1.5rem;
            font-variant-numeric: tabular-nums;
        }
        .banner-inline-red {
            color: var(--accent-red);
            font-weight: 700;
        }
        @media (max-width: 600px) {
            .banner-text { font-size: 1.2rem; }
            .banner-number { font-size: 1.2rem; }
        }

        .warden-card {
            background: var(--surface-beige-light);
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-lg);
            padding: 24px 28px;
            box-shadow: var(--shadow-sm);
        }
        .warden-quote {
            font-family: var(--font-display);
            font-style: italic;
            font-size: 1.15rem;
            line-height: 1.6;
        }
        .warden-quote::before {
            content: '\201C';
            color: var(--accent-gold);
            font-size: 1.8rem;
            vertical-align: -0.2em;
            margin-right: 4px;
            opacity: 0.6;
        }
        .warden-quote::after {
            content: '\201D';
            color: var(--accent-gold);
            font-size: 1.8rem;
            vertical-align: -0.45em;
            margin-left: 4px;
            opacity: 0.6;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
        }
        @media (max-width: 520px) { .stats-grid { grid-template-columns: 1fr; } }
        .stat-card {
            background: var(--surface);
            border-radius: var(--radius-lg);
            border: 1px solid var(--border-subtle);
            box-shadow: var(--shadow-sm);
            padding: 22px 24px;
            display: flex;
            flex-direction: column;
            gap: 8px;
        }
        .stat-label {
            font-family: var(--font-display);
            font-size: 0.6rem;
            font-weight: 600;
            letter-spacing: var(--letter-spacing-widest);
            text-transform: uppercase;
            color: var(--text-muted);
        }
        .stat-number {
            font-family: var(--font-display);
            font-size: 2.8rem;
            font-weight: 600;
            line-height: 1.1;
            color: var(--text-primary);
            font-variant-numeric: tabular-nums;
        }
        .stat-sub { font-size: 0.9rem; color: var(--text-secondary); }
        .progress-bar {
            margin-top: 4px;
            width: 100%;
            height: 4px;
            background: var(--surface-beige);
            border-radius: 2px;
            overflow: hidden;
        }
        .progress-bar-fill {
            height: 100%;
            border-radius: 2px;
            background: linear-gradient(90deg, var(--accent-gold-light), var(--accent-gold));
            transition: width 0.6s;
        }
        .stat-text-highlight { color: var(--accent-gold); font-weight: 600; }

        .pinned-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
        .pinned-subcard {
            background: var(--surface-beige-light);
            border-radius: var(--radius-md);
            padding: 16px 18px;
            text-align: center;
            border: 1px solid var(--border-subtle);
            box-shadow: var(--shadow-sm);
        }
        .pinned-label {
            font-size: 0.6rem;
            text-transform: uppercase;
            letter-spacing: var(--letter-spacing-wider);
            color: var(--text-muted);
        }
        .pinned-number {
            font-family: var(--font-display);
            font-size: 2.5rem;
            font-weight: 600;
            line-height: 1.2;
            margin: 6px 0 2px;
        }
        .pinned-sub { font-size: 0.8rem; color: var(--text-secondary); }

        .lock-stats-row { display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; }
        .lock-stat-card {
            background: var(--surface-beige-light);
            border-radius: var(--radius-md);
            padding: 16px;
            text-align: center;
            border: 1px solid var(--border-subtle);
        }
        .lock-stat-label {
            font-size: 0.6rem;
            text-transform: uppercase;
            letter-spacing: var(--letter-spacing-wider);
            color: var(--text-muted);
        }
        .lock-stat-number {
            font-family: var(--font-display);
            font-size: 1.8rem;
            font-weight: 600;
            margin: 6px 0 2px;
        }
        .lock-stat-number.gold { color: var(--accent-gold); }
        .lock-stat-sub { font-size: 0.75rem; color: var(--text-secondary); }

        .heatmap-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 16px;
        }
        .heatmap-nav { display: flex; align-items: center; gap: 8px; }
        .heatmap-year {
            font-family: var(--font-display);
            font-size: 1.4rem;
            font-weight: 600;
            color: var(--accent-gold);
            min-width: 60px;
            text-align: center;
        }
        .heatmap-btn {
            background: none;
            border: 1px solid var(--border-subtle);
            border-radius: 4px;
            width: 28px;
            height: 28px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            color: var(--text-secondary);
            transition: var(--transition);
        }
        .heatmap-btn:hover { border-color: var(--accent-gold); color: var(--accent-gold); }
        .heatmap-btn svg {
            width: 14px;
            height: 14px;
            stroke: currentColor;
            fill: none;
            stroke-width: 1.8;
            stroke-linecap: round;
            stroke-linejoin: round;
        }
        .heatmap-months {
            display: grid;
            grid-template-columns: repeat(6, 1fr);
            gap: 12px;
        }
        @media (max-width: 600px) { .heatmap-months { grid-template-columns: repeat(3, 1fr); } }
        .heatmap-month {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 4px;
        }
        .heatmap-month-label {
            font-size: 0.55rem;
            text-transform: uppercase;
            letter-spacing: var(--letter-spacing-wider);
            color: var(--text-muted);
            font-family: var(--font-display);
            font-weight: 600;
        }
        .heatmap-squares {
            display: grid;
            grid-template-columns: repeat(3, 14px);
            gap: 2px;
            justify-content: center;
        }
        .heatmap-square {
            width: 14px;
            height: 14px;
            border-radius: 2px;
            background: var(--surface-beige);
            border: 1px solid var(--border-subtle);
            cursor: pointer;
            transition: all 0.2s;
        }
        .heatmap-square.gold { background: var(--accent-gold); border-color: var(--accent-gold-dark); }
        .heatmap-square.blue { background: var(--blue); border-color: var(--blue-dark); }
        .heatmap-square.gray {
            background: rgba(220, 215, 205, 0.4);
            border-color: rgba(200, 195, 185, 0.3);
            cursor: default;
        }
        .heatmap-square.partial {
            background: linear-gradient(135deg, var(--accent-gold) 50%, var(--surface-beige) 50%);
            border-color: var(--accent-gold-dark);
        }
        .heatmap-square:hover { transform: scale(1.25); z-index: 2; }
        .heatmap-legend {
            display: flex;
            align-items: center;
            gap: 16px;
            margin-top: 16px;
            flex-wrap: wrap;
            font-size: 0.7rem;
            color: var(--text-secondary);
        }
        .legend-item { display: flex; align-items: center; gap: 6px; }
        .legend-square { width: 12px; height: 12px; border-radius: 2px; background: var(--accent-gold); }
        .legend-square.blue { background: var(--blue); }
        .legend-square.gray {
            background: rgba(220, 215, 205, 0.4);
            border: 1px solid rgba(200, 195, 185, 0.3);
        }
        .legend-square.partial {
            background: linear-gradient(135deg, var(--accent-gold) 50%, var(--surface-beige) 50%);
        }
        .legend-circle { width: 12px; height: 12px; border-radius: 50%; background: var(--accent-red); }

        .donut-chart-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 16px;
        }
        .donut-chart {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            background: conic-gradient(var(--accent-gold) 0% 0%, var(--blue) 0% 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            flex-shrink: 0;
        }
        .donut-hole {
            width: 130px;
            height: 130px;
            background: var(--surface);
            border-radius: 50%;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            font-family: var(--font-display);
        }
        .donut-hole span:first-child {
            font-size: 1.4rem;
            font-weight: 600;
            color: var(--text-primary);
        }
        .donut-label {
            font-size: 0.5rem;
            text-transform: uppercase;
            letter-spacing: var(--letter-spacing-wider);
            color: var(--text-muted);
        }
        .donut-legend {
            display: flex;
            flex-direction: column;
            gap: 8px;
            align-items: center;
        }
        .donut-legend .legend-item {
            justify-content: center;
        }

        .chart-container {
            position: relative;
            width: 100%;
            background: var(--surface-beige-light);
            border-radius: var(--radius-sm);
            padding: 8px;
        }
        .chart-svg {
            display: block;
            width: 100%;
            height: auto;
            background: transparent;
        }
        .chart-tooltip {
            position: absolute;
            background: white;
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-sm);
            box-shadow: var(--shadow-md);
            padding: 8px 10px;
            pointer-events: none;
            display: none;
            z-index: 10;
            font-size: 0.75rem;
            color: var(--text-primary);
            white-space: nowrap;
        }
        .chart-tooltip::after {
            content: '';
            position: absolute;
            top: 100%;
            left: 50%;
            transform: translateX(-50%);
            border: 5px solid transparent;
            border-top-color: white;
        }
        .chart-legend {
            display: flex;
            justify-content: center;
            gap: 24px;
            margin-top: 10px;
            flex-wrap: wrap;
        }
        .legend-dot {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            display: inline-block;
            margin-right: 4px;
        }
        .legend-dot.gold { background: var(--accent-gold); }
        .legend-dot.red { background: var(--accent-red); }

        .log-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(90px, 1fr));
            gap: 8px;
        }
        .log-day {
            background: var(--surface-beige-light);
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-sm);
            padding: 8px 6px;
            text-align: center;
            cursor: pointer;
            transition: var(--transition);
            font-size: 0.7rem;
        }
        .log-day:hover { border-color: var(--accent-gold); box-shadow: var(--shadow-sm); }
        .log-day.locked { background: var(--accent-gold); color: var(--text-on-dark); border-color: var(--accent-gold-dark); }
        .log-day.unlocked { background: var(--blue); color: white; border-color: var(--blue-dark); }
        .log-day.partial {
            background: linear-gradient(135deg, var(--accent-gold) 50%, var(--surface-beige) 50%);
            color: var(--text-on-dark);
            border-color: var(--accent-gold-dark);
        }
        .log-day.orgasm { border: 2px solid var(--accent-red); }
        .log-day .log-day-date { font-weight: 600; font-size: 0.75rem; }
        .log-day .log-day-status {
            font-size: 0.55rem;
            text-transform: uppercase;
            letter-spacing: 0.04em;
        }
        .log-day .log-day-orgasm-info {
            font-size: 0.5rem;
            color: inherit;
            opacity: 0.9;
            margin-top: 2px;
            word-break: break-word;
        }

        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.4);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 100;
            animation: fadeIn 0.2s ease-out;
        }
        .modal-overlay.hidden { display: none; }
        .modal {
            background: var(--surface);
            border-radius: var(--radius-lg);
            border: 1px solid var(--border-subtle);
            box-shadow: var(--shadow-lg);
            padding: 28px;
            width: 90%;
            max-width: 480px;
        }
        .modal-title {
            font-family: var(--font-display);
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 16px;
        }
        .modal-label {
            font-family: var(--font-display);
            font-size: 0.6rem;
            text-transform: uppercase;
            letter-spacing: var(--letter-spacing-wider);
            color: var(--text-muted);
            margin-bottom: 4px;
        }
        .modal-input {
            width: 100%;
            padding: 8px 12px;
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-sm);
            font-family: var(--font-body);
            font-size: 0.9rem;
            margin-bottom: 12px;
            background: var(--surface);
            color: var(--text-primary);
        }
        .modal-input:focus { outline: none; border-color: var(--accent-gold); }
        .modal-buttons {
            display: flex;
            gap: 8px;
            justify-content: flex-end;
            margin-top: 16px;
        }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        .hidden { display: none; }

        .orgasm-type-row {
            display: flex;
            align-items: center;
            gap: 8px;
            margin-bottom: 8px;
        }
        .orgasm-type-row label {
            font-size: 0.75rem;
            color: var(--text-secondary);
            min-width: 30px;
        }
        .orgasm-type-row select {
            flex: 1;
        }

        .pinned-list { display: flex; flex-direction: column; gap: 8px; }
        .pinned-item {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 12px 16px;
            background: var(--surface-beige-light);
            border-radius: var(--radius-sm);
            border: 1px solid var(--border-subtle);
        }
        .pinned-item-info { display: flex; flex-direction: column; }
        .pinned-item-label {
            font-size: 0.65rem;
            text-transform: uppercase;
            letter-spacing: var(--letter-spacing-wider);
            color: var(--text-muted);
        }
        .pinned-item-value {
            font-family: var(--font-display);
            font-size: 1.3rem;
            font-weight: 600;
        }
        .pinned-item-sub { font-size: 0.8rem; color: var(--text-secondary); }
        .pinned-item-actions { display: flex; gap: 8px; align-items: center; }
        .pinned-item-delete,
        .pinned-item-edit,
        .pinned-item-fav {
            background: none;
            border: none;
            color: var(--text-muted);
            cursor: pointer;
            font-size: 1.1rem;
            padding: 4px;
            border-radius: 4px;
            transition: var(--transition);
        }
        .pinned-item-delete:hover { color: var(--accent-red); }
        .pinned-item-edit:hover { color: var(--accent-gold); }
        .pinned-item-fav { color: #D4AF37; }
        .pinned-item-fav.active { color: #FFD700; text-shadow: 0 0 4px rgba(255,215,0,0.6); }
        .pinned-item-fav:not(.active) { opacity: 0.4; }

        .pinned-add-form {
            display: flex;
            flex-direction: column;
            gap: 8px;
            margin-top: 12px;
        }
        .pinned-add-form input,
        .pinned-add-form select {
            width: 100%;
            padding: 8px 12px;
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-sm);
            font-family: var(--font-body);
            font-size: 0.85rem;
            background: var(--surface);
            color: var(--text-primary);
        }
        .pinned-add-form input:focus,
        .pinned-add-form select:focus { outline: none; border-color: var(--accent-gold); }
        .pinned-add-form .radio-group {
            display: flex;
            gap: 12px;
            align-items: center;
            flex-wrap: wrap;
            margin: 4px 0;
        }
        .pinned-add-form .radio-group label {
            display: flex;
            align-items: center;
            gap: 4px;
            font-size: 0.85rem;
            color: var(--text-secondary);
        }

        .warden-list { display: flex; flex-direction: column; gap: 8px; }
        .warden-item {
            padding: 12px 16px;
            background: var(--surface-beige-light);
            border-radius: var(--radius-sm);
            border: 1px solid var(--border-subtle);
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 12px;
        }
        .warden-item-quote {
            font-family: var(--font-display);
            font-style: italic;
            font-size: 0.95rem;
            flex: 1;
        }
        .warden-item-delete {
            background: none;
            border: none;
            color: var(--text-muted);
            cursor: pointer;
            font-size: 1.2rem;
            padding: 4px 8px;
            border-radius: 4px;
            transition: var(--transition);
            flex-shrink: 0;
        }
        .warden-item-delete:hover { color: var(--accent-red); }
        .warden-add-form { display: flex; gap: 8px; margin-top: 12px; flex-wrap: wrap; }
        .warden-add-form input {
            flex: 1;
            min-width: 180px;
            padding: 8px 12px;
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-sm);
            font-family: var(--font-body);
            font-size: 0.9rem;
            background: var(--surface);
            color: var(--text-primary);
        }
        .warden-add-form input:focus { outline: none; border-color: var(--accent-gold); }

        .settings-list { display: flex; flex-direction: column; gap: 16px; }
        .settings-item {
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 12px;
        }
        .settings-label { font-size: 0.9rem; color: var(--text-primary); }
        .toggle-switch {
            width: 44px;
            height: 24px;
            background: var(--surface-beige);
            border-radius: 12px;
            border: 1px solid var(--border-subtle);
            cursor: pointer;
            position: relative;
            transition: var(--transition);
            flex-shrink: 0;
        }
        .toggle-switch.active {
            background: var(--accent-gold);
            border-color: var(--accent-gold);
        }
        .toggle-switch::after {
            content: '';
            position: absolute;
            top: 2px;
            left: 2px;
            width: 18px;
            height: 18px;
            background: white;
            border-radius: 50%;
            transition: var(--transition);
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
        }
        .toggle-switch.active::after { left: 22px; }

        .orgasm-type-item {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 6px 10px;
            background: var(--surface-beige-light);
            border-radius: 4px;
            border: 1px solid var(--border-subtle);
            margin-bottom: 4px;
        }
        .orgasm-type-item span { font-size: 0.9rem; }
        .orgasm-type-delete {
            background: none;
            border: none;
            color: var(--text-muted);
            cursor: pointer;
            font-size: 1rem;
            padding: 2px 6px;
            border-radius: 3px;
        }
        .orgasm-type-delete:hover { color: var(--accent-red); }

        .footer {
            text-align: center;
            padding-top: 12px;
            font-family: var(--font-display);
            font-size: 0.55rem;
            letter-spacing: var(--letter-spacing-wider);
            text-transform: uppercase;
            color: var(--text-muted);
            opacity: 0.7;
            border-top: 1px solid var(--border-subtle);
            padding-top: 20px;
            margin-top: 8px;
        }

        [data-theme="dark"] {
            --bg: #1A1815;
            --surface: #242220;
            --surface-beige: #2E2A26;
            --surface-beige-light: #2A2623;
            --surface-pink: #3E2A2A;
            --accent-gold: #C49A2A;
            --accent-gold-dark: #D4AA3A;
            --accent-gold-light: #E0B84A;
            --text-primary: #E8E2D8;
            --text-secondary: #B0A89C;
            --text-muted: #7A7268;
            --border-subtle: #3A3630;
            --border-strong: #4A4438;
            --blue: #5B7E9E;
            --blue-dark: #4A6A88;
            --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.3);
            --shadow-md: 0 4px 12px rgba(0, 0, 0, 0.35);
            --shadow-lg: 0 8px 24px rgba(0, 0, 0, 0.4);
        }
    </style>
</head>
<body>
    <div class="container" id="appContainer">
        <header class="header">
            <span class="logo" id="logoBtn">Дисциплина</span>
            <div class="header-icons">
                <button class="header-icon-btn" id="themeToggle" aria-label="Переключить тему" title="Переключить тему">
                    <svg viewBox="0 0 24 24"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/></svg>
                </button>
                <button class="header-icon-btn" id="logoutBtn" aria-label="Выйти" title="Сбросить данные">
                    <svg viewBox="0 0 24 24"><path d="M9 21H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h4"/><polyline points="16 17 21 12 16 7"/><line x1="21" y1="12" x2="9" y2="12"/></svg>
                </button>
            </div>
        </header>

        <nav class="nav" id="mainNav">
            <button class="nav-item active" data-page="dashboard">
                <svg viewBox="0 0 24 24"><rect x="3" y="3" width="7" height="7" rx="1"/><rect x="14" y="3" width="7" height="7" rx="1"/><rect x="3" y="14" width="7" height="7" rx="1"/><rect x="14" y="14" width="7" height="7" rx="1"/></svg>
                Панель
            </button>
            <button class="nav-item" data-page="log">
                <svg viewBox="0 0 24 24"><rect x="3" y="4" width="18" height="18" rx="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
                Журнал
            </button>
            <button class="nav-item" data-page="pinned">
                <svg viewBox="0 0 24 24"><polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/></svg>
                Закреплено
            </button>
            <button class="nav-item" data-page="warden">
                <svg viewBox="0 0 24 24"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>
                Надзиратель
            </button>
            <button class="nav-item" data-page="settings">
                <svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 1 1-2.83 2.83l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 1 1-4 0v-.09a1.65 1.65 0 0 0-1-1.51 1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 1 1-2.83-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 1 1 0-4h.09a1.65 1.65 0 0 0 1.51-1 1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 1 1 2.83-2.83l.06.06a1.65 1.65 0 0 0 1.82.33h.01a1.65 1.65 0 0 0 1-1.51V3a2 2 0 1 1 4 0v.09a1.65 1.65 0 0 0 1 1.51h.01a1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 1 1 2.83 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82v.01a1.65 1.65 0 0 0 1.51 1H21a2 2 0 1 1 0 4h-.09a1.65 1.65 0 0 0-1.51 1z"/></svg>
                Настройки
            </button>
        </nav>

        <!-- Панель -->
        <div class="page active" id="page-dashboard">
            <section class="card today-card">
                <div class="today-left">
                    <span class="today-label">Сегодня</span>
                    <span class="today-date" id="dashDate"></span>
                </div>
                <div style="display:flex;align-items:center;gap:12px;flex-wrap:wrap;">
                    <span class="status-pill" id="dashStatusPill" title="Нажмите для переключения">
                        <span class="dot"></span>
                        <span id="dashStatusText">—</span>
                    </span>
                    <button class="btn" id="logTodayBtn">Записать сегодня</button>
                </div>
            </section>

            <section class="banner">
                <p class="banner-text" id="bannerText">Прошло <span class="banner-number" id="daysSinceOrgasm">0</span> дней с вашего последнего оргазма.</p>
            </section>

            <section class="warden-card">
                <p class="section-title">Надзиратель</p>
                <blockquote class="warden-quote" id="dashWardenQuote">Заблокирован и лишён на месяц одновременно. Вы либо глубоко преданы, либо глубоко сбиты с толку.</blockquote>
            </section>

            <section class="stats-grid">
                <div class="stat-card">
                    <span class="stat-label">Текущая серия</span>
                    <span class="stat-number" id="statCurrentStreak">0</span>
                    <span class="stat-sub">дней заблокирован</span>
                    <div class="progress-bar"><div class="progress-bar-fill" id="statStreakProgress" style="width:0%"></div></div>
                </div>
                <div class="stat-card">
                    <span class="stat-label">Рекордная серия</span>
                    <span class="stat-number" id="statRecordStreak">0</span>
                    <span class="stat-sub">дней заблокирован</span>
                </div>
                <div class="stat-card">
                    <span class="stat-label">До рекорда</span>
                    <span class="stat-number" id="statTowardRecord">0%</span>
                    <span class="stat-sub">процентов</span>
                </div>
                <div class="stat-card">
                    <span class="stat-label">За всю жизнь заблокирован</span>
                    <p class="stat-card-text" id="statLifetime">Нет данных</p>
                </div>
            </section>

            <section class="card">
                <p class="section-title">Закреплено</p>
                <div class="pinned-grid" id="dashPinnedGrid"></div>
            </section>

            <section class="card">
                <p class="section-title">Статистика блокировки</p>
                <div class="lock-stats-row">
                    <div class="lock-stat-card">
                        <span class="lock-stat-label">Этот год</span>
                        <div class="lock-stat-number gold" id="yearPercent">0%</div>
                        <span class="lock-stat-sub">% заблокирован</span>
                    </div>
                    <div class="lock-stat-card">
                        <span class="lock-stat-label">Этот месяц</span>
                        <div class="lock-stat-number gold" id="monthPercent">0%</div>
                        <span class="lock-stat-sub">% заблокирован</span>
                    </div>
                    <div class="lock-stat-card">
                        <span class="lock-stat-label">Оргазмы за месяц</span>
                        <div class="lock-stat-number" id="monthOrgasms">0</div>
                        <span class="lock-stat-sub">в этом месяце</span>
                    </div>
                </div>
            </section>

            <section class="card">
                <div class="heatmap-header">
                    <p class="section-title" style="margin-bottom:0;">Тепловая карта года</p>
                    <div class="heatmap-nav">
                        <button class="heatmap-btn" id="heatmapPrev" aria-label="Предыдущий год">
                            <svg viewBox="0 0 24 24"><polyline points="15 18 9 12 15 6"/></svg>
                        </button>
                        <span class="heatmap-year" id="heatmapYear">2026</span>
                        <button class="heatmap-btn" id="heatmapNext" aria-label="Следующий год">
                            <svg viewBox="0 0 24 24"><polyline points="9 18 15 12 9 6"/></svg>
                        </button>
                    </div>
                </div>
                <div class="heatmap-months" id="heatmapMonths"></div>
                <div class="heatmap-legend">
					<span class="legend-item"><span class="legend-square"></span> Заблокирован</span>
					<span class="legend-item"><span class="legend-square blue"></span> Разблокирован</span>
					<span class="legend-item"><span class="legend-square partial"></span> Частично</span>
					<span class="legend-item"><span class="legend-square gray"></span> Нет данных</span>
					<span class="legend-item"><span class="legend-circle"></span> Мой оргазм</span>
					<span class="legend-item"><span class="legend-circle" style="background:var(--green, #2E7D32);"></span> Её оргазм</span>
					<span class="legend-item"><span class="legend-circle" style="background:var(--blue);"></span> Оба</span>
				</div>
            </section>

            <section class="card">
                <p class="section-title">Соотношение за историю</p>
                <div class="donut-chart-container">
                    <div class="donut-chart" id="donutChart">
                        <div class="donut-hole">
                            <span id="donutPercent">0%</span>
                            <span class="donut-label">заблокировано</span>
                        </div>
                    </div>
                    <div class="donut-legend">
                        <div class="legend-item">
                            <span class="legend-square"></span> Заблокировано: <span id="donutLockedDays">0</span> дн.
                        </div>
                        <div class="legend-item">
                            <span class="legend-square blue"></span> Разблокировано: <span id="donutUnlockedDays">0</span> дн.
                        </div>
                    </div>
                </div>
            </section>

            <section class="card">
                <p class="section-title">Заблокирован % — последние 12 месяцев</p>
                <div class="chart-container">
                    <svg id="monthlyChart" class="chart-svg" viewBox="0 0 600 300" preserveAspectRatio="xMidYMid meet"></svg>
                    <div class="chart-tooltip" id="chartTooltip"></div>
                </div>
                <div class="chart-legend">
                    <div class="legend-item">
                        <span class="legend-dot gold"></span> % заблокирован
                    </div>
                    <div class="legend-item">
                        <span class="legend-dot red"></span> Количество оргазмов
                    </div>
                </div>
            </section>
        </div>

        <!-- Журнал -->
        <div class="page" id="page-log">
            <section class="card">
                <p class="section-title">Журнал записей</p>
                <p style="font-size:0.85rem;color:var(--text-secondary);margin-bottom:12px;">Нажмите на день, чтобы изменить статус. Shift+клик — добавить/убрать оргазм (до 5).</p>
                <div class="log-grid" id="logGrid"></div>
            </section>
            <section class="card">
                <p class="section-title">Добавить запись</p>
                <div style="display:flex;gap:8px;flex-wrap:wrap;">
                    <input type="date" id="logDateInput" class="modal-input" style="flex:1;min-width:150px;margin:0;">
                    <select id="logStatusSelect" class="modal-input" style="flex:1;min-width:120px;margin:0;">
                        <option value="locked">Заблокирован</option>
                        <option value="unlocked">Разблокирован</option>
                        <option value="partial">Частично</option>
                    </select>
                    <button class="btn" id="logAddBtn">Добавить</button>
                </div>
            </section>
        </div>

        <!-- Закреплено -->
        <div class="page" id="page-pinned">
            <section class="card">
                <p class="section-title">Закреплённые записи</p>
                <div class="pinned-list" id="pinnedList"></div>
                <div class="pinned-add-form">
                    <input type="text" id="pinnedLabelInput" placeholder="Название">
                    <div class="radio-group">
                        <label><input type="radio" name="pinnedType" value="date" checked> Дата</label>
                        <label><input type="radio" name="pinnedType" value="number"> Число</label>
                        <label><input type="radio" name="pinnedType" value="event"> Событие</label>
                        <label><input type="radio" name="pinnedType" value="her_event"> Её событие</label>
                    </div>
                    <input type="date" id="pinnedDateInput">
                    <input type="number" id="pinnedNumberInput" placeholder="Число" style="display:none;">
                    <select id="pinnedEventTypeSelect" style="display:none;"></select>
                    <select id="pinnedHerEventTypeSelect" style="display:none;"></select>
                    <select id="pinnedEventLogicSelect" style="display:none;">
                        <option value="date">Дата последнего события</option>
                        <option value="count">Количество событий</option>
                    </select>
                    <input type="text" id="pinnedSubInput" placeholder="Подпись (необязательно)">
                    <button class="btn" id="pinnedAddBtn">Добавить</button>
                </div>
            </section>
        </div>

        <!-- Надзиратель -->
        <div class="page" id="page-warden">
            <section class="card">
                <p class="section-title">Цитаты Надзирателя</p>
                <div class="warden-list" id="wardenList"></div>
                <div class="warden-add-form">
                    <input type="text" id="wardenQuoteInput" placeholder="Новая цитата..." style="flex:1;min-width:200px;">
                    <button class="btn" id="wardenAddBtn">Добавить</button>
                </div>
            </section>
        </div>

        <!-- Настройки -->
        <div class="page" id="page-settings">
            <section class="card">
                <p class="section-title">Настройки</p>
                <div class="settings-list">
                    <div class="settings-item">
                        <span class="settings-label">Тёмная тема</span>
                        <div class="toggle-switch" id="settingsThemeToggle"></div>
                    </div>
                    <div class="settings-item">
                        <span class="settings-label">Автосохранение (включено)</span>
                        <div class="toggle-switch active" id="settingsAutosave"></div>
                    </div>
                    <div class="settings-item">
                        <span class="settings-label">Виды моего оргазма</span>
                    </div>
                    <div id="orgasmTypeList"></div>
                    <div style="display:flex;gap:8px;margin-top:4px;">
                        <input type="text" id="newOrgasmTypeInput" placeholder="Новый вид..." class="modal-input" style="flex:1;margin:0;">
                        <button class="btn btn-outline" id="addOrgasmTypeBtn">Добавить</button>
                    </div>
                    <div class="settings-item">
                        <span class="settings-label">Виды её оргазма</span>
                    </div>
                    <div id="herOrgasmTypeList"></div>
                    <div style="display:flex;gap:8px;margin-top:4px;">
                        <input type="text" id="newHerOrgasmTypeInput" placeholder="Новый вид..." class="modal-input" style="flex:1;margin:0;">
                        <button class="btn btn-outline" id="addHerOrgasmTypeBtn">Добавить</button>
                    </div>
                    <div class="settings-item">
                        <span class="settings-label">Дата рождения</span>
                        <input type="date" id="birthdateInput" class="modal-input" style="max-width: 180px; margin:0;">
                    </div>
                    <div class="settings-item">
                        <span class="settings-label">Сбросить все данные</span>
                        <button class="btn btn-danger" id="settingsResetBtn">Сбросить</button>
                    </div>
                    <div class="settings-item" style="flex-direction:column;align-items:flex-start;gap:8px;">
                        <span class="settings-label">Экспорт данных</span>
                        <button class="btn btn-outline" id="settingsExportBtn">Экспорт JSON</button>
                    </div>
                    <div class="settings-item" style="flex-direction:column;align-items:flex-start;gap:8px;">
                        <span class="settings-label">Импорт данных</span>
                        <input type="file" id="settingsImportInput" accept=".json" style="font-family:var(--font-body);font-size:0.85rem;">
                    </div>
                </div>
            </section>
        </div>

        <footer class="footer">Дисциплина — записи и рефлексия</footer>
    </div>

    <!-- Модальное окно для записи дня -->
    <div class="modal-overlay hidden" id="modalOverlay">
        <div class="modal">
            <p class="modal-title" id="modalTitle">Запись</p>
            <p class="modal-label">Дата</p>
            <input type="date" id="modalDate" class="modal-input">
            <p class="modal-label">Статус</p>
            <select id="modalStatus" class="modal-input">
                <option value="locked">Заблокирован</option>
                <option value="unlocked">Разблокирован</option>
                <option value="partial">Частично</option>
            </select>
            <p class="modal-label">Мои оргазмы (0-5)</p>
            <select id="modalOrgasmCount" class="modal-input">
                <option value="0">0</option>
                <option value="1">1</option>
                <option value="2">2</option>
                <option value="3">3</option>
                <option value="4">4</option>
                <option value="5">5</option>
            </select>
            <div id="orgasmTypesContainer"></div>
            <p class="modal-label">Её оргазмы (без лимита)</p>
            <select id="modalHerOrgasmCount" class="modal-input">
                <option value="0">0</option>
                <option value="1">1</option>
                <option value="2">2</option>
                <option value="3">3</option>
                <option value="4">4</option>
                <option value="5">5</option>
                <option value="6">6</option>
                <option value="7">7</option>
                <option value="8">8</option>
                <option value="9">9</option>
                <option value="10">10</option>
                <option value="11">11</option>
                <option value="12">12</option>
                <option value="13">13</option>
                <option value="14">14</option>
                <option value="15">15</option>
                <option value="16">16</option>
                <option value="17">17</option>
                <option value="18">18</option>
                <option value="19">19</option>
                <option value="20">20</option>
            </select>
            <div id="herOrgasmTypesContainer"></div>
            <div class="modal-buttons">
                <button class="btn btn-outline" id="modalCancel">Отмена</button>
                <button class="btn" id="modalSave">Сохранить</button>
            </div>
        </div>
    </div>

    <!-- Модальное окно для редактирования закреплённой записи -->
    <div class="modal-overlay hidden" id="pinnedEditOverlay">
        <div class="modal">
            <p class="modal-title" id="pinnedEditTitle">Редактировать запись</p>
            <p class="modal-label">Название</p>
            <input type="text" id="pinnedEditLabel" class="modal-input">
            <p class="modal-label">Тип</p>
            <div class="radio-group" style="margin-bottom:12px;">
                <label><input type="radio" name="pinnedEditType" value="date" id="pinnedEditTypeDate"> Дата</label>
                <label><input type="radio" name="pinnedEditType" value="number" id="pinnedEditTypeNumber"> Число</label>
                <label><input type="radio" name="pinnedEditType" value="event" id="pinnedEditTypeEvent"> Событие</label>
                <label><input type="radio" name="pinnedEditType" value="her_event" id="pinnedEditTypeHerEvent"> Её событие</label>
            </div>
            <p class="modal-label" id="pinnedEditDateLabel">Дата</p>
            <input type="date" id="pinnedEditDate" class="modal-input">
            <p class="modal-label" id="pinnedEditNumberLabel" style="display:none;">Число</p>
            <input type="number" id="pinnedEditNumber" class="modal-input" style="display:none;">
            <p class="modal-label" id="pinnedEditEventLabel" style="display:none;">Тип события</p>
            <select id="pinnedEditEventType" class="modal-input" style="display:none;"></select>
            <p class="modal-label" id="pinnedEditHerEventLabel" style="display:none;">Тип её события</p>
            <select id="pinnedEditHerEventType" class="modal-input" style="display:none;"></select>
            <p class="modal-label" id="pinnedEditEventLogicLabel" style="display:none;">Логика</p>
            <select id="pinnedEditEventLogic" class="modal-input" style="display:none;">
                <option value="date">Дата последнего события</option>
                <option value="count">Количество событий</option>
            </select>
            <p class="modal-label">Подпись</p>
            <input type="text" id="pinnedEditSub" class="modal-input">
            <div class="modal-buttons">
                <button class="btn btn-outline" id="pinnedEditCancel">Отмена</button>
                <button class="btn" id="pinnedEditSave">Сохранить</button>
            </div>
        </div>
    </div>

    <script>
        (function() {
            const STORAGE_KEY = 'discipline_app_data';
            const DEFAULT_DATA = {
                entries: {},
                pinned: [],
                wardenQuotes: [
                    "Заблокирован и лишён на месяц одновременно. Вы либо глубоко преданы, либо глубоко сбиты с толку.",
                    "Дисциплина — это выбор между тем, что вы хотите сейчас, и тем, что вы хотите больше всего.",
                    "Каждый день без оргазма — это шаг к ясности ума."
                ],
                settings: {
                    theme: 'light',
                    autosave: true,
                    orgasmTypes: ['Вагинальный', 'Анальный', 'Оральный', 'Мастурбация', 'Другой'],
                    herOrgasmTypes: ['Вагинальный', 'Анальный', 'Оральный', 'Другой'],
                    birthdate: ''
                }
            };

            let data = loadData();

            function loadData() {
                const stored = localStorage.getItem(STORAGE_KEY);
                if (stored) {
                    try {
                        const parsed = JSON.parse(stored);
                        if (parsed.pinned) {
                            parsed.pinned = parsed.pinned.map(p => ({
                                ...p,
                                favorite: !!p.favorite,
                                type: p.type || (p.date ? 'date' : 'number'),
                                sub: p.sub || (p.type === 'date' ? 'дней назад' : ''),
                                eventType: p.eventType || null,
                                eventLogic: p.eventLogic || 'date'
                            }));
                        }
                        if (parsed.entries) {
                            Object.keys(parsed.entries).forEach(key => {
                                const entry = parsed.entries[key];
                                if (entry && typeof entry.orgasm !== 'undefined' && typeof entry.orgasmCount === 'undefined') {
                                    entry.orgasmCount = entry.orgasm ? 1 : 0;
                                    entry.orgasmTypes = entry.orgasm ? (entry.orgasmType ? [entry.orgasmType] : []) : [];
                                    delete entry.orgasm;
                                    delete entry.orgasmType;
                                } else if (entry && typeof entry.orgasmCount === 'undefined') {
                                    entry.orgasmCount = 0;
                                    entry.orgasmTypes = [];
                                }
                                if (!Array.isArray(entry.orgasmTypes)) entry.orgasmTypes = [];
                                if (entry.orgasmCount > 5) entry.orgasmCount = 5;
                                if (typeof entry.partial === 'undefined') entry.partial = false;
                                if (typeof entry.herOrgasmCount === 'undefined') entry.herOrgasmCount = 0;
                                if (!Array.isArray(entry.herOrgasmTypes)) entry.herOrgasmTypes = [];
                            });
                        }
                        if (!parsed.settings) parsed.settings = {};
                        if (!parsed.settings.orgasmTypes) parsed.settings.orgasmTypes = [...DEFAULT_DATA.settings.orgasmTypes];
                        if (!parsed.settings.herOrgasmTypes) parsed.settings.herOrgasmTypes = [...DEFAULT_DATA.settings.herOrgasmTypes];
                        if (!parsed.settings.birthdate) parsed.settings.birthdate = '';
                        return parsed;
                    } catch (e) {
                        console.error('Ошибка загрузки данных, создаём новые', e);
                    }
                }
                const d = JSON.parse(JSON.stringify(DEFAULT_DATA));
                const today = new Date();
                for (let i = 0; i < 70; i++) {
                    const d2 = new Date(today);
                    d2.setDate(d2.getDate() - i);
                    const key = formatDateKey(d2);
                    d.entries[key] = { locked: true, partial: false, orgasmCount: 0, orgasmTypes: [], herOrgasmCount: 0, herOrgasmTypes: [], note: '' };
                }
                d.entries[formatDateKey(new Date())] = { locked: true, partial: false, orgasmCount: 0, orgasmTypes: [], herOrgasmCount: 0, herOrgasmTypes: [], note: '' };
                localStorage.setItem(STORAGE_KEY, JSON.stringify(d));
                return d;
            }

            function saveData() {
                localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
                renderAll();
            }

            function formatDateKey(date) {
                const y = date.getFullYear();
                const m = String(date.getMonth() + 1).padStart(2, '0');
                const d = String(date.getDate()).padStart(2, '0');
                return `${y}-${m}-${d}`;
            }
            function parseDateKey(key) {
                const parts = key.split('-').map(Number);
                return new Date(parts[0], parts[1] - 1, parts[2]);
            }
            function todayKey() { return formatDateKey(new Date()); }
            function addDays(date, days) { const d = new Date(date); d.setDate(d.getDate() + days); return d; }
            function daysBetween(day1, day2) {
                const d1 = new Date(day1);
                const d2 = new Date(day2);
                return Math.round((d1 - d2) / (1000 * 60 * 60 * 24));
            }
            function getEntry(dateKey) { return data.entries[dateKey] || null; }
            function setEntry(dateKey, entry) { data.entries[dateKey] = entry; saveData(); }

            function getSortedEntries() {
                return Object.entries(data.entries)
                    .map(([key, val]) => ({ key, ...val }))
                    .sort((a, b) => a.key.localeCompare(b.key));
            }

            function calcCurrentStreak() {
                let streak = 0;
                const today = new Date();
                for (let i = 0; i < 10000; i++) {
                    const d = addDays(today, -i);
                    const key = formatDateKey(d);
                    const entry = getEntry(key);
                    if (entry && (entry.locked || entry.partial)) streak++;
                    else break;
                }
                return streak;
            }

            function calcRecordStreak() {
                const entries = getSortedEntries();
                let maxStreak = 0;
                let currentRun = 0;
                for (const e of entries) {
                    if (e.locked || e.partial) {
                        currentRun++;
                        maxStreak = Math.max(maxStreak, currentRun);
                    } else {
                        currentRun = 0;
                    }
                }
                return maxStreak;
            }

            function calcDaysSinceOrgasm() {
                const today = new Date();
                for (let i = 0; i < 10000; i++) {
                    const d = addDays(today, -i);
                    const key = formatDateKey(d);
                    const entry = getEntry(key);
                    if (entry && entry.orgasmCount > 0) return i;
                }
                return 0;
            }

            function calcYearPercent(year) {
                const startKey = `${year}-01-01`;
                const endKey = `${year}-12-31`;
                const entries = getSortedEntries();
                const yearEntries = entries.filter(e => e.key >= startKey && e.key <= endKey);
                const totalDaysInYear = (year % 4 === 0 && year % 100 !== 0) || year % 400 === 0 ? 366 : 365;
                let lockedDays = 0;
                yearEntries.forEach(e => {
                    if (e.partial) lockedDays += 0.5;
                    else if (e.locked) lockedDays += 1;
                });
                return (lockedDays / totalDaysInYear) * 100;
            }

            function calcMonthPercent(year, month) {
                const m = String(month + 1).padStart(2, '0');
                const startKey = `${year}-${m}-01`;
                const lastDay = new Date(year, month + 1, 0).getDate();
                const endKey = `${year}-${m}-${String(lastDay).padStart(2, '0')}`;
                const entries = getSortedEntries();
                const monthEntries = entries.filter(e => e.key >= startKey && e.key <= endKey);
                let lockedDays = 0;
                monthEntries.forEach(e => {
                    if (e.partial) lockedDays += 0.5;
                    else if (e.locked) lockedDays += 1;
                });
                return (lockedDays / lastDay) * 100;
            }

            function calcMonthOrgasms(year, month) {
                const m = String(month + 1).padStart(2, '0');
                const startKey = `${year}-${m}-01`;
                const lastDay = new Date(year, month + 1, 0).getDate();
                const endKey = `${year}-${m}-${String(lastDay).padStart(2, '0')}`;
                const entries = getSortedEntries();
                let totalOrgasms = 0;
                entries.forEach(e => {
                    if (e.key >= startKey && e.key <= endKey) {
                        totalOrgasms += (e.orgasmCount || 0);
                    }
                });
                return totalOrgasms;
            }

            function calcLifetimeLocked() {
                const entries = getSortedEntries();
                if (entries.length === 0) return { totalDays: 0, lockedDays: 0, percent: 0, hasBirthdate: false };
                let totalDays = 0;
                const hasBirthdate = !!(data.settings.birthdate && data.settings.birthdate !== '');
                if (hasBirthdate) {
                    const startDate = parseDateKey(data.settings.birthdate);
                    const today = new Date();
                    totalDays = daysBetween(today, startDate) + 1;
                } else {
                    const firstKey = entries[0].key;
                    const lastKey = entries[entries.length - 1].key;
                    const startDate = parseDateKey(firstKey);
                    const endDate = parseDateKey(lastKey);
                    totalDays = daysBetween(endDate, startDate) + 1;
                }
                let lockedDays = 0;
                entries.forEach(e => {
                    if (e.partial) lockedDays += 0.5;
                    else if (e.locked) lockedDays += 1;
                });
                const percent = totalDays > 0 ? (lockedDays / totalDays) * 100 : 0;
                return { totalDays, lockedDays: Math.round(lockedDays * 10) / 10, percent, hasBirthdate };
            }

            function calcHistoryRatio() {
                const entries = getSortedEntries();
                if (entries.length === 0) return { locked: 0, unlocked: 0, percent: 0 };
                const firstKey = entries[0].key;
                const lastKey = entries[entries.length - 1].key;
                const totalDays = daysBetween(parseDateKey(lastKey), parseDateKey(firstKey)) + 1;
                let lockedDays = 0;
                entries.forEach(e => {
                    if (e.partial) lockedDays += 0.5;
                    else if (e.locked) lockedDays += 1;
                });
                const unlockedDays = totalDays - lockedDays;
                const percent = totalDays > 0 ? (lockedDays / totalDays) * 100 : 0;
                return {
                    locked: Math.round(lockedDays * 10) / 10,
                    unlocked: Math.round(unlockedDays * 10) / 10,
                    percent: percent
                };
            }

            function getLastEventDateByType(eventType, isHer = false) {
                const entries = getSortedEntries().filter(e => {
                    if (isHer) {
                        return e.herOrgasmCount > 0 && e.herOrgasmTypes && e.herOrgasmTypes.includes(eventType);
                    } else {
                        return e.orgasmCount > 0 && e.orgasmTypes && e.orgasmTypes.includes(eventType);
                    }
                });
                if (entries.length === 0) return null;
                return entries[entries.length - 1].key;
            }

            function getEventCountByType(eventType, isHer = false) {
                let count = 0;
                const entries = getSortedEntries();
                entries.forEach(e => {
                    if (isHer) {
                        if (e.herOrgasmCount > 0 && e.herOrgasmTypes) {
                            count += e.herOrgasmTypes.filter(t => t === eventType).length;
                        }
                    } else {
                        if (e.orgasmCount > 0 && e.orgasmTypes) {
                            count += e.orgasmTypes.filter(t => t === eventType).length;
                        }
                    }
                });
                return count;
            }

            function getPinnedDisplayValue(p) {
                let value, sub;
                if (p.type === 'number') {
                    value = p.value;
                    sub = p.sub || '';
                } else if (p.type === 'event' || p.type === 'her_event') {
                    const isHer = p.type === 'her_event';
                    const eventType = p.eventType;
                    if (p.eventLogic === 'count') {
                        value = getEventCountByType(eventType, isHer);
                        sub = p.sub || 'событий всего';
                    } else {
                        const lastDateKey = getLastEventDateByType(eventType, isHer);
                        if (lastDateKey) {
                            const daysAgo = daysBetween(new Date(), parseDateKey(lastDateKey));
                            value = daysAgo > 0 ? daysAgo : 0;
                            sub = p.sub || 'дней с последнего события';
                        } else {
                            value = 0;
                            sub = p.sub || 'событий не было';
                        }
                    }
                } else {
                    const daysAgo = daysBetween(new Date(), parseDateKey(p.date));
                    value = daysAgo > 0 ? daysAgo : 0;
                    sub = p.sub || 'дней назад';
                }
                return { value, sub };
            }

            function getPinnedList() {
                return data.pinned.slice().sort((a, b) => {
                    if (a.type === 'date' && b.type === 'date') return a.date.localeCompare(b.date);
                    return 0;
                });
            }

            function renderAll() {
                renderDashboard();
                renderLog();
                renderPinnedPage();
                renderWardenPage();
                renderSettings();
            }

            function renderDashboard() {
                const today = new Date();
                document.getElementById('dashDate').textContent = new Intl.DateTimeFormat('ru-RU', {
                    day: 'numeric', month: 'long', year: 'numeric'
                }).format(today);

                const todayEntry = getEntry(todayKey());
                const statusText = document.getElementById('dashStatusText');
                const statusPill = document.getElementById('dashStatusPill');
                if (todayEntry) {
                    if (todayEntry.partial) {
                        statusText.textContent = 'Частично';
                        statusPill.classList.add('partial');
                        statusPill.classList.remove('locked');
                    } else if (todayEntry.locked) {
                        statusText.textContent = 'Заблокировано';
                        statusPill.classList.add('locked');
                        statusPill.classList.remove('partial');
                    } else {
                        statusText.textContent = 'Разблокировано';
                        statusPill.classList.remove('locked', 'partial');
                    }
                } else {
                    statusText.textContent = 'Нет записи';
                    statusPill.classList.remove('locked', 'partial');
                }

                const daysSinceOrg = calcDaysSinceOrgasm();
                const bannerElement = document.getElementById('bannerText');
                if (daysSinceOrg === 1) {
                    bannerElement.innerHTML = 'Последний оргазм был <span class="banner-inline-red">вчера</span>.';
                } else {
                    bannerElement.innerHTML = `Прошло <span class="banner-number">${daysSinceOrg}</span> дней с вашего последнего оргазма.`;
                }

                const currentStreak = calcCurrentStreak();
                const recordStreak = calcRecordStreak();
                document.getElementById('statCurrentStreak').textContent = currentStreak;
                document.getElementById('statRecordStreak').textContent = recordStreak;
                const towardRecord = recordStreak > 0 ? Math.round((currentStreak / recordStreak) * 100) : 0;
                document.getElementById('statTowardRecord').textContent = towardRecord + '%';
                document.getElementById('statStreakProgress').style.width = towardRecord + '%';

                const lifetime = calcLifetimeLocked();
                const lifetimeEl = document.getElementById('statLifetime');
                if (lifetime.totalDays > 0) {
                    const daysText = lifetime.hasBirthdate
                        ? `За всю жизнь вы провели заблокированным`
                        : `С момента начала записей вы провели`;
                    lifetimeEl.innerHTML = `${daysText} <span class="stat-text-highlight">${lifetime.lockedDays}</span> дней — или <span class="stat-text-highlight">${lifetime.percent.toFixed(1)}%</span> вашей жизни!`;
                } else {
                    lifetimeEl.textContent = 'Нет данных';
                }

                const pinnedGrid = document.getElementById('dashPinnedGrid');
                const pinned = getPinnedList();
                const favorites = pinned.filter(p => p.favorite);
                pinnedGrid.innerHTML = '';
                favorites.forEach(p => {
                    const { value, sub } = getPinnedDisplayValue(p);
                    const div = document.createElement('div');
                    div.className = 'pinned-subcard';
                    div.innerHTML = `<span class="pinned-label">${p.label}</span><div class="pinned-number">${value}</div>${sub ? `<span class="pinned-sub">${sub}</span>` : ''}`;
                    pinnedGrid.appendChild(div);
                });

                const todayDate = new Date();
                const year = todayDate.getFullYear();
                const month = todayDate.getMonth();
                document.getElementById('yearPercent').textContent = calcYearPercent(year).toFixed(1) + '%';
                document.getElementById('monthPercent').textContent = calcMonthPercent(year, month).toFixed(1) + '%';
                document.getElementById('monthOrgasms').textContent = calcMonthOrgasms(year, month);

                const quoteEl = document.getElementById('dashWardenQuote');
                const quotes = data.wardenQuotes;
                if (quotes.length > 0) {
                    const todayDay = new Date().getDate();
                    quoteEl.textContent = quotes[todayDay % quotes.length];
                } else {
                    quoteEl.textContent = 'Нет цитат. Добавьте в разделе «Надзиратель».';
                }

                renderHeatmap();
                renderDonutChart();
                renderMonthlyChart();
            }

            let heatmapYear = new Date().getFullYear();

            function renderHeatmap() {
				const monthsContainer = document.getElementById('heatmapMonths');
				const yearEl = document.getElementById('heatmapYear');
				yearEl.textContent = heatmapYear;
				monthsContainer.innerHTML = '';
				const monthNames = ['ЯНВ', 'ФЕВ', 'МАР', 'АПР', 'МАЙ', 'ИЮН', 'ИЮЛ', 'АВГ', 'СЕН', 'ОКТ', 'НОЯ', 'ДЕК'];
				const today = new Date();
				const isCurrentYear = heatmapYear === today.getFullYear();
				const currentMonth = today.getMonth();

				for (let m = 0; m < 12; m++) {
					const monthDiv = document.createElement('div');
					monthDiv.className = 'heatmap-month';
					const label = document.createElement('span');
					label.className = 'heatmap-month-label';
					label.textContent = monthNames[m];
					monthDiv.appendChild(label);

					const squaresDiv = document.createElement('div');
					squaresDiv.className = 'heatmap-squares';

					const daysInMonth = new Date(heatmapYear, m + 1, 0).getDate();

					for (let dayNum = 1; dayNum <= daysInMonth; dayNum++) {
						const sq = document.createElement('span');
						sq.className = 'heatmap-square';
						const dateObj = new Date(heatmapYear, m, dayNum);
						const key = formatDateKey(dateObj);
						const entry = getEntry(key);
						const isFuture = dateObj > today;

						if (isFuture || (isCurrentYear && m > currentMonth) || (isCurrentYear && m === currentMonth && dayNum > today.getDate())) {
							sq.classList.add('gray');
							sq.title = 'Нет данных';
						} else if (entry) {
							if (entry.partial) {
								sq.classList.add('partial');
								sq.title = `Частично: ${key}`;
							} else if (entry.locked) {
								sq.classList.add('gold');
								sq.title = `Заблокирован: ${key}`;
							} else {
								sq.classList.add('blue');
								sq.title = `Разблокирован: ${key}`;
							}

							const hasMy = entry.orgasmCount > 0;
							const hasHer = entry.herOrgasmCount > 0;

							if (hasMy && hasHer) {
								sq.style.borderColor = 'var(--blue)';
								sq.style.boxShadow = '0 0 0 2px var(--blue)';
								sq.title += ` (оба: ${entry.orgasmCount} моих, ${entry.herOrgasmCount} её)`;
							} else if (hasMy) {
								sq.style.borderColor = 'var(--accent-red)';
								sq.style.boxShadow = '0 0 0 2px var(--accent-red)';
								sq.title += ` (оргазмов: ${entry.orgasmCount})`;
							} else if (hasHer) {
								sq.style.borderColor = 'var(--green, #2E7D32)';
								sq.style.boxShadow = '0 0 0 2px var(--green, #2E7D32)';
								sq.title += ` (её оргазмов: ${entry.herOrgasmCount})`;
							}
						} else {
							sq.classList.add('gray');
							sq.title = 'Нет записи';
						}

						sq.addEventListener('click', () => {
							const dateObj2 = new Date(heatmapYear, m, dayNum);
							const key2 = formatDateKey(dateObj2);
							if (dateObj2 > today) return;
							openModalForKey(key2);
						});

						squaresDiv.appendChild(sq);
					}

					monthDiv.appendChild(squaresDiv);
					monthsContainer.appendChild(monthDiv);
				}
			}

            function renderDonutChart() {
                const ratio = calcHistoryRatio();
                const donutPercent = document.getElementById('donutPercent');
                const donutLocked = document.getElementById('donutLockedDays');
                const donutUnlocked = document.getElementById('donutUnlockedDays');
                const donutChart = document.getElementById('donutChart');

                donutPercent.textContent = ratio.percent.toFixed(1) + '%';
                donutLocked.textContent = ratio.locked;
                donutUnlocked.textContent = ratio.unlocked;
                const lockedAngle = ratio.percent;
                donutChart.style.background = `conic-gradient(var(--accent-gold) 0% ${lockedAngle}%, var(--blue) ${lockedAngle}% 100%)`;
            }

            function calcMonthlyStats() {
                const today = new Date();
                const months = [];
                const monthNames = ['янв', 'фев', 'мар', 'апр', 'мая', 'июн', 'июл', 'авг', 'сен', 'окт', 'ноя', 'дек'];
                for (let i = 11; i >= 0; i--) {
                    const d = new Date(today.getFullYear(), today.getMonth() - i, 1);
                    const year = d.getFullYear();
                    const month = d.getMonth();
                    const percent = calcMonthPercent(year, month);
                    const events = calcMonthOrgasms(year, month);
                    const label = monthNames[month] + ' ' + year;
                    months.push({ label, percent: Math.round(percent), events });
                }
                return months;
            }

            function renderMonthlyChart() {
                const svg = document.getElementById('monthlyChart');
                const tooltip = document.getElementById('chartTooltip');
                const data = calcMonthlyStats();

                const width = 600;
                const height = 300;
                const margin = { top: 20, right: 30, bottom: 60, left: 40 };
                const innerWidth = width - margin.left - margin.right;
                const innerHeight = height - margin.top - margin.bottom;

                svg.innerHTML = '';

                const yGridLines = [0, 25, 50, 75, 100];
                yGridLines.forEach(val => {
                    const y = margin.top + innerHeight - (val / 100) * innerHeight;
                    const line = document.createElementNS('http://www.w3.org/2000/svg', 'line');
                    line.setAttribute('x1', margin.left);
                    line.setAttribute('y1', y);
                    line.setAttribute('x2', width - margin.right);
                    line.setAttribute('y2', y);
                    line.setAttribute('stroke', 'var(--border-subtle)');
                    line.setAttribute('stroke-dasharray', '4 4');
                    svg.appendChild(line);
                });

                yGridLines.forEach(val => {
                    const y = margin.top + innerHeight - (val / 100) * innerHeight;
                    const text = document.createElementNS('http://www.w3.org/2000/svg', 'text');
                    text.setAttribute('x', margin.left - 10);
                    text.setAttribute('y', y + 4);
                    text.setAttribute('text-anchor', 'end');
                    text.setAttribute('font-size', '10');
                    text.setAttribute('fill', 'var(--text-muted)');
                    text.textContent = val + '%';
                    svg.appendChild(text);
                });

                const maxEvents = Math.max(...data.map(d => d.events), 5);
                const eventGridLines = [0, 1, 2, 3, 4, 5].filter(v => v <= maxEvents);
                eventGridLines.forEach(val => {
                    const y = margin.top + innerHeight - (val / maxEvents) * innerHeight;
                    const text = document.createElementNS('http://www.w3.org/2000/svg', 'text');
                    text.setAttribute('x', width - margin.right + 10);
                    text.setAttribute('y', y + 4);
                    text.setAttribute('text-anchor', 'start');
                    text.setAttribute('font-size', '10');
                    text.setAttribute('fill', 'var(--text-muted)');
                    text.textContent = val;
                    svg.appendChild(text);
                });

                const xStep = innerWidth / (data.length - 1);
                data.forEach((d, i) => {
                    const x = margin.left + i * xStep;
                    const text = document.createElementNS('http://www.w3.org/2000/svg', 'text');
                    text.setAttribute('x', x);
                    text.setAttribute('y', height - 25);
                    text.setAttribute('text-anchor', 'end');
                    text.setAttribute('transform', `rotate(-35 ${x} ${height - 25})`);
                    text.setAttribute('font-size', '10');
                    text.setAttribute('fill', 'var(--text-muted)');
                    text.textContent = d.label;
                    svg.appendChild(text);
                });

                const percentPoints = data.map((d, i) => ({
                    x: margin.left + i * xStep,
                    y: margin.top + innerHeight - (d.percent / 100) * innerHeight
                }));
                const percentPath = document.createElementNS('http://www.w3.org/2000/svg', 'path');
                const dPath = percentPoints.map((p, i) => (i === 0 ? 'M' : 'L') + p.x + ' ' + p.y).join(' ');
                percentPath.setAttribute('d', dPath);
                percentPath.setAttribute('fill', 'none');
                percentPath.setAttribute('stroke', 'var(--accent-gold)');
                percentPath.setAttribute('stroke-width', '2');
                svg.appendChild(percentPath);

                percentPoints.forEach((p, i) => {
                    const circle = document.createElementNS('http://www.w3.org/2000/svg', 'circle');
                    circle.setAttribute('cx', p.x);
                    circle.setAttribute('cy', p.y);
                    circle.setAttribute('r', '5');
                    circle.setAttribute('fill', 'var(--accent-gold)');
                    circle.setAttribute('stroke', 'white');
                    circle.setAttribute('stroke-width', '1');
                    circle.dataset.index = i;
                    circle.style.cursor = 'pointer';
                    circle.addEventListener('mouseenter', (e) => showTooltip(e, data[i]));
                    circle.addEventListener('mouseleave', hideTooltip);
                    svg.appendChild(circle);
                });

                const eventPoints = data.map((d, i) => ({
                    x: margin.left + i * xStep,
                    y: margin.top + innerHeight - (d.events / maxEvents) * innerHeight
                }));
                const eventPath = document.createElementNS('http://www.w3.org/2000/svg', 'path');
                const ePath = eventPoints.map((p, i) => (i === 0 ? 'M' : 'L') + p.x + ' ' + p.y).join(' ');
                eventPath.setAttribute('d', ePath);
                eventPath.setAttribute('fill', 'none');
                eventPath.setAttribute('stroke', 'var(--accent-red)');
                eventPath.setAttribute('stroke-width', '1.5');
                eventPath.setAttribute('stroke-dasharray', '6 4');
                svg.appendChild(eventPath);

                eventPoints.forEach((p, i) => {
                    const circle = document.createElementNS('http://www.w3.org/2000/svg', 'circle');
                    circle.setAttribute('cx', p.x);
                    circle.setAttribute('cy', p.y);
                    circle.setAttribute('r', '4');
                    circle.setAttribute('fill', 'var(--accent-red)');
                    circle.setAttribute('stroke', 'white');
                    circle.setAttribute('stroke-width', '1');
                    circle.dataset.index = i;
                    circle.style.cursor = 'pointer';
                    circle.addEventListener('mouseenter', (e) => showTooltip(e, data[i]));
                    circle.addEventListener('mouseleave', hideTooltip);
                    svg.appendChild(circle);
                });

                function showTooltip(e, d) {
                    const rect = svg.getBoundingClientRect();
                    const x = e.clientX - rect.left;
                    const y = e.clientY - rect.top;
                    tooltip.innerHTML = `<strong>${d.label}</strong><br>% заблокирован: ${d.percent}%<br>Оргазмы: ${d.events}`;
                    tooltip.style.display = 'block';
                    tooltip.style.left = (x + 10) + 'px';
                    tooltip.style.top = (y - 10) + 'px';
                }

                function hideTooltip() {
                    tooltip.style.display = 'none';
                }
            }

            function renderLog() {
                const grid = document.getElementById('logGrid');
                grid.innerHTML = '';
                const today = new Date();
                const startDate = addDays(today, -30);
                const monthAbbr = ['янв', 'фев', 'мар', 'апр', 'мая', 'июн', 'июл', 'авг', 'сен', 'окт', 'ноя', 'дек'];

                for (let i = 0; i < 35; i++) {
                    const d = addDays(startDate, i);
                    const key = formatDateKey(d);
                    const entry = getEntry(key);
                    const dayDiv = document.createElement('div');
                    dayDiv.className = 'log-day';
                    if (entry) {
                        if (entry.partial) {
                            dayDiv.classList.add('partial');
                        } else if (entry.locked) {
                            dayDiv.classList.add('locked');
                        } else {
                            dayDiv.classList.add('unlocked');
                        }
                        if (entry.orgasmCount > 0) dayDiv.classList.add('orgasm');
                    }
                    let statusText = entry ? (entry.partial ? 'ЧАСТ' : (entry.locked ? 'ЗБЛ' : 'РЗБ')) : '—';
                    let orgasmInfo = '';
                    if (entry && entry.orgasmCount > 0) {
                        orgasmInfo = `Орг: ${entry.orgasmCount}`;
                        if (entry.orgasmTypes && entry.orgasmTypes.length > 0) {
                            orgasmInfo += ` (${entry.orgasmTypes.join(', ')})`;
                        }
                    }
                    if (entry && entry.herOrgasmCount > 0) {
                        orgasmInfo += ` | Её: ${entry.herOrgasmCount}`;
                        if (entry.herOrgasmTypes && entry.herOrgasmTypes.length > 0) {
                            orgasmInfo += ` (${entry.herOrgasmTypes.join(', ')})`;
                        }
                    }
                    const dateDisplay = `${d.getDate()} ${monthAbbr[d.getMonth()]}`;
                    dayDiv.innerHTML = `<div class="log-day-date">${dateDisplay}</div><div class="log-day-status">${statusText}</div>${orgasmInfo ? `<div class="log-day-orgasm-info">${orgasmInfo}</div>` : ''}`;
                    dayDiv.addEventListener('click', (e) => {
                        e.stopPropagation();
                        if (e.shiftKey) {
                            const current = getEntry(key);
                            if (current) {
                                if (!current.orgasmCount) current.orgasmCount = 0;
                                current.orgasmCount = (current.orgasmCount + 1) % 6;
                                if (current.orgasmCount > 0) {
                                    if (!current.orgasmTypes) current.orgasmTypes = [];
                                    while (current.orgasmTypes.length < current.orgasmCount) {
                                        current.orgasmTypes.push(data.settings.orgasmTypes[0] || '');
                                    }
                                    if (current.orgasmTypes.length > current.orgasmCount) {
                                        current.orgasmTypes = current.orgasmTypes.slice(0, current.orgasmCount);
                                    }
                                } else {
                                    current.orgasmTypes = [];
                                }
                                setEntry(key, current);
                            } else {
                                setEntry(key, { locked: true, partial: false, orgasmCount: 1, orgasmTypes: [data.settings.orgasmTypes[0] || ''], herOrgasmCount: 0, herOrgasmTypes: [], note: '' });
                            }
                        } else {
                            openModalForKey(key);
                        }
                    });
                    grid.appendChild(dayDiv);
                }
            }

            let modalKey = null;

            function openModalForKey(key) {
                modalKey = key;
                const entry = getEntry(key);
                document.getElementById('modalDate').value = key;
                const statusSelect = document.getElementById('modalStatus');
                if (entry) {
                    if (entry.partial) {
                        statusSelect.value = 'partial';
                    } else if (entry.locked) {
                        statusSelect.value = 'locked';
                    } else {
                        statusSelect.value = 'unlocked';
                    }
                } else {
                    statusSelect.value = 'locked';
                }
                const count = entry ? (entry.orgasmCount || 0) : 0;
                document.getElementById('modalOrgasmCount').value = String(Math.min(count, 5));
                const herCount = entry ? (entry.herOrgasmCount || 0) : 0;
                document.getElementById('modalHerOrgasmCount').value = String(Math.min(herCount, 20));
                document.getElementById('modalOverlay').classList.remove('hidden');
                updateOrgasmTypeFields(count);
                updateHerOrgasmTypeFields(herCount);
            }

            function updateOrgasmTypeFields(count) {
                const container = document.getElementById('orgasmTypesContainer');
                container.innerHTML = '';
                const entry = modalKey ? getEntry(modalKey) : null;
                for (let i = 0; i < count; i++) {
                    const row = document.createElement('div');
                    row.className = 'orgasm-type-row';
                    const label = document.createElement('label');
                    label.textContent = `#${i+1}`;
                    const select = document.createElement('select');
                    select.className = 'modal-input';
                    select.style.marginBottom = '0';
                    data.settings.orgasmTypes.forEach(type => {
                        const option = document.createElement('option');
                        option.value = type;
                        option.textContent = type;
                        if (entry && entry.orgasmTypes && entry.orgasmTypes[i] === type) {
                            option.selected = true;
                        }
                        select.appendChild(option);
                    });
                    row.appendChild(label);
                    row.appendChild(select);
                    container.appendChild(row);
                }
            }

            function updateHerOrgasmTypeFields(count) {
                const container = document.getElementById('herOrgasmTypesContainer');
                container.innerHTML = '';
                const entry = modalKey ? getEntry(modalKey) : null;
                for (let i = 0; i < count; i++) {
                    const row = document.createElement('div');
                    row.className = 'orgasm-type-row';
                    const label = document.createElement('label');
                    label.textContent = `#${i+1}`;
                    const select = document.createElement('select');
                    select.className = 'modal-input';
                    select.style.marginBottom = '0';
                    data.settings.herOrgasmTypes.forEach(type => {
                        const option = document.createElement('option');
                        option.value = type;
                        option.textContent = type;
                        if (entry && entry.herOrgasmTypes && entry.herOrgasmTypes[i] === type) {
                            option.selected = true;
                        }
                        select.appendChild(option);
                    });
                    row.appendChild(label);
                    row.appendChild(select);
                    container.appendChild(row);
                }
            }

            document.getElementById('modalOrgasmCount').addEventListener('change', (e) => {
                const count = parseInt(e.target.value, 10) || 0;
                updateOrgasmTypeFields(count);
            });

            document.getElementById('modalHerOrgasmCount').addEventListener('change', (e) => {
                const count = parseInt(e.target.value, 10) || 0;
                updateHerOrgasmTypeFields(count);
            });

            function closeModal() {
                document.getElementById('modalOverlay').classList.add('hidden');
                modalKey = null;
            }

            document.getElementById('modalCancel').addEventListener('click', closeModal);
            document.getElementById('modalSave').addEventListener('click', () => {
                if (!modalKey) return;
                const status = document.getElementById('modalStatus').value;
                const locked = status === 'locked' || status === 'partial';
                const partial = status === 'partial';
                const count = parseInt(document.getElementById('modalOrgasmCount').value, 10) || 0;
                const typeSelects = document.querySelectorAll('#orgasmTypesContainer select');
                const types = Array.from(typeSelects).map(sel => sel.value);
                const herCount = parseInt(document.getElementById('modalHerOrgasmCount').value, 10) || 0;
                const herTypeSelects = document.querySelectorAll('#herOrgasmTypesContainer select');
                const herTypes = Array.from(herTypeSelects).map(sel => sel.value);
                setEntry(modalKey, {
                    locked: locked,
                    partial: partial,
                    orgasmCount: count,
                    orgasmTypes: types,
                    herOrgasmCount: herCount,
                    herOrgasmTypes: herTypes,
                    note: ''
                });
                closeModal();
            });
            document.getElementById('modalOverlay').addEventListener('click', (e) => {
                if (e.target === e.currentTarget) closeModal();
            });

            const navItems = document.querySelectorAll('.nav-item');
            const pages = {
                dashboard: document.getElementById('page-dashboard'),
                log: document.getElementById('page-log'),
                pinned: document.getElementById('page-pinned'),
                warden: document.getElementById('page-warden'),
                settings: document.getElementById('page-settings'),
            };

            function switchPage(pageName) {
                Object.keys(pages).forEach(k => pages[k].classList.toggle('active', k === pageName));
                navItems.forEach(nav => nav.classList.toggle('active', nav.dataset.page === pageName));
                if (pageName === 'dashboard') renderDashboard();
                if (pageName === 'log') renderLog();
                if (pageName === 'pinned') renderPinnedPage();
                if (pageName === 'warden') renderWardenPage();
                if (pageName === 'settings') renderSettings();
            }

            navItems.forEach(nav => nav.addEventListener('click', () => switchPage(nav.dataset.page)));
            document.getElementById('logoBtn').addEventListener('click', () => switchPage('dashboard'));

            document.getElementById('logTodayBtn').addEventListener('click', () => {
                const key = todayKey();
                const entry = getEntry(key);
                if (entry) {
                    if (entry.partial) {
                        entry.partial = false;
                        entry.locked = false;
                    } else if (entry.locked) {
                        entry.partial = true;
                        entry.locked = true;
                    } else {
                        entry.locked = true;
                        entry.partial = false;
                    }
                    setEntry(key, entry);
                } else {
                    setEntry(key, { locked: true, partial: false, orgasmCount: 0, orgasmTypes: [], herOrgasmCount: 0, herOrgasmTypes: [], note: '' });
                }
            });

            document.getElementById('dashStatusPill').addEventListener('click', () => {
                const key = todayKey();
                const entry = getEntry(key);
                if (entry) {
                    if (entry.partial) {
                        entry.partial = false;
                        entry.locked = false;
                    } else if (entry.locked) {
                        entry.partial = true;
                        entry.locked = true;
                    } else {
                        entry.locked = true;
                        entry.partial = false;
                    }
                    setEntry(key, entry);
                } else {
                    setEntry(key, { locked: true, partial: false, orgasmCount: 0, orgasmTypes: [], herOrgasmCount: 0, herOrgasmTypes: [], note: '' });
                }
            });

            document.getElementById('logAddBtn').addEventListener('click', () => {
                const date = document.getElementById('logDateInput').value;
                const status = document.getElementById('logStatusSelect').value;
                if (!date) return;
                const locked = status === 'locked' || status === 'partial';
                const partial = status === 'partial';
                setEntry(date, { locked, partial, orgasmCount: 0, orgasmTypes: [], herOrgasmCount: 0, herOrgasmTypes: [], note: '' });
                renderLog();
            });

            const pinnedTypeRadios = document.querySelectorAll('input[name="pinnedType"]');
            pinnedTypeRadios.forEach(radio => {
                radio.addEventListener('change', () => {
                    const dateInput = document.getElementById('pinnedDateInput');
                    const numberInput = document.getElementById('pinnedNumberInput');
                    const eventSelect = document.getElementById('pinnedEventTypeSelect');
                    const herEventSelect = document.getElementById('pinnedHerEventTypeSelect');
                    const eventLogicSelect = document.getElementById('pinnedEventLogicSelect');

                    if (radio.value === 'date') {
                        dateInput.style.display = 'block';
                        numberInput.style.display = 'none';
                        eventSelect.style.display = 'none';
                        herEventSelect.style.display = 'none';
                        eventLogicSelect.style.display = 'none';
                    } else if (radio.value === 'number') {
                        dateInput.style.display = 'none';
                        numberInput.style.display = 'block';
                        eventSelect.style.display = 'none';
                        herEventSelect.style.display = 'none';
                        eventLogicSelect.style.display = 'none';
                    } else if (radio.value === 'event') {
                        dateInput.style.display = 'none';
                        numberInput.style.display = 'none';
                        eventSelect.style.display = 'block';
                        herEventSelect.style.display = 'none';
                        eventLogicSelect.style.display = 'block';
                    } else if (radio.value === 'her_event') {
                        dateInput.style.display = 'none';
                        numberInput.style.display = 'none';
                        eventSelect.style.display = 'none';
                        herEventSelect.style.display = 'block';
                        eventLogicSelect.style.display = 'block';
                    }
                });
            });

            function populateEventSelect(selectElement, selectedValue, isHer = false) {
                selectElement.innerHTML = '';
                const types = isHer ? data.settings.herOrgasmTypes : data.settings.orgasmTypes;
                types.forEach(type => {
                    const option = document.createElement('option');
                    option.value = type;
                    option.textContent = type;
                    if (selectedValue === type) option.selected = true;
                    selectElement.appendChild(option);
                });
            }

            populateEventSelect(document.getElementById('pinnedEventTypeSelect'));
            populateEventSelect(document.getElementById('pinnedHerEventTypeSelect'), null, true);
            populateEventSelect(document.getElementById('pinnedEditEventType'));
            populateEventSelect(document.getElementById('pinnedEditHerEventType'), null, true);

            document.getElementById('pinnedAddBtn').addEventListener('click', () => {
                const label = document.getElementById('pinnedLabelInput').value.trim();
                if (!label) return;
                const type = document.querySelector('input[name="pinnedType"]:checked').value;
                const sub = document.getElementById('pinnedSubInput').value.trim();
                let newEntry = { id: Date.now(), label, type, sub, favorite: false, eventType: null, eventLogic: 'date' };
                if (type === 'date') {
                    const date = document.getElementById('pinnedDateInput').value;
                    if (!date) return;
                    newEntry.date = date;
                } else if (type === 'number') {
                    const value = parseFloat(document.getElementById('pinnedNumberInput').value);
                    if (isNaN(value)) return;
                    newEntry.value = value;
                } else if (type === 'event' || type === 'her_event') {
                    const select = type === 'event' ? document.getElementById('pinnedEventTypeSelect') : document.getElementById('pinnedHerEventTypeSelect');
                    const eventType = select.value;
                    if (!eventType) return;
                    newEntry.eventType = eventType;
                    newEntry.eventLogic = document.getElementById('pinnedEventLogicSelect').value;
                }
                data.pinned.push(newEntry);
                document.getElementById('pinnedLabelInput').value = '';
                document.getElementById('pinnedDateInput').value = '';
                document.getElementById('pinnedNumberInput').value = '';
                document.getElementById('pinnedSubInput').value = '';
                saveData();
                renderPinnedPage();
            });

            function renderPinnedPage() {
                const list = document.getElementById('pinnedList');
                const pinned = getPinnedList();
                list.innerHTML = '';
                pinned.forEach(p => {
                    const { value, sub } = getPinnedDisplayValue(p);
                    const div = document.createElement('div');
                    div.className = 'pinned-item';
                    div.innerHTML = `
                        <div class="pinned-item-info">
                            <span class="pinned-item-label">${p.label}</span>
                            <span class="pinned-item-value">${value}</span>
                            ${sub ? `<span class="pinned-item-sub">${sub}</span>` : ''}
                        </div>
                        <div class="pinned-item-actions">
                            <button class="pinned-item-fav ${p.favorite ? 'active' : ''}" data-id="${p.id}" title="Избранное">★</button>
                            <button class="pinned-item-edit" data-id="${p.id}" title="Редактировать">✎</button>
                            <button class="pinned-item-delete" data-id="${p.id}" title="Удалить">✕</button>
                        </div>
                    `;
                    div.querySelector('.pinned-item-fav').addEventListener('click', () => {
                        p.favorite = !p.favorite;
                        saveData();
                        renderPinnedPage();
                        renderDashboard();
                    });
                    div.querySelector('.pinned-item-edit').addEventListener('click', () => {
                        openPinnedEditModal(p);
                    });
                    div.querySelector('.pinned-item-delete').addEventListener('click', () => {
                        data.pinned = data.pinned.filter(x => x.id !== p.id);
                        saveData();
                        renderPinnedPage();
                    });
                    list.appendChild(div);
                });
            }

            let editingPinnedId = null;

            function openPinnedEditModal(p) {
                editingPinnedId = p.id;
                document.getElementById('pinnedEditLabel').value = p.label;
                document.getElementById('pinnedEditTypeDate').checked = p.type === 'date';
                document.getElementById('pinnedEditTypeNumber').checked = p.type === 'number';
                document.getElementById('pinnedEditTypeEvent').checked = p.type === 'event';
                document.getElementById('pinnedEditTypeHerEvent').checked = p.type === 'her_event';
                document.getElementById('pinnedEditDate').value = p.date || '';
                document.getElementById('pinnedEditNumber').value = p.value || '';
                document.getElementById('pinnedEditSub').value = p.sub || '';
                populateEventSelect(document.getElementById('pinnedEditEventType'), p.eventType);
                populateEventSelect(document.getElementById('pinnedEditHerEventType'), p.eventType, true);
                document.getElementById('pinnedEditEventLogic').value = p.eventLogic || 'date';
                updatePinnedEditType();
                document.getElementById('pinnedEditOverlay').classList.remove('hidden');
            }

            function updatePinnedEditType() {
                const isDate = document.getElementById('pinnedEditTypeDate').checked;
                const isNumber = document.getElementById('pinnedEditTypeNumber').checked;
                const isEvent = document.getElementById('pinnedEditTypeEvent').checked;
                const isHerEvent = document.getElementById('pinnedEditTypeHerEvent').checked;

                document.getElementById('pinnedEditDateLabel').style.display = isDate ? 'block' : 'none';
                document.getElementById('pinnedEditDate').style.display = isDate ? 'block' : 'none';
                document.getElementById('pinnedEditNumberLabel').style.display = isNumber ? 'block' : 'none';
                document.getElementById('pinnedEditNumber').style.display = isNumber ? 'block' : 'none';
                document.getElementById('pinnedEditEventLabel').style.display = isEvent ? 'block' : 'none';
                document.getElementById('pinnedEditEventType').style.display = isEvent ? 'block' : 'none';
                document.getElementById('pinnedEditHerEventLabel').style.display = isHerEvent ? 'block' : 'none';
                document.getElementById('pinnedEditHerEventType').style.display = isHerEvent ? 'block' : 'none';
                const showLogic = isEvent || isHerEvent;
                document.getElementById('pinnedEditEventLogicLabel').style.display = showLogic ? 'block' : 'none';
                document.getElementById('pinnedEditEventLogic').style.display = showLogic ? 'block' : 'none';
            }

            document.querySelectorAll('input[name="pinnedEditType"]').forEach(radio => {
                radio.addEventListener('change', updatePinnedEditType);
            });

            document.getElementById('pinnedEditCancel').addEventListener('click', () => {
                document.getElementById('pinnedEditOverlay').classList.add('hidden');
                editingPinnedId = null;
            });

            document.getElementById('pinnedEditSave').addEventListener('click', () => {
                if (!editingPinnedId) return;
                const item = data.pinned.find(p => p.id === editingPinnedId);
                if (!item) return;
                item.label = document.getElementById('pinnedEditLabel').value.trim();
                item.sub = document.getElementById('pinnedEditSub').value.trim();
                if (document.getElementById('pinnedEditTypeDate').checked) {
                    item.type = 'date';
                    item.date = document.getElementById('pinnedEditDate').value;
                    delete item.value;
                    delete item.eventType;
                    delete item.eventLogic;
                } else if (document.getElementById('pinnedEditTypeNumber').checked) {
                    item.type = 'number';
                    item.value = parseFloat(document.getElementById('pinnedEditNumber').value);
                    delete item.date;
                    delete item.eventType;
                    delete item.eventLogic;
                } else if (document.getElementById('pinnedEditTypeEvent').checked) {
                    item.type = 'event';
                    item.eventType = document.getElementById('pinnedEditEventType').value;
                    item.eventLogic = document.getElementById('pinnedEditEventLogic').value;
                    delete item.date;
                    delete item.value;
                } else if (document.getElementById('pinnedEditTypeHerEvent').checked) {
                    item.type = 'her_event';
                    item.eventType = document.getElementById('pinnedEditHerEventType').value;
                    item.eventLogic = document.getElementById('pinnedEditEventLogic').value;
                    delete item.date;
                    delete item.value;
                }
                saveData();
                renderPinnedPage();
                document.getElementById('pinnedEditOverlay').classList.add('hidden');
                editingPinnedId = null;
            });

            function renderWardenPage() {
                const list = document.getElementById('wardenList');
                list.innerHTML = '';
                data.wardenQuotes.forEach((q, idx) => {
                    const div = document.createElement('div');
                    div.className = 'warden-item';
                    div.innerHTML = `<span class="warden-item-quote">${q}</span><button class="warden-item-delete" data-index="${idx}">✕</button>`;
                    div.querySelector('.warden-item-delete').addEventListener('click', () => {
                        data.wardenQuotes.splice(idx, 1);
                        saveData();
                        renderWardenPage();
                    });
                    list.appendChild(div);
                });
            }

            document.getElementById('wardenAddBtn').addEventListener('click', () => {
                const quote = document.getElementById('wardenQuoteInput').value.trim();
                if (!quote) return;
                data.wardenQuotes.push(quote);
                document.getElementById('wardenQuoteInput').value = '';
                saveData();
                renderWardenPage();
            });

            function renderSettings() {
                const themeToggle = document.getElementById('settingsThemeToggle');
                const isDark = data.settings.theme === 'dark';
                themeToggle.classList.toggle('active', isDark);
                document.documentElement.setAttribute('data-theme', isDark ? 'dark' : 'light');
                document.getElementById('settingsAutosave').classList.toggle('active', data.settings.autosave);

                document.getElementById('birthdateInput').value = data.settings.birthdate || '';

                const orgasmListContainer = document.getElementById('orgasmTypeList');
                orgasmListContainer.innerHTML = '';
                data.settings.orgasmTypes.forEach((type, idx) => {
                    const item = document.createElement('div');
                    item.className = 'orgasm-type-item';
                    item.innerHTML = `<span>${type}</span><button class="orgasm-type-delete" data-index="${idx}">✕</button>`;
                    item.querySelector('.orgasm-type-delete').addEventListener('click', () => {
                        data.settings.orgasmTypes.splice(idx, 1);
                        saveData();
                        renderSettings();
                    });
                    orgasmListContainer.appendChild(item);
                });

                const herOrgasmListContainer = document.getElementById('herOrgasmTypeList');
                herOrgasmListContainer.innerHTML = '';
                data.settings.herOrgasmTypes.forEach((type, idx) => {
                    const item = document.createElement('div');
                    item.className = 'orgasm-type-item';
                    item.innerHTML = `<span>${type}</span><button class="orgasm-type-delete" data-index="${idx}">✕</button>`;
                    item.querySelector('.orgasm-type-delete').addEventListener('click', () => {
                        data.settings.herOrgasmTypes.splice(idx, 1);
                        saveData();
                        renderSettings();
                    });
                    herOrgasmListContainer.appendChild(item);
                });
            }

            document.getElementById('settingsThemeToggle').addEventListener('click', () => {
                data.settings.theme = data.settings.theme === 'dark' ? 'light' : 'dark';
                saveData();
                renderSettings();
            });

            document.getElementById('settingsAutosave').addEventListener('click', () => {
                data.settings.autosave = !data.settings.autosave;
                saveData();
                renderSettings();
            });

            document.getElementById('addOrgasmTypeBtn').addEventListener('click', () => {
                const input = document.getElementById('newOrgasmTypeInput');
                const newType = input.value.trim();
                if (!newType) return;
                if (!data.settings.orgasmTypes.includes(newType)) {
                    data.settings.orgasmTypes.push(newType);
                    input.value = '';
                    saveData();
                    renderSettings();
                }
            });

            document.getElementById('newOrgasmTypeInput').addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    e.preventDefault();
                    document.getElementById('addOrgasmTypeBtn').click();
                }
            });

            document.getElementById('addHerOrgasmTypeBtn').addEventListener('click', () => {
                const input = document.getElementById('newHerOrgasmTypeInput');
                const newType = input.value.trim();
                if (!newType) return;
                if (!data.settings.herOrgasmTypes.includes(newType)) {
                    data.settings.herOrgasmTypes.push(newType);
                    input.value = '';
                    saveData();
                    renderSettings();
                }
            });

            document.getElementById('newHerOrgasmTypeInput').addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    e.preventDefault();
                    document.getElementById('addHerOrgasmTypeBtn').click();
                }
            });

            document.getElementById('birthdateInput').addEventListener('change', (e) => {
                data.settings.birthdate = e.target.value;
                saveData();
            });

            document.getElementById('settingsResetBtn').addEventListener('click', () => {
                if (confirm('Вы уверены? Все данные будут удалены.')) {
                    data = JSON.parse(JSON.stringify(DEFAULT_DATA));
                    saveData();
                    switchPage('dashboard');
                }
            });

            document.getElementById('settingsExportBtn').addEventListener('click', () => {
                const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' });
                const url = URL.createObjectURL(blob);
                const a = document.createElement('a');
                a.href = url;
                a.download = 'discipline_data.json';
                a.click();
                URL.revokeObjectURL(url);
            });

            document.getElementById('settingsImportInput').addEventListener('change', (e) => {
                const file = e.target.files[0];
                if (!file) return;
                const reader = new FileReader();
                reader.onload = (ev) => {
                    try {
                        const imported = JSON.parse(ev.target.result);
                        if (imported.entries && imported.pinned && imported.wardenQuotes && imported.settings) {
                            data = imported;
                            data.pinned = data.pinned.map(p => ({
                                ...p,
                                favorite: !!p.favorite,
                                type: p.type || (p.date ? 'date' : 'number'),
                                sub: p.sub || (p.type === 'date' ? 'дней назад' : ''),
                                eventType: p.eventType || null,
                                eventLogic: p.eventLogic || 'date'
                            }));
                            Object.keys(data.entries).forEach(key => {
                                const entry = data.entries[key];
                                if (entry && typeof entry.orgasm !== 'undefined' && typeof entry.orgasmCount === 'undefined') {
                                    entry.orgasmCount = entry.orgasm ? 1 : 0;
                                    entry.orgasmTypes = entry.orgasm ? (entry.orgasmType ? [entry.orgasmType] : []) : [];
                                    delete entry.orgasm;
                                    delete entry.orgasmType;
                                }
                                if (!entry.orgasmCount) entry.orgasmCount = 0;
                                if (!entry.orgasmTypes) entry.orgasmTypes = [];
                                if (typeof entry.partial === 'undefined') entry.partial = false;
                                if (typeof entry.herOrgasmCount === 'undefined') entry.herOrgasmCount = 0;
                                if (!Array.isArray(entry.herOrgasmTypes)) entry.herOrgasmTypes = [];
                            });
                            if (!data.settings.orgasmTypes) data.settings.orgasmTypes = [...DEFAULT_DATA.settings.orgasmTypes];
                            if (!data.settings.herOrgasmTypes) data.settings.herOrgasmTypes = [...DEFAULT_DATA.settings.herOrgasmTypes];
                            if (!data.settings.birthdate) data.settings.birthdate = '';
                            saveData();
                            switchPage('dashboard');
                        } else {
                            alert('Неверный формат файла');
                        }
                    } catch (err) {
                        alert('Ошибка чтения файла');
                    }
                };
                reader.readAsText(file);
            });

            document.getElementById('heatmapPrev').addEventListener('click', () => {
                heatmapYear--;
                renderHeatmap();
            });
            document.getElementById('heatmapNext').addEventListener('click', () => {
                heatmapYear++;
                renderHeatmap();
            });

            document.getElementById('themeToggle').addEventListener('click', () => {
                data.settings.theme = data.settings.theme === 'dark' ? 'light' : 'dark';
                saveData();
            });

            document.getElementById('logoutBtn').addEventListener('click', () => {
                if (confirm('Сбросить все данные?')) {
                    data = JSON.parse(JSON.stringify(DEFAULT_DATA));
                    saveData();
                    switchPage('dashboard');
                }
            });

            window.addEventListener('beforeunload', () => {
                localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
            });

            renderAll();
            switchPage('dashboard');
        })();
    </script>
</body>
</html>
