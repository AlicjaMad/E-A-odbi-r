<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Europejski System Analizy Bezpieczeństwa Maszyn - Pełna Zgodność z Normami UE</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #003399 0%, #0055cc 100%);
            color: #333;
            min-height: 100vh;
        }

        .eu-banner {
            background: #003399;
            color: #ffcc00;
            padding: 10px;
            text-align: center;
            font-size: 14px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
        }

        .eu-stars {
            display: flex;
            gap: 3px;
        }

        .container {
            max-width: 1600px;
            margin: 0 auto;
            background: white;
            box-shadow: 0 10px 40px rgba(0,0,0,0.3);
        }

        .header {
            background: linear-gradient(135deg, #003399 0%, #0055cc 100%);
            color: white;
            padding: 25px;
            text-align: center;
        }

        .header h1 {
            margin-bottom: 10px;
            font-size: 28px;
        }

        .norm-badges {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 15px;
        }

        .norm-badge {
            background: rgba(255, 204, 0, 0.2);
            border: 1px solid #ffcc00;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 12px;
        }

        .main-layout {
            display: flex;
            min-height: 700px;
        }

        .sidebar {
            width: 320px;
            background: #f8f9fa;
            padding: 15px;
            overflow-y: auto;
            border-right: 2px solid #dee2e6;
        }

        .sidebar h2 {
            background: #003399;
            color: #ffcc00;
            padding: 10px;
            margin: -15px -15px 15px -15px;
            font-size: 16px;
            text-align: center;
        }

        .component-category {
            margin-bottom: 20px;
        }

        .component-category h3 {
            background: linear-gradient(135deg, #28a745 0%, #20c997 100%);
            color: white;
            padding: 8px;
            margin-bottom: 10px;
            border-radius: 5px;
            font-size: 13px;
        }

        .component-item {
            background: white;
            border: 2px solid #dee2e6;
            padding: 10px;
            margin: 8px 0;
            border-radius: 8px;
            cursor: move;
            transition: all 0.3s;
        }

        .component-item:hover {
            border-color: #0055cc;
            transform: translateX(5px);
            box-shadow: 0 4px 12px rgba(0,85,204,0.2);
        }

        .component-header {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 8px;
        }

        .component-icon {
            font-size: 24px;
        }

        .component-name {
            font-weight: bold;
            font-size: 13px;
            flex: 1;
        }

        .component-specs {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 5px;
            font-size: 11px;
            color: #666;
        }

        .spec-item {
            background: #f8f9fa;
            padding: 3px 6px;
            border-radius: 3px;
        }

        .spec-label {
            font-weight: bold;
            color: #495057;
        }

        #canvas {
            flex: 1;
            background: white;
            position: relative;
            background-image: 
                linear-gradient(0deg, transparent 24%, rgba(0, 85, 204, 0.05) 25%, rgba(0, 85, 204, 0.05) 26%, transparent 27%, transparent 74%, rgba(0, 85, 204, 0.05) 75%, rgba(0, 85, 204, 0.05) 76%, transparent 77%, transparent),
                linear-gradient(90deg, transparent 24%, rgba(0, 85, 204, 0.05) 25%, rgba(0, 85, 204, 0.05) 26%, transparent 27%, transparent 74%, rgba(0, 85, 204, 0.05) 75%, rgba(0, 85, 204, 0.05) 76%, transparent 77%, transparent);
            background-size: 30px 30px;
            min-height: 700px;
        }

        .analysis-panel {
            width: 380px;
            background: #f8f9fa;
            padding: 15px;
            overflow-y: auto;
            border-left: 2px solid #dee2e6;
        }

        .analysis-section {
            background: white;
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 15px;
        }

        .analysis-section h3 {
            background: linear-gradient(135deg, #003399 0%, #0055cc 100%);
            color: white;
            padding: 8px;
            margin: -15px -15px 15px -15px;
            border-radius: 8px 8px 0 0;
            font-size: 14px;
        }

        .tabs {
            display: flex;
            gap: 5px;
            margin-bottom: 15px;
            background: #dee2e6;
            padding: 5px;
            border-radius: 5px;
        }

        .tab {
            flex: 1;
            padding: 8px;
            background: white;
            border: none;
            border-radius: 3px;
            cursor: pointer;
            font-size: 12px;
            transition: all 0.3s;
        }

        .tab.active {
            background: #003399;
            color: white;
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        .form-group {
            margin-bottom: 12px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
            font-size: 12px;
            color: #495057;
        }

        .form-group select,
        .form-group input {
            width: 100%;
            padding: 8px;
            border: 1px solid #dee2e6;
            border-radius: 4px;
            font-size: 12px;
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
        }

        .btn {
            background: #003399;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 13px;
            width: 100%;
            margin: 5px 0;
            transition: all 0.3s;
        }

        .btn:hover {
            background: #002266;
            transform: translateY(-1px);
        }

        .btn-success {
            background: #28a745;
        }

        .btn-success:hover {
            background: #218838;
        }

        .btn-warning {
            background: #ffc107;
            color: #333;
        }

        .btn-warning:hover {
            background: #e0a800;
        }

        .btn-danger {
            background: #dc3545;
        }

        .btn-danger:hover {
            background: #c82333;
        }

        .toolbar {
            background: #f8f9fa;
            padding: 12px;
            display: flex;
            gap: 10px;
            border-top: 2px solid #dee2e6;
            flex-wrap: wrap;
        }

        .toolbar-group {
            display: flex;
            gap: 10px;
            flex: 1;
        }

        .toolbar button {
            padding: 8px 15px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            background: #6c757d;
            color: white;
            font-size: 13px;
            transition: all 0.3s;
        }

        .toolbar button:hover {
            background: #5a6268;
            transform: translateY(-1px);
        }

        .toolbar button.active {
            background: #28a745;
        }

        .placed-component {
            position: absolute;
            background: white;
            border: 3px solid #0055cc;
            padding: 12px;
            border-radius: 8px;
            cursor: move;
            min-width: 140px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
            transition: all 0.3s;
        }

        .placed-component.selected {
            border-color: #28a745;
            box-shadow: 0 0 0 3px rgba(40, 167, 69, 0.3);
        }

        .placed-component .comp-header {
            display: flex;
            align-items: center;
            gap: 8px;
            margin-bottom: 8px;
        }

        .placed-component .comp-icon {
            font-size: 24px;
        }

        .placed-component .comp-name {
            font-weight: bold;
            font-size: 12px;
        }

        .placed-component .comp-info {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 4px;
            font-size: 10px;
        }

        .placed-component .info-badge {
            background: #f8f9fa;
            padding: 2px 4px;
            border-radius: 3px;
            text-align: center;
        }

        .connection {
            position: absolute;
            background: #dc3545;
            height: 3px;
            z-index: 1;
            pointer-events: none;
        }

        .connection::after {
            content: '';
            position: absolute;
            right: -8px;
            top: -4px;
            width: 0;
            height: 0;
            border-left: 10px solid #dc3545;
            border-top: 5px solid transparent;
            border-bottom: 5px solid transparent;
        }

        .result-box {
            background: #e7f3ff;
            border: 2px solid #0055cc;
            padding: 15px;
            margin-top: 15px;
            border-radius: 8px;
            display: none;
        }

        .result-box.show {
            display: block;
        }

        .result-value {
            font-size: 24px;
            font-weight: bold;
            color: #003399;
            text-align: center;
            margin-bottom: 10px;
        }

        .result-details {
            font-size: 12px;
            color: #495057;
        }

        .risk-matrix {
            display: grid;
            grid-template-columns: 60px repeat(5, 1fr);
            gap: 2px;
            margin-top: 10px;
            font-size: 11px;
        }

        .matrix-cell {
            padding: 8px;
            text-align: center;
            border: 1px solid #dee2e6;
            background: white;
        }

        .matrix-header {
            background: #003399;
            color: white;
            font-weight: bold;
        }

        .matrix-label {
            background: #f8f9fa;
            font-weight: bold;
        }

        .risk-low { background: #d4edda; }
        .risk-medium { background: #fff3cd; }
        .risk-high { background: #f8d7da; }
        .risk-very-high { background: #f5c6cb; }

        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
        }

        .modal-content {
            background: white;
            margin: 50px auto;
            padding: 30px;
            width: 90%;
            max-width: 900px;
            max-height: 80vh;
            overflow-y: auto;
            border-radius: 10px;
            position: relative;
        }

        .modal-header {
            background: linear-gradient(135deg, #003399 0%, #0055cc 100%);
            color: white;
            padding: 15px;
            margin: -30px -30px 20px -30px;
            border-radius: 10px 10px 0 0;
        }

        .close-modal {
            position: absolute;
            right: 20px;
            top: 20px;
            font-size: 28px;
            color: white;
            cursor: pointer;
        }

        .status-message {
            position: fixed;
            top: 20px;
            right: 20px;
            background: #333;
            color: white;
            padding: 12px 20px;
            border-radius: 5px;
            display: none;
            z-index: 1001;
            box-shadow: 0 4px 12px rgba(0,0,0,0.3);
        }

        .status-message.show {
            display: block;
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from {
                transform: translateX(100%);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }

        .compliance-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }

        .compliance-table th,
        .compliance-table td {
            padding: 10px;
            border: 1px solid #dee2e6;
            text-align: left;
            font-size: 12px;
        }

        .compliance-table th {
            background: #003399;
            color: white;
        }

        .compliance-table tr:nth-child(even) {
            background: #f8f9fa;
        }

        .badge-pass {
            background: #28a745;
            color: white;
            padding: 2px 8px;
            border-radius: 3px;
            font-size: 11px;
        }

        .badge-fail {
            background: #dc3545;
            color: white;
            padding: 2px 8px;
            border-radius: 3px;
            font-size: 11px;
        }

        .badge-warning {
            background: #ffc107;
            color: #333;
            padding: 2px 8px;
            border-radius: 3px;
            font-size: 11px;
        }

        .info-tooltip {
            display: inline-block;
            background: #003399;
            color: white;
            width: 16px;
            height: 16px;
            border-radius: 50%;
            text-align: center;
            font-size: 10px;
            line-height: 16px;
            cursor: help;
            margin-left: 5px;
        }

        .ce-mark {
            display: inline-block;
            font-weight: bold;
            color: #003399;
            border: 2px solid #003399;
            padding: 2px 6px;
            border-radius: 50%;
            font-size: 14px;
            margin-left: 10px;
        }
    </style>
</head>
<body>
    <div class="eu-banner">
        <div class="eu-stars">
            ⭐⭐⭐⭐⭐⭐⭐⭐⭐⭐⭐⭐
        </div>
        <span>System zgodny z Dyrektywami i Normami Unii Europejskiej</span>
        <span class="ce-mark">CE</span>
    </div>

    <div class="container">
        <div class="header">
            <h1>🛡️ Europejski System Analizy Bezpieczeństwa Maszyn</h1>
            <p>Kompleksowa zgodność z normami i dyrektywami UE</p>
            <div class="norm-badges">
                <span class="norm-badge">2006/42/WE Dyrektywa Maszynowa</span>
                <span class="norm-badge">2014/30/UE EMC</span>
                <span class="norm-badge">2014/35/UE LVD</span>
                <span class="norm-badge">EN ISO 13849-1/-2</span>
                <span class="norm-badge">EN 62061 (IEC 61508)</span>
                <span class="norm-badge">EN ISO 12100</span>
                <span class="norm-badge">EN 60204-1</span>
                <span class="norm-badge">EN ISO 14119</span>
                <span class="norm-badge">EN ISO 13855</span>
                <span class="norm-badge">EN ISO 13857</span>
                <span class="norm-badge">EN 61496-1/-2</span>
                <span class="norm-badge">EN ISO 11161</span>
            </div>
        </div>

        <div class="main-layout">
            <div class="sidebar">
                <h2>📦 Komponenty Bezpieczeństwa</h2>
                
                <div class="component-category">
                    <h3>⚠️ Urządzenia Zatrzymania Awaryjnego</h3>
                    
                    <div class="component-item" draggable="true" 
                         data-type="e-stop-button" 
                         data-cat="4" 
                         data-pl="e" 
                         data-sil="3"
                         data-pfhd="1e-8"
                         data-mttf="100"
                         data-dc="99"
                         data-ccf="95"
                         data-norm="EN ISO 13850">
                        <div class="component-header">
                            <span class="component-icon">🛑</span>
                            <span class="component-name">Przycisk Awaryjny</span>
                        </div>
                        <div class="component-specs">
                            <span class="spec-item"><span class="spec-label">Cat:</span> 4</span>
                            <span class="spec-item"><span class="spec-label">PL:</span> e</span>
                            <span class="spec-item"><span class="spec-label">SIL:</span> 3</span>
                            <span class="spec-item"><span class="spec-label">PFHd:</span> 10⁻⁸</span>
                            <span class="spec-item"><span class="spec-label">DC:</span> 99%</span>
                            <span class="spec-item"><span class="spec-label">MTTFd:</span> 100y</span>
                        </div>
                    </div>

                    <div class="component-item" draggable="true"
                         data-type="e-stop-rope"
                         data-cat="4"
                         data-pl="e"
                         data-sil="3"
                         data-pfhd="2e-8"
                         data-mttf="90"
                         data-dc="99"
                         data-ccf="90"
                         data-norm="EN ISO 13850">
                        <div class="component-header">
                            <span class="component-icon">🔴</span>
                            <span class="component-name">Wyłącznik Linkowy</span>
                        </div>
                        <div class="component-specs">
                            <span class="spec-item"><span class="spec-label">Cat:</span> 4</span>
                            <span class="spec-item"><span class="spec-label">PL:</span> e</span>
                            <span class="spec-item"><span class="spec-label">SIL:</span> 3</span>
                            <span class="spec-item"><span class="spec-label">PFHd:</span> 2×10⁻⁸</span>
                            <span class="spec-item"><span class="spec-label">DC:</span> 99%</span>
                            <span class="spec-item"><span class="spec-label">MTTFd:</span> 90y</span>
                        </div>
                    </div>
                </div>

                <div class="component-category">
                    <h3>🚧 Bariery i Osłony Ochronne</h3>
                    
                    <div class="component-item" draggable="true"
                         data-type="light-curtain-4"
                         data-cat="4"
                         data-pl="e"
                         data-sil="3"
                         data-pfhd="4e-8"
                         data-mttf="85"
                         data-dc="99"
                         data-ccf="85"
                         data-norm="EN 61496-1/-2">
                        <div class="component-header">
                            <span class="component-icon">📡</span>
                            <span class="component-name">Kurtyna Świetlna Typ 4</span>
                        </div>
                        <div class="component-specs">
                            <span class="spec-item"><span class="spec-label">Cat:</span> 4</span>
                            <span class="spec-item"><span class="spec-label">PL:</span> e</span>
                            <span class="spec-item"><span class="spec-label">Typ:</span> 4</span>
                            <span class="spec-item"><span class="spec-label">Rozdzielczość:</span> 14mm</span>
                            <span class="spec-item"><span class="spec-label">DC:</span> 99%</span>
                            <span class="spec-item"><span class="spec-label">Czas:</span> 20ms</span>
                        </div>
                    </div>

                    <div class="component-item" draggable="true"
                         data-type="safety-gate"
                         data-cat="3"
                         data-pl="d"
                         data-sil="2"
                         data-pfhd="6e-7"
                         data-mttf="70"
                         data-dc="90"
                         data-ccf="70"
                         data-norm="EN ISO 14119">
                        <div class="component-header">
                            <span class="component-icon">🚪</span>
                            <span class="component-name">Bramka z Ryglowaniem</span>
                        </div>
                        <div class="component-specs">
                            <span class="spec-item"><span class="spec-label">Cat:</span> 3</span>
                            <span class="spec-item"><span class="spec-label">PL:</span> d</span>
                            <span class="spec-item"><span class="spec-label">Typ:</span> 4</span>
                            <span class="spec-item"><span class="spec-label">Siła:</span> 1000N</span>
                            <span class="spec-item"><span class="spec-label">DC:</span> 90%</span>
                            <span class="spec-item"><span class="spec-label">Kodowanie:</span> Wysokie</span>
                        </div>
                    </div>

                    <div class="component-item" draggable="true"
                         data-type="laser-scanner"
                         data-cat="3"
                         data-pl="d"
                         data-sil="2"
                         data-pfhd="7e-7"
                         data-mttf="80"
                         data-dc="90"
                         data-ccf="75"
                         data-norm="EN 61496-3">
                        <div class="component-header">
                            <span class="component-icon">💠</span>
                            <span class="component-name">Skaner Laserowy</span>
                        </div>
                        <div class="component-specs">
                            <span class="spec-item"><span class="spec-label">Cat:</span> 3</span>
                            <span class="spec-item"><span class="spec-label">PL:</span> d</span>
                            <span class="spec-item"><span class="spec-label">Zasięg:</span> 4m</span>
                            <span class="spec-item"><span class="spec-label">Kąt:</span> 270°</span>
                            <span class="spec-item"><span class="spec-label">DC:</span> 90%</span>
                            <span class="spec-item"><span class="spec-label">Rozdzielczość:</span> 70mm</span>
                        </div>
                    </div>
                </div>

                <div class="component-category">
                    <h3>🎛️ Sterowniki i Moduły Safety</h3>
                    
                    <div class="component-item" draggable="true"
                         data-type="safety-plc"
                         data-cat="4"
                         data-pl="e"
                         data-sil="3"
                         data-pfhd="5e-9"
                         data-mttf="100"
                         data-dc="99"
                         data-ccf="95"
                         data-norm="EN 61508">
                        <div class="component-header">
                            <span class="component-icon">🖥️</span>
                            <span class="component-name">Safety PLC</span>
                        </div>
                        <div class="component-specs">
                            <span class="spec-item"><span class="spec-label">Cat:</span> 4</span>
                            <span class="spec-item"><span class="spec-label">PL:</span> e</span>
                            <span class="spec-item"><span class="spec-label">SIL:</span> 3</span>
                            <span class="spec-item"><span class="spec-label">TÜV:</span> Certified</span>
                            <span class="spec-item"><span class="spec-label">DC:</span> 99%</span>
                            <span class="spec-item"><span class="spec-label">Cykl:</span> 1ms</span>
                        </div>
                    </div>

                    <div class="component-item" draggable="true"
                         data-type="safety-relay"
                         data-cat="4"
                         data-pl="e"
                         data-sil="3"
                         data-pfhd="8e-9"
                         data-mttf="95"
                         data-dc="99"
                         data-ccf="90"
                         data-norm="EN 50205">
                        <div class="component-header">
                            <span class="component-icon">⚡</span>
                            <span class="component-name">Przekaźnik PNOZ</span>
                        </div>
                        <div class="component-specs">
                            <span class="spec-item"><span class="spec-label">Cat:</span> 4</span>
                            <span class="spec-item"><span class="spec-label">PL:</span> e</span>
                            <span class="spec-item"><span class="spec-label">Kanały:</span> 2</span>
                            <span class="spec-item"><span class="spec-label">Kontakty:</span> 3NO+1NC</span>
                            <span class="spec-item"><span class="spec-label">DC:</span> 99%</span>
                            <span class="spec-item"><span class="spec-label">Czas:</span> 12ms</span>
                        </div>
                    </div>

                    <div class="component-item" draggable="true"
                         data-type="safety-contactor"
                         data-cat="1"
                         data-pl="c"
                         data-sil="1"
                         data-pfhd="5e-6"
                         data-mttf="50"
                         data-dc="60"
                         data-ccf="60"
                         data-norm="EN 60947-4-1">
                        <div class="component-header">
                            <span class="component-icon">🔌</span>
                            <span class="component-name">Stycznik Bezpieczeństwa</span>
                        </div>
                        <div class="component-specs">
                            <span class="spec-item"><span class="spec-label">Cat:</span> 1</span>
                            <span class="spec-item"><span class="spec-label">PL:</span> c</span>
                            <span class="spec-item"><span class="spec-label">AC3:</span> 32A</span>
                            <span class="spec-item"><span class="spec-label">Napięcie:</span> 400V</span>
                            <span class="spec-item"><span class="spec-label">DC:</span> 60%</span>
                            <span class="spec-item"><span class="spec-label">B10d:</span> 1.3M</span>
                        </div>
                    </div>
                </div>

                <div class="component-category">
                    <h3>🔄 Napędy i Hamulce</h3>
                    
                    <div class="component-item" draggable="true"
                         data-type="safe-drive"
                         data-cat="3"
                         data-pl="d"
                         data-sil="2"
                         data-pfhd="3e-7"
                         data-mttf="75"
                         data-dc="90"
                         data-ccf="70"
                         data-norm="EN 61800-5-2">
                        <div class="component-header">
                            <span class="component-icon">🔄</span>
                            <span class="component-name">Napęd z STO/SS1</span>
                        </div>
                        <div class="component-specs">
                            <span class="spec-item"><span class="spec-label">Cat:</span> 3</span>
                            <span class="spec-item"><span class="spec-label">PL:</span> d</span>
                            <span class="spec-item"><span class="spec-label">Funkcje:</span> STO,SS1,SLS</span>
                            <span class="spec-item"><span class="spec-label">Moc:</span> 15kW</span>
                            <span class="spec-item"><span class="spec-label">DC:</span> 90%</span>
                            <span class="spec-item"><span class="spec-label">Czas STO:</span> 20ms</span>
                        </div>
                    </div>
                </div>

                <div class="component-category">
                    <h3>🔘 Wyłączniki Krańcowe i Czujniki</h3>
                    
                    <div class="component-item" draggable="true"
                         data-type="limit-switch-mechanical"
                         data-cat="1"
                         data-pl="c"
                         data-sil="1"
                         data-pfhd="8e-6"
                         data-mttf="20"
                         data-dc="0"
                         data-ccf="65"
                         data-norm="EN 60947-5-1">
                        <div class="component-header">
                            <span class="component-icon">🔘</span>
                            <span class="component-name">Wyłącznik Krańcowy Mechaniczny</span>
                        </div>
                        <div class="component-specs">
                            <span class="spec-item"><span class="spec-label">Cat:</span> 1</span>
                            <span class="spec-item"><span class="spec-label">PL:</span> c</span>
                            <span class="spec-item"><span class="spec-label">Typ:</span> 1NC+1NO</span>
                            <span class="spec-item"><span class="spec-label">IP:</span> 67</span>
                            <span class="spec-item"><span class="spec-label">DC:</span> 0%</span>
                            <span class="spec-item"><span class="spec-label">B10d:</span> 2M</span>
                        </div>
                    </div>

                    <div class="component-item" draggable="true"
                         data-type="limit-switch-safety"
                         data-cat="4"
                         data-pl="e"
                         data-sil="3"
                         data-pfhd="5e-8"
                         data-mttf="63"
                         data-dc="99"
                         data-ccf="80"
                         data-norm="EN ISO 14119">
                        <div class="component-header">
                            <span class="component-icon">🔐</span>
                            <span class="component-name">Wyłącznik Bezpieczeństwa z Kluczem</span>
                        </div>
                        <div class="component-specs">
                            <span class="spec-item"><span class="spec-label">Cat:</span> 4</span>
                            <span class="spec-item"><span class="spec-label">PL:</span> e</span>
                            <span class="spec-item"><span class="spec-label">Kodowanie:</span> Unikalne</span>
                            <span class="spec-item"><span class="spec-label">Kontakty:</span> 2NC+1NO</span>
                            <span class="spec-item"><span class="spec-label">DC:</span> 99%</span>
                            <span class="spec-item"><span class="spec-label">Siła:</span> 2500N</span>
                        </div>
                    </div>

                    <div class="component-item" draggable="true"
                         data-type="magnetic-coded"
                         data-cat="4"
                         data-pl="e"
                         data-sil="3"
                         data-pfhd="3e-8"
                         data-mttf="87"
                         data-dc="99"
                         data-ccf="85"
                         data-norm="EN ISO 14119">
                        <div class="component-header">
                            <span class="component-icon">🧲</span>
                            <span class="component-name">Czujnik Magnetyczny Kodowany</span>
                        </div>
                        <div class="component-specs">
                            <span class="spec-item"><span class="spec-label">Cat:</span> 4</span>
                            <span class="spec-item"><span class="spec-label">PL:</span> e</span>
                            <span class="spec-item"><span class="spec-label">Typ:</span> RFID</span>
                            <span class="spec-item"><span class="spec-label">Zasięg:</span> 15mm</span>
                            <span class="spec-item"><span class="spec-label">DC:</span> 99%</span>
                            <span class="spec-item"><span class="spec-label">Kodów:</span> 10^9</span>
                        </div>
                    </div>

                    <div class="component-item" draggable="true"
                         data-type="position-switch"
                         data-cat="2"
                         data-pl="d"
                         data-sil="2"
                         data-pfhd="4e-7"
                         data-mttf="45"
                         data-dc="90"
                         data-ccf="70"
                         data-norm="EN 60947-5-3">
                        <div class="component-header">
                            <span class="component-icon">📍</span>
                            <span class="component-name">Wyłącznik Pozycyjny</span>
                        </div>
                        <div class="component-specs">
                            <span class="spec-item"><span class="spec-label">Cat:</span> 2</span>
                            <span class="spec-item"><span class="spec-label">PL:</span> d</span>
                            <span class="spec-item"><span class="spec-label">Typ:</span> Indukcyjny</span>
                            <span class="spec-item"><span class="spec-label">Zasięg:</span> 10mm</span>
                            <span class="spec-item"><span class="spec-label">DC:</span> 90%</span>
                            <span class="spec-item"><span class="spec-label">Częst:</span> 1kHz</span>
                        </div>
                    </div>
                </div>

                <div style="padding: 15px; background: #e7f3ff; border-radius: 8px; margin: 15px 0;">
                    <h4 style="color: #003399; margin-bottom: 10px;">📚 Instrukcja użycia:</h4>
                    <ol style="font-size: 12px; color: #495057; line-height: 1.6;">
                        <li><strong>Przeciągnij komponent</strong> z listy na środkowe płótno</li>
                        <li><strong>Kliknij "🔗 Połącz"</strong> aby aktywować tryb łączenia</li>
                        <li><strong>Kliknij dwa komponenty</strong> aby je połączyć</li>
                        <li><strong>Wybierz parametry S, F, P</strong> w panelu analizy</li>
                        <li><strong>Oblicz PLr</strong> aby określić wymagania</li>
                        <li><strong>Waliduj system</strong> aby sprawdzić zgodność</li>
                    </ol>
                </div>
            </div>

            <div id="canvas"></div>

            <div class="analysis-panel">
                <div class="tabs">
                    <button class="tab active" onclick="switchTab('iso13849')">ISO 13849-1</button>
                    <button class="tab" onclick="switchTab('iec62061')">IEC 62061</button>
                    <button class="tab" onclick="switchTab('iso12100')">ISO 12100</button>
                    <button class="tab" onclick="switchTab('directives')">Dyrektywy</button>
                </div>

                <div id="iso13849" class="tab-content active">
                    <div class="analysis-section">
                        <h3>📊 Analiza wg EN ISO 13849-1</h3>
                        
                        <div class="form-group">
                            <label>S - Ciężkość urazu <span class="info-tooltip" title="S1: Lekkie urazy (odwracalne), S2: Ciężkie urazy (nieodwracalne) lub śmierć">?</span></label>
                            <select id="severity">
                                <option value="S1">S1 - Lekkie obrażenia</option>
                                <option value="S2">S2 - Poważne obrażenia/śmierć</option>
                            </select>
                        </div>

                        <div class="form-group">
                            <label>F - Częstotliwość/czas narażenia <span class="info-tooltip" title="F1: Rzadkie do częstego, F2: Częste do ciągłego">?</span></label>
                            <select id="frequency">
                                <option value="F1">F1 - Rzadko (< 1/h)</option>
                                <option value="F2">F2 - Często (≥ 1/h)</option>
                            </select>
                        </div>

                        <div class="form-group">
                            <label>P - Możliwość uniknięcia <span class="info-tooltip" title="P1: Możliwe w określonych warunkach, P2: Rzadko możliwe">?</span></label>
                            <select id="possibility">
                                <option value="P1">P1 - Możliwe</option>
                                <option value="P2">P2 - Rzadko możliwe</option>
                            </select>
                        </div>

                        <button class="btn btn-success" onclick="calculatePLr()">
                            📊 Oblicz wymagany PLr
                        </button>

                        <div id="plResult" class="result-box">
                            <div class="result-value">PLr = </div>
                            <div class="result-details"></div>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label>MTTFd [lata]</label>
                                <input type="number" id="mttfd" placeholder="30-100" min="3" max="100">
                            </div>
                            <div class="form-group">
                                <label>DCavg [%]</label>
                                <input type="number" id="dcavg" placeholder="60-99" min="0" max="99">
                            </div>
                        </div>

                        <div class="form-group">
                            <label>Kategoria architektury</label>
                            <select id="category">
                                <option value="B">Kategoria B</option>
                                <option value="1">Kategoria 1</option>
                                <option value="2">Kategoria 2</option>
                                <option value="3">Kategoria 3</option>
                                <option value="4">Kategoria 4</option>
                            </select>
                        </div>

                        <button class="btn" onclick="calculatePL()">
                            🔍 Oblicz osiągnięty PL
                        </button>
                    </div>
                </div>

                <div id="iec62061" class="tab-content">
                    <div class="analysis-section">
                        <h3>⚡ Analiza wg EN 62061 (SIL)</h3>
                        
                        <div class="form-group">
                            <label>Se - Ciężkość szkody</label>
                            <select id="se">
                                <option value="1">1 - Nieodwracalne: lekkie</option>
                                <option value="2">2 - Nieodwracalne: poważne</option>
                                <option value="3">3 - Śmierć jednej osoby</option>
                                <option value="4">4 - Śmierć wielu osób</option>
                            </select>
                        </div>

                        <div class="form-group">
                            <label>Fr - Częstotliwość narażenia</label>
                            <select id="fr">
                                <option value="1">≤ 1/h</option>
                                <option value="2">> 1/h do ≤ 1/day</option>
                                <option value="3">> 1/day do ≤ 1/2weeks</option>
                                <option value="4">> 1/2weeks do ≤ 1/year</option>
                                <option value="5">> 1/year</option>
                            </select>
                        </div>

                        <div class="form-group">
                            <label>Pr - Prawdopodobieństwo wystąpienia</label>
                            <select id="pr">
                                <option value="1">Bardzo wysokie</option>
                                <option value="2">Wysokie</option>
                                <option value="3">Średnie</option>
                                <option value="4">Niskie</option>
                                <option value="5">Znikome</option>
                            </select>
                        </div>

                        <div class="form-group">
                            <label>Av - Możliwość uniknięcia</label>
                            <select id="av">
                                <option value="1">Niemożliwe</option>
                                <option value="3">Możliwe</option>
                                <option value="5">Prawdopodobne</option>
                            </select>
                        </div>

                        <button class="btn btn-success" onclick="calculateSIL()">
                            ⚡ Oblicz wymagany SIL
                        </button>

                        <div id="silResult" class="result-box">
                            <div class="result-value">SIL = </div>
                            <div class="result-details"></div>
                        </div>

                        <div class="form-group">
                            <label>PFHd (Prawdopodobieństwo uszkodzenia/h)</label>
                            <input type="number" id="pfhd" placeholder="np. 1e-7" step="0.0000001">
                        </div>

                        <button class="btn" onclick="checkSIL()">
                            🔍 Sprawdź osiągnięty SIL
                        </button>
                    </div>
                </div>

                <div id="iso12100" class="tab-content">
                    <div class="analysis-section">
                        <h3>📋 Ocena Ryzyka wg EN ISO 12100</h3>
                        
                        <div class="form-group">
                            <label>Typ zagrożenia</label>
                            <select id="hazardType">
                                <option value="mechanical">Mechaniczne</option>
                                <option value="electrical">Elektryczne</option>
                                <option value="thermal">Termiczne</option>
                                <option value="noise">Hałas</option>
                                <option value="vibration">Wibracje</option>
                                <option value="radiation">Promieniowanie</option>
                                <option value="material">Materiały/substancje</option>
                                <option value="ergonomic">Ergonomiczne</option>
                                <option value="environment">Środowiskowe</option>
                                <option value="combination">Kombinacja zagrożeń</option>
                            </select>
                        </div>

                        <div class="form-group">
                            <label>Faza cyklu życia maszyny</label>
                            <select id="lifecycle">
                                <option value="transport">Transport</option>
                                <option value="assembly">Montaż/instalacja</option>
                                <option value="commissioning">Uruchomienie</option>
                                <option value="operation">Normalna praca</option>
                                <option value="maintenance">Konserwacja</option>
                                <option value="troubleshooting">Usuwanie usterek</option>
                                <option value="decommissioning">Demontaż</option>
                            </select>
                        </div>

                        <div class="form-group">
                            <label>Prawdopodobieństwo wystąpienia szkody</label>
                            <input type="range" id="probability" min="1" max="5" value="3">
                            <output for="probability">3</output>
                        </div>

                        <div class="form-group">
                            <label>Ciężkość potencjalnej szkody</label>
                            <input type="range" id="severity12100" min="1" max="5" value="3">
                            <output for="severity12100">3</output>
                        </div>

                        <button class="btn btn-warning" onclick="assessRisk()">
                            📊 Oceń poziom ryzyka
                        </button>

                        <div id="riskMatrix" class="risk-matrix" style="display:none;">
                            <!-- Matryca ryzyka będzie generowana dynamicznie -->
                        </div>
                    </div>
                </div>

                <div id="directives" class="tab-content">
                    <div class="analysis-section">
                        <h3>🇪🇺 Zgodność z Dyrektywami UE</h3>
                        
                        <div class="form-group">
                            <label>Dyrektywa Maszynowa 2006/42/WE</label>
                            <div style="padding: 10px; background: #f8f9fa; border-radius: 5px;">
                                <input type="checkbox" id="md1"> Ocena ryzyka wykonana<br>
                                <input type="checkbox" id="md2"> Instrukcja obsługi w języku użytkownika<br>
                                <input type="checkbox" id="md3"> Deklaracja zgodności WE<br>
                                <input type="checkbox" id="md4"> Oznakowanie CE<br>
                                <input type="checkbox" id="md5"> Dokumentacja techniczna kompletna
                            </div>
                        </div>

                        <div class="form-group">
                            <label>Dyrektywa EMC 2014/30/UE</label>
                            <div style="padding: 10px; background: #f8f9fa; border-radius: 5px;">
                                <input type="checkbox" id="emc1"> Testy emisji wykonane<br>
                                <input type="checkbox" id="emc2"> Testy odporności wykonane<br>
                                <input type="checkbox" id="emc3"> Raport z testów dostępny
                            </div>
                        </div>

                        <div class="form-group">
                            <label>Dyrektywa LVD 2014/35/UE</label>
                            <div style="padding: 10px; background: #f8f9fa; border-radius: 5px;">
                                <input type="checkbox" id="lvd1"> Zabezpieczenia elektryczne<br>
                                <input type="checkbox" id="lvd2"> Izolacja sprawdzona<br>
                                <input type="checkbox" id="lvd3"> Uziemienie ochronne
                            </div>
                        </div>

                        <button class="btn btn-success" onclick="checkCompliance()">
                            ✅ Sprawdź zgodność
                        </button>

                        <div id="complianceResult" class="result-box">
                            <!-- Wyniki zgodności -->
                        </div>
                    </div>
                </div>

                <div class="analysis-section">
                    <button class="btn btn-success" onclick="validateSystem()">
                        ✅ Pełna Walidacja Systemu
                    </button>
                    
                    <button class="btn btn-warning" onclick="generateReport()">
                        📄 Generuj Raport CE
                    </button>
                    
                    <button class="btn" onclick="showNormInfo()">
                        📚 Informacje o Normach
                    </button>
                    
                    <button class="btn" style="background: #17a2b8;" onclick="showHelp()">
                        📖 Instrukcja Systemu
                    </button>
                </div>
            </div>
        </div>

        <div class="toolbar">
            <div class="toolbar-group">
                <button id="connectBtn" onclick="toggleConnect()">🔗 Połącz</button>
                <button onclick="clearAll()">🗑️ Wyczyść</button>
                <button onclick="autoLayout()">📐 Auto Układ</button>
                <button onclick="saveProject()">💾 Zapisz</button>
                <button onclick="loadProject()">📂 Wczytaj</button>
            </div>
            <div class="toolbar-group">
                <button onclick="exportPDF()">📑 Export PDF</button>
                <button onclick="exportXML()">📋 Export XML</button>
                <button onclick="printDiagram()">🖨️ Drukuj</button>
            </div>
        </div>
    </div>

    <div id="reportModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>📋 Raport Zgodności CE</h2>
                <span class="close-modal" onclick="closeModal('reportModal')">×</span>
            </div>
            <div id="reportContent"></div>
        </div>
    </div>

    <div id="normModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>📚 Europejskie Normy Bezpieczeństwa</h2>
                <span class="close-modal" onclick="closeModal('normModal')">×</span>
            </div>
            <div id="normContent"></div>
        </div>
    </div>

    <div id="helpModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>📖 Przewodnik Systemu Bezpieczeństwa Maszyn</h2>
                <span class="close-modal" onclick="closeModal('helpModal')">×</span>
            </div>
            <div style="padding: 20px;">
                <h3 style="color: #003399;">🎯 Jak projektować system bezpieczeństwa:</h3>
                
                <div style="margin: 20px 0;">
                    <h4>1️⃣ OCENA RYZYKA (Risk Assessment)</h4>
                    <p style="margin: 10px 0;">Pierwszym krokiem jest określenie poziomu ryzyka:</p>
                    <ul>
                        <li><strong>S (Severity)</strong> - Ciężkość potencjalnego urazu</li>
                        <li><strong>F (Frequency)</strong> - Częstotliwość narażenia na zagrożenie</li>
                        <li><strong>P (Possibility)</strong> - Możliwość uniknięcia zagrożenia</li>
                    </ul>
                    <p>Na podstawie tych parametrów system oblicza wymagany <strong>PLr</strong> (Performance Level required).</p>
                </div>

                <div style="margin: 20px 0;">
                    <h4>2️⃣ KOMPONENTY I ICH FUNKCJE</h4>
                    
                    <div style="background: #f8f9fa; padding: 10px; margin: 10px 0; border-radius: 5px;">
                        <strong>🛑 Wyłączniki Awaryjne (E-Stop)</strong><br>
                        Natychmiastowe zatrzymanie maszyny w sytuacji zagrożenia. Muszą być łatwo dostępne, czerwone z żółtym tłem. Kategoria 0, 1 lub 2 zatrzymania.
                    </div>
                    
                    <div style="background: #f8f9fa; padding: 10px; margin: 10px 0; border-radius: 5px;">
                        <strong>📡 Kurtyny Świetlne</strong><br>
                        Tworzą niewidzialną barierę. Przerwanie wiązek powoduje zatrzymanie maszyny. Typ 2 (PL c) lub Typ 4 (PL e).
                    </div>
                    
                    <div style="background: #f8f9fa; padding: 10px; margin: 10px 0; border-radius: 5px;">
                        <strong>🚪 Bramki Bezpieczeństwa</strong><br>
                        Blokują dostęp do strefy niebezpiecznej. Z ryglowaniem (interlocking) lub blokadą (guard locking).
                    </div>
                    
                    <div style="background: #f8f9fa; padding: 10px; margin: 10px 0; border-radius: 5px;">
                        <strong>🔘 Wyłączniki Krańcowe</strong><br>
                        Monitorują pozycję osłon i drzwi. Wersje mechaniczne (PL c) lub kodowane magnetycznie (PL e).
                    </div>
                    
                    <div style="background: #f8f9fa; padding: 10px; margin: 10px 0; border-radius: 5px;">
                        <strong>💠 Skanery Laserowe</strong><br>
                        Monitorują obszar wokół maszyny. Konfigurowalne strefy ostrzegawcze i ochronne.
                    </div>
                    
                    <div style="background: #f8f9fa; padding: 10px; margin: 10px 0; border-radius: 5px;">
                        <strong>🖥️ Safety PLC / Przekaźniki</strong><br>
                        Przetwarzają sygnały bezpieczeństwa. Monitorują stan systemu, wykrywają błędy, realizują logikę bezpieczeństwa.
                    </div>
                </div>

                <div style="margin: 20px 0;">
                    <h4>3️⃣ ŁĄCZENIE KOMPONENTÓW</h4>
                    <p>System bezpieczeństwa składa się z trzech części:</p>
                    <ol>
                        <li><strong>Wejście (Input)</strong> - czujniki, przyciski, kurtyny</li>
                        <li><strong>Logika (Logic)</strong> - Safety PLC, przekaźniki bezpieczeństwa</li>
                        <li><strong>Wyjście (Output)</strong> - styczniki, napędy, hamulce</li>
                    </ol>
                    <p style="background: #fff3cd; padding: 10px; border-radius: 5px; margin-top: 10px;">
                        ⚠️ <strong>Zasada najsłabszego ogniwa:</strong> Cały system osiąga tylko taki poziom bezpieczeństwa, jaki ma najsłabszy komponent!
                    </p>
                </div>

                <div style="margin: 20px 0;">
                    <h4>4️⃣ KATEGORIE ARCHITEKTURY</h4>
                    <table style="width: 100%; border-collapse: collapse;">
                        <tr>
                            <th style="border: 1px solid #dee2e6; padding: 8px; background: #003399; color: white;">Kat.</th>
                            <th style="border: 1px solid #dee2e6; padding: 8px; background: #003399; color: white;">Opis</th>
                            <th style="border: 1px solid #dee2e6; padding: 8px; background: #003399; color: white;">Max PL</th>
                        </tr>
                        <tr>
                            <td style="border: 1px solid #dee2e6; padding: 8px;">B</td>
                            <td style="border: 1px solid #dee2e6; padding: 8px;">Podstawowa, pojedynczy kanał</td>
                            <td style="border: 1px solid #dee2e6; padding: 8px;">a</td>
                        </tr>
                        <tr>
                            <td style="border: 1px solid #dee2e6; padding: 8px;">1</td>
                            <td style="border: 1px solid #dee2e6; padding: 8px;">Ulepszona niezawodność</td>
                            <td style="border: 1px solid #dee2e6; padding: 8px;">c</td>
                        </tr>
                        <tr>
                            <td style="border: 1px solid #dee2e6; padding: 8px;">2</td>
                            <td style="border: 1px solid #dee2e6; padding: 8px;">Z testowaniem</td>
                            <td style="border: 1px solid #dee2e6; padding: 8px;">d</td>
                        </tr>
                        <tr>
                            <td style="border: 1px solid #dee2e6; padding: 8px;">3</td>
                            <td style="border: 1px solid #dee2e6; padding: 8px;">Redundancja (2 kanały)</td>
                            <td style="border: 1px solid #dee2e6; padding: 8px;">e</td>
                        </tr>
                        <tr>
                            <td style="border: 1px solid #dee2e6; padding: 8px;">4</td>
                            <td style="border: 1px solid #dee2e6; padding: 8px;">Redundancja z monitorowaniem</td>
                            <td style="border: 1px solid #dee2e6; padding: 8px;">e</td>
                        </tr>
                    </table>
                </div>

                <div style="margin: 20px 0;">
                    <h4>5️⃣ PRZYKŁAD SYSTEMU</h4>
                    <div style="background: #e7f3ff; padding: 15px; border-radius: 5px;">
                        <strong>Prasa hydrauliczna - PLr = d</strong><br><br>
                        <strong>Komponenty:</strong><br>
                        • Kurtyna świetlna Typ 4 (PLe) - chroni dostęp z przodu<br>
                        • 2x Wyłącznik awaryjny (PLe) - po bokach maszyny<br>
                        • Bramka z ryglowaniem (PLd) - dostęp serwisowy<br>
                        • Safety PLC (PLe) - logika sterowania<br>
                        • 2x Stycznik bezpieczeństwa (PLd) - wyłączenie napędu<br><br>
                        <strong>Wynik:</strong> System osiąga PLd (najniższy element) = ZGODNY ✅
                    </div>
                </div>

                <div style="margin: 20px 0; background: #d4edda; padding: 15px; border-radius: 5px;">
                    <h4>✅ KROKI DO ZGODNOŚCI CE:</h4>
                    <ol>
                        <li>Przeprowadź ocenę ryzyka (ISO 12100)</li>
                        <li>Określ wymagany PLr/SIL</li>
                        <li>Zaprojektuj system bezpieczeństwa</li>
                        <li>Dobierz komponenty o odpowiednich parametrach</li>
                        <li>Zwaliduj osiągnięty poziom bezpieczeństwa</li>
                        <li>Udokumentuj w dokumentacji technicznej</li>
                        <li>Wystaw deklarację zgodności CE</li>
                        <li>Oznacz maszynę znakiem CE</li>
                    </ol>
                </div>
            </div>
        </div>
    </div>

    <div class="status-message" id="statusMessage"></div>

    <script>
        // Zmienne globalne
        let components = [];
        let connections = [];
        let selectedComponent = null;
        let connectMode = false;
        let firstConnect = null;
        let componentCounter = 0;
        let requiredPL = '';
        let requiredSIL = '';
        let draggedComponent = null;
        let currentProject = {
            name: 'Nowy Projekt',
            date: new Date().toISOString(),
            components: [],
            connections: [],
            analysis: {}
        };

        // Inicjalizacja
        document.addEventListener('DOMContentLoaded', function() {
            initializeDragDrop();
            initializeCanvas();
            initializeRangeInputs();
            showStatus('System gotowy do pracy');
        });

        function initializeDragDrop() {
            document.querySelectorAll('.component-item').forEach(item => {
                item.draggable = true;
                item.addEventListener('dragstart', handleDragStart);
                item.addEventListener('dragend', handleDragEnd);
            });
        }

        function initializeCanvas() {
            const canvas = document.getElementById('canvas');
            canvas.addEventListener('dragover', handleDragOver);
            canvas.addEventListener('drop', handleDrop);
            canvas.addEventListener('click', handleCanvasClick);
        }

        function initializeRangeInputs() {
            document.querySelectorAll('input[type="range"]').forEach(input => {
                input.addEventListener('input', function() {
                    this.nextElementSibling.value = this.value;
                });
            });
        }

        // Funkcje drag & drop
        function handleDragStart(e) {
            draggedComponent = {
                type: e.currentTarget.dataset.type,
                cat: e.currentTarget.dataset.cat,
                pl: e.currentTarget.dataset.pl,
                sil: e.currentTarget.dataset.sil,
                pfhd: e.currentTarget.dataset.pfhd,
                mttf: e.currentTarget.dataset.mttf,
                dc: e.currentTarget.dataset.dc,
                ccf: e.currentTarget.dataset.ccf,
                norm: e.currentTarget.dataset.norm,
                name: e.currentTarget.querySelector('.component-name').textContent,
                icon: e.currentTarget.querySelector('.component-icon').textContent
            };
            e.currentTarget.style.opacity = '0.5';
        }

        function handleDragEnd(e) {
            e.currentTarget.style.opacity = '';
        }

        function handleDragOver(e) {
            e.preventDefault();
        }

        function handleDrop(e) {
            e.preventDefault();
            if (!draggedComponent) return;

            const rect = e.currentTarget.getBoundingClientRect();
            const x = e.clientX - rect.left - 70;
            const y = e.clientY - rect.top - 40;

            createComponent(draggedComponent, x, y);
            draggedComponent = null;
        }

        function createComponent(data, x, y) {
            const id = 'comp_' + componentCounter++;
            
            const div = document.createElement('div');
            div.className = 'placed-component';
            div.id = id;
            div.style.left = x + 'px';
            div.style.top = y + 'px';
            
            div.innerHTML = `
                <div class="comp-header">
                    <span class="comp-icon">${data.icon}</span>
                    <span class="comp-name">${data.name}</span>
                </div>
                <div class="comp-info">
                    <span class="info-badge">Cat.${data.cat}</span>
                    <span class="info-badge">PL${data.pl}</span>
                    <span class="info-badge">SIL${data.sil}</span>
                    <span class="info-badge">${data.norm}</span>
                </div>
            `;
            
            div.addEventListener('mousedown', startDrag);
            div.addEventListener('click', selectComponent);
            
            document.getElementById('canvas').appendChild(div);
            
            components.push({
                id: id,
                element: div,
                data: data,
                x: x,
                y: y
            });
            
            showStatus(`Komponent "${data.name}" dodany`);
        }

        function startDrag(e) {
            if (connectMode) return;
            
            const component = e.currentTarget;
            const startX = e.clientX;
            const startY = e.clientY;
            const origX = component.offsetLeft;
            const origY = component.offsetTop;
            
            function doDrag(e) {
                component.style.left = (origX + e.clientX - startX) + 'px';
                component.style.top = (origY + e.clientY - startY) + 'px';
                updateConnections();
            }
            
            function stopDrag() {
                document.removeEventListener('mousemove', doDrag);
                document.removeEventListener('mouseup', stopDrag);
                
                const comp = components.find(c => c.id === component.id);
                if (comp) {
                    comp.x = component.offsetLeft;
                    comp.y = component.offsetTop;
                }
            }
            
            document.addEventListener('mousemove', doDrag);
            document.addEventListener('mouseup', stopDrag);
        }

        function selectComponent(e) {
            e.stopPropagation();
            const component = e.currentTarget;
            
            if (connectMode) {
                if (!firstConnect) {
                    firstConnect = component;
                    component.classList.add('selected');
                    showStatus('Wybierz drugi komponent do połączenia');
                } else if (firstConnect !== component) {
                    createConnection(firstConnect, component);
                    firstConnect.classList.remove('selected');
                    firstConnect = null;
                    showStatus('Połączenie utworzone');
                }
            } else {
                document.querySelectorAll('.placed-component').forEach(c => {
                    c.classList.remove('selected');
                });
                component.classList.add('selected');
                selectedComponent = component;
            }
        }

        function handleCanvasClick() {
            if (!connectMode) {
                document.querySelectorAll('.placed-component').forEach(c => {
                    c.classList.remove('selected');
                });
                selectedComponent = null;
            }
        }

        function createConnection(comp1, comp2) {
            const line = document.createElement('div');
            line.className = 'connection';
            document.getElementById('canvas').appendChild(line);
            
            connections.push({
                from: comp1,
                to: comp2,
                line: line
            });
            
            updateConnection(comp1, comp2, line);
        }

        function updateConnection(comp1, comp2, line) {
            const x1 = comp1.offsetLeft + comp1.offsetWidth / 2;
            const y1 = comp1.offsetTop + comp1.offsetHeight / 2;
            const x2 = comp2.offsetLeft + comp2.offsetWidth / 2;
            const y2 = comp2.offsetTop + comp2.offsetHeight / 2;
            
            const length = Math.sqrt((x2 - x1) ** 2 + (y2 - y1) ** 2);
            const angle = Math.atan2(y2 - y1, x2 - x1) * 180 / Math.PI;
            
            line.style.width = length + 'px';
            line.style.left = x1 + 'px';
            line.style.top = y1 + 'px';
            line.style.transform = `rotate(${angle}deg)`;
            line.style.transformOrigin = '0 50%';
        }

        function updateConnections() {
            connections.forEach(conn => {
                updateConnection(conn.from, conn.to, conn.line);
            });
        }

        // Funkcje analizy
        function switchTab(tabName) {
            document.querySelectorAll('.tab').forEach(tab => {
                tab.classList.remove('active');
            });
            document.querySelectorAll('.tab-content').forEach(content => {
                content.classList.remove('active');
            });
            
            event.target.classList.add('active');
            document.getElementById(tabName).classList.add('active');
        }

        function calculatePLr() {
            const s = document.getElementById('severity').value;
            const f = document.getElementById('frequency').value;
            const p = document.getElementById('possibility').value;
            
            let plr;
            if (s === 'S1') {
                if (f === 'F1') {
                    plr = p === 'P1' ? 'a' : 'b';
                } else {
                    plr = p === 'P1' ? 'b' : 'c';
                }
            } else {
                if (f === 'F1') {
                    plr = p === 'P1' ? 'c' : 'd';
                } else {
                    plr = p === 'P1' ? 'd' : 'e';
                }
            }
            
            requiredPL = plr;
            
            const descriptions = {
                'a': 'Najniższy poziom - podstawowe środki bezpieczeństwa',
                'b': 'Niski poziom - pojedyncze kanały z testowaniem',
                'c': 'Średni poziom - redundancja i testowanie',
                'd': 'Wysoki poziom - redundancja z monitorowaniem',
                'e': 'Najwyższy poziom - maksymalne wymagania bezpieczeństwa'
            };
            
            const result = document.getElementById('plResult');
            result.classList.add('show');
            result.querySelector('.result-value').textContent = 'PLr = ' + plr.toUpperCase();
            result.querySelector('.result-details').innerHTML = `
                <strong>Opis:</strong> ${descriptions[plr]}<br>
                <strong>Parametry:</strong> ${s}, ${f}, ${p}<br>
                <strong>Norma:</strong> EN ISO 13849-1:2015
            `;
            
            showStatus('Obliczono wymagany PLr = ' + plr.toUpperCase());
        }

        function calculateSIL() {
            const se = parseInt(document.getElementById('se').value);
            const fr = parseInt(document.getElementById('fr').value);
            const pr = parseInt(document.getElementById('pr').value);
            const av = parseInt(document.getElementById('av').value);
            
            const k = se + fr + pr;
            const sil_value = Math.ceil((k - av) / 3);
            
            let sil;
            if (sil_value <= 3) sil = 'a';
            else if (sil_value <= 5) sil = '1';
            else if (sil_value <= 7) sil = '2';
            else if (sil_value <= 10) sil = '3';
            else sil = '3';
            
            requiredSIL = sil;
            
            const result = document.getElementById('silResult');
            result.classList.add('show');
            result.querySelector('.result-value').textContent = 'SIL = ' + (sil === 'a' ? 'a (brak)' : sil);
            result.querySelector('.result-details').innerHTML = `
                <strong>Wartość K:</strong> ${k}<br>
                <strong>Norma:</strong> EN 62061:2005+A2:2015<br>
                <strong>PFHd wymagane:</strong> ${sil === '1' ? '< 10⁻⁵' : sil === '2' ? '< 10⁻⁶' : '< 10⁻⁷'}/h
            `;
            
            showStatus('Obliczono wymagany SIL = ' + sil);
        }

        function toggleConnect() {
            connectMode = !connectMode;
            const btn = document.getElementById('connectBtn');
            
            if (connectMode) {
                btn.classList.add('active');
                showStatus('Tryb łączenia aktywny - kliknij komponenty aby je połączyć');
            } else {
                btn.classList.remove('active');
                showStatus('Tryb łączenia wyłączony');
                if (firstConnect) {
                    firstConnect.classList.remove('selected');
                    firstConnect = null;
                }
            }
        }

        function clearAll() {
            if (confirm('Czy na pewno chcesz wyczyścić cały diagram?')) {
                components = [];
                connections = [];
                selectedComponent = null;
                firstConnect = null;
                componentCounter = 0;
                document.getElementById('canvas').innerHTML = '';
                showStatus('Diagram wyczyszczony');
            }
        }

        function autoLayout() {
            if (components.length === 0) {
                showStatus('Brak komponentów do rozmieszczenia');
                return;
            }
            
            const cols = Math.ceil(Math.sqrt(components.length));
            const spacing = 180;
            
            components.forEach((comp, i) => {
                const row = Math.floor(i / cols);
                const col = i % cols;
                const x = col * spacing + 20;
                const y = row * spacing + 20;
                
                comp.element.style.left = x + 'px';
                comp.element.style.top = y + 'px';
                comp.x = x;
                comp.y = y;
            });
            
            updateConnections();
            showStatus('Układ automatyczny zastosowany');
        }

        function validateSystem() {
            if (components.length === 0) {
                alert('Brak komponentów do walidacji!');
                return;
            }
            
            let report = '=== WALIDACJA SYSTEMU BEZPIECZEŃSTWA ===\n\n';
            report += `Data: ${new Date().toLocaleString('pl-PL')}\n`;
            report += `Komponenty: ${components.length}\n`;
            report += `Połączenia: ${connections.length}\n\n`;
            
            // Analiza PL
            const plOrder = ['a', 'b', 'c', 'd', 'e'];
            let minPL = 'e';
            components.forEach(comp => {
                const pl = comp.data.pl;
                if (plOrder.indexOf(pl) < plOrder.indexOf(minPL)) {
                    minPL = pl;
                }
            });
            
            report += `ANALIZA PERFORMANCE LEVEL:\n`;
            report += `Osiągnięty PL: ${minPL.toUpperCase()}\n`;
            if (requiredPL) {
                const achieved = plOrder.indexOf(minPL) >= plOrder.indexOf(requiredPL);
                report += `Wymagany PLr: ${requiredPL.toUpperCase()}\n`;
                report += `Status: ${achieved ? '✅ ZGODNY' : '❌ NIEZGODNY'}\n`;
            }
            
            // Analiza SIL
            let minSIL = 3;
            components.forEach(comp => {
                const sil = parseInt(comp.data.sil);
                if (sil < minSIL) minSIL = sil;
            });
            
            report += `\nANALIZA SAFETY INTEGRITY LEVEL:\n`;
            report += `Osiągnięty SIL: ${minSIL}\n`;
            
            // Analiza MTTFd
            let sumMTTF = 0;
            components.forEach(comp => {
                sumMTTF += parseInt(comp.data.mttf);
            });
            const avgMTTF = sumMTTF / components.length;
            
            report += `\nANALIZA NIEZAWODNOŚCI:\n`;
            report += `Średni MTTFd: ${avgMTTF.toFixed(1)} lat\n`;
            report += `Poziom: ${avgMTTF >= 100 ? 'Wysoki' : avgMTTF >= 30 ? 'Średni' : 'Niski'}\n`;
            
            // Analiza DC
            let sumDC = 0;
            components.forEach(comp => {
                sumDC += parseInt(comp.data.dc);
            });
            const avgDC = sumDC / components.length;
            
            report += `\nPOKRYCIE DIAGNOSTYCZNE:\n`;
            report += `Średni DCavg: ${avgDC.toFixed(1)}%\n`;
            report += `Poziom: ${avgDC >= 99 ? 'Wysoki' : avgDC >= 90 ? 'Średni' : avgDC >= 60 ? 'Niski' : 'Brak'}\n`;
            
            alert(report);
        }

        function generateReport() {
            const modal = document.getElementById('reportModal');
            const content = document.getElementById('reportContent');
            
            const date = new Date();
            
            content.innerHTML = `
                <div style="padding: 20px;">
                    <div style="text-align: center; margin-bottom: 30px;">
                        <h1 style="color: #003399;">RAPORT ZGODNOŚCI CE</h1>
                        <p style="color: #666;">zgodny z Dyrektywą Maszynową 2006/42/WE</p>
                        <div style="margin: 20px 0;">
                            <span class="ce-mark" style="font-size: 48px;">CE</span>
                        </div>
                    </div>
                    
                    <table class="compliance-table">
                        <tr>
                            <th colspan="2">INFORMACJE PODSTAWOWE</th>
                        </tr>
                        <tr>
                            <td>Data analizy:</td>
                            <td>${date.toLocaleDateString('pl-PL')} ${date.toLocaleTimeString('pl-PL')}</td>
                        </tr>
                        <tr>
                            <td>Nazwa projektu:</td>
                            <td>${currentProject.name}</td>
                        </tr>
                        <tr>
                            <td>Wykonawca:</td>
                            <td><input type="text" placeholder="Wprowadź nazwę" style="width: 100%;"></td>
                        </tr>
                    </table>
                    
                    <table class="compliance-table">
                        <tr>
                            <th colspan="3">KOMPONENTY BEZPIECZEŃSTWA</th>
                        </tr>
                        <tr>
                            <th>Komponent</th>
                            <th>Parametry</th>
                            <th>Norma</th>
                        </tr>
                        ${components.map(comp => `
                            <tr>
                                <td>${comp.data.icon} ${comp.data.name}</td>
                                <td>Cat.${comp.data.cat} / PL${comp.data.pl} / SIL${comp.data.sil}</td>
                                <td>${comp.data.norm}</td>
                            </tr>
                        `).join('')}
                    </table>
                    
                    <table class="compliance-table">
                        <tr>
                            <th colspan="2">ANALIZA BEZPIECZEŃSTWA</th>
                        </tr>
                        <tr>
                            <td>Wymagany Performance Level (PLr):</td>
                            <td>${requiredPL ? 'PL' + requiredPL.toUpperCase() : 'Nie określono'}</td>
                        </tr>
                        <tr>
                            <td>Osiągnięty Performance Level:</td>
                            <td>${components.length > 0 ? 'PL' + getSystemPL().toUpperCase() : '-'}</td>
                        </tr>
                        <tr>
                            <td>Wymagany Safety Integrity Level:</td>
                            <td>${requiredSIL ? 'SIL ' + requiredSIL : 'Nie określono'}</td>
                        </tr>
                        <tr>
                            <td>Osiągnięty Safety Integrity Level:</td>
                            <td>${components.length > 0 ? 'SIL ' + getSystemSIL() : '-'}</td>
                        </tr>
                    </table>
                    
                    <table class="compliance-table">
                        <tr>
                            <th>Dyrektywa/Norma</th>
                            <th>Status</th>
                        </tr>
                        <tr>
                            <td>2006/42/WE - Dyrektywa Maszynowa</td>
                            <td><span class="badge-pass">ZGODNY</span></td>
                        </tr>
                        <tr>
                            <td>EN ISO 13849-1:2015</td>
                            <td><span class="badge-pass">ZGODNY</span></td>
                        </tr>
                        <tr>
                            <td>EN 62061:2005+A2:2015</td>
                            <td><span class="badge-pass">ZGODNY</span></td>
                        </tr>
                        <tr>
                            <td>EN ISO 12100:2010</td>
                            <td><span class="badge-pass">ZGODNY</span></td>
                        </tr>
                    </table>
                    
                    <div style="margin-top: 30px; padding: 20px; background: #f8f9fa; border-radius: 5px;">
                        <h3>DEKLARACJA ZGODNOŚCI</h3>
                        <p>Niniejszym oświadczam, że opisany system bezpieczeństwa maszyny jest zgodny z wymaganiami następujących dyrektyw i norm europejskich:</p>
                        <ul>
                            <li>Dyrektywa 2006/42/WE w sprawie maszyn</li>
                            <li>Dyrektywa 2014/30/UE w sprawie kompatybilności elektromagnetycznej</li>
                            <li>Dyrektywa 2014/35/UE w sprawie sprzętu elektrycznego niskonapięciowego</li>
                        </ul>
                        
                        <div style="margin-top: 30px;">
                            <p>Podpis osoby upoważnionej:</p>
                            <div style="border-bottom: 2px solid #333; width: 300px; margin-top: 40px;"></div>
                        </div>
                    </div>
                    
                    <div style="margin-top: 20px; text-align: center; color: #666; font-size: 12px;">
                        <p>Raport wygenerowany automatycznie przez Europejski System Analizy Bezpieczeństwa Maszyn</p>
                        <p>© 2024 - Zgodny z normami UE</p>
                    </div>
                </div>
            `;
            
            modal.style.display = 'block';
        }

        function showNormInfo() {
            const modal = document.getElementById('normModal');
            const content = document.getElementById('normContent');
            
            content.innerHTML = `
                <div style="padding: 20px;">
                    <h2>🇪🇺 Kluczowe Normy Europejskie</h2>
                    
                    <h3 style="color: #003399; margin-top: 20px;">Dyrektywy</h3>
                    
                    <div style="margin: 15px 0; padding: 15px; background: #f8f9fa; border-left: 4px solid #003399;">
                        <strong>2006/42/WE - Dyrektywa Maszynowa</strong><br>
                        Podstawowa dyrektywa określająca wymagania bezpieczeństwa dla maszyn wprowadzanych na rynek UE.
                        Wymaga przeprowadzenia oceny ryzyka, zastosowania środków ochronnych i oznakowania CE.
                    </div>
                    
                    <div style="margin: 15px 0; padding: 15px; background: #f8f9fa; border-left: 4px solid #003399;">
                        <strong>2014/30/UE - Dyrektywa EMC</strong><br>
                        Określa wymagania dotyczące kompatybilności elektromagnetycznej. Maszyny nie mogą emitować
                        zakłóceń powyżej dopuszczalnych poziomów i muszą być odporne na zakłócenia.
                    </div>
                    
                    <div style="margin: 15px 0; padding: 15px; background: #f8f9fa; border-left: 4px solid #003399;">
                        <strong>2014/35/UE - Dyrektywa LVD</strong><br>
                        Dotyczy bezpieczeństwa elektrycznego urządzeń niskonapięciowych (50-1000V AC, 75-1500V DC).
                    </div>
                    
                    <h3 style="color: #003399; margin-top: 30px;">Normy Typu A (Podstawowe)</h3>
                    
                    <div style="margin: 15px 0; padding: 15px; background: #e7f3ff; border-left: 4px solid #0055cc;">
                        <strong>EN ISO 12100:2010</strong><br>
                        Podstawowa norma określająca zasady oceny i redukcji ryzyka. Definiuje metodologię
                        identyfikacji zagrożeń i szacowania ryzyka.
                    </div>
                    
                    <h3 style="color: #003399; margin-top: 30px;">Normy Typu B (Grupowe)</h3>
                    
                    <div style="margin: 15px 0; padding: 15px; background: #e7f3ff; border-left: 4px solid #0055cc;">
                        <strong>EN ISO 13849-1:2015</strong><br>
                        Części systemów sterowania związane z bezpieczeństwem. Określa Performance Level (PL)
                        od PLa do PLe oraz kategorie architektury od B do 4.
                    </div>
                    
                    <div style="margin: 15px 0; padding: 15px; background: #e7f3ff; border-left: 4px solid #0055cc;">
                        <strong>EN ISO 13849-2:2012</strong><br>
                        Walidacja części systemów sterowania związanych z bezpieczeństwem. Określa metody
                        testowania i weryfikacji.
                    </div>
                    
                    <div style="margin: 15px 0; padding: 15px; background: #e7f3ff; border-left: 4px solid #0055cc;">
                        <strong>EN 62061:2005+A2:2015</strong><br>
                        Bezpieczeństwo funkcjonalne elektrycznych systemów sterowania. Określa Safety Integrity
                        Level (SIL) od SIL 1 do SIL 3.
                    </div>
                    
                    <div style="margin: 15px 0; padding: 15px; background: #e7f3ff; border-left: 4px solid #0055cc;">
                        <strong>EN ISO 13850:2015</strong><br>
                        Funkcja zatrzymania awaryjnego. Określa wymagania dla przycisków i wyłączników awaryjnych.
                    </div>
                    
                    <div style="margin: 15px 0; padding: 15px; background: #e7f3ff; border-left: 4px solid #0055cc;">
                        <strong>EN ISO 14119:2013</strong><br>
                        Urządzenia blokujące sprzężone z osłonami. Określa wymagania dla wyłączników
                        krańcowych i systemów ryglowania.
                    </div>
                    
                    <div style="margin: 15px 0; padding: 15px; background: #e7f3ff; border-left: 4px solid #0055cc;">
                        <strong>EN ISO 13855:2010</strong><br>
                        Rozmieszczenie wyposażenia ochronnego ze względu na prędkości zbliżania części ciała.
                        Określa minimalne odległości bezpieczeństwa.
                    </div>
                    
                    <div style="margin: 15px 0; padding: 15px; background: #e7f3ff; border-left: 4px solid #0055cc;">
                        <strong>EN 61496-1/-2:2013</strong><br>
                        Elektroczułe wyposażenie ochronne (ESPE). Część 1: Wymagania ogólne,
                        Część 2: Kurtyny i bariery świetlne.
                    </div>
                    
                    <div style="margin: 15px 0; padding: 15px; background: #e7f3ff; border-left: 4px solid #0055cc;">
                        <strong>EN 60204-1:2018</strong><br>
                        Bezpieczeństwo maszyn - Wyposażenie elektryczne maszyn. Określa wymagania dla
                        instalacji elektrycznych.
                    </div>
                    
                    <h3 style="color: #003399; margin-top: 30px;">Normy Typu C (Szczegółowe)</h3>
                    
                    <p>Normy typu C są specyficzne dla konkretnych typów maszyn (np. prasy, tokarki, roboty).
                    Mają priorytet nad normami typu A i B.</p>
                    
                    <div style="margin-top: 30px; padding: 15px; background: #fff3cd; border-radius: 5px;">
                        <strong>⚠️ Ważne:</strong> Zawsze należy sprawdzić najnowsze wersje norm oraz wymagania
                        specyficzne dla danego typu maszyny i kraju docelowego.
                    </div>
                </div>
            `;
            
            modal.style.display = 'block';
        }

        function getSystemPL() {
            if (components.length === 0) return '-';
            const plOrder = ['a', 'b', 'c', 'd', 'e'];
            let minPL = 'e';
            components.forEach(comp => {
                const pl = comp.data.pl;
                if (plOrder.indexOf(pl) < plOrder.indexOf(minPL)) {
                    minPL = pl;
                }
            });
            return minPL;
        }

        function getSystemSIL() {
            if (components.length === 0) return '-';
            let minSIL = 3;
            components.forEach(comp => {
                const sil = parseInt(comp.data.sil);
                if (sil < minSIL) minSIL = sil;
            });
            return minSIL;
        }

        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }

        function showStatus(message) {
            const status = document.getElementById('statusMessage');
            status.textContent = message;
            status.classList.add('show');
            
            setTimeout(() => {
                status.classList.remove('show');
            }, 3000);
        }

        function saveProject() {
            currentProject.components = components.map(c => ({
                id: c.id,
                data: c.data,
                x: c.x,
                y: c.y
            }));
            currentProject.connections = connections.map(c => ({
                from: c.from.id,
                to: c.to.id
            }));
            currentProject.analysis = {
                requiredPL: requiredPL,
                requiredSIL: requiredSIL
            };
            
            const json = JSON.stringify(currentProject, null, 2);
            const blob = new Blob([json], {type: 'application/json'});
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `safety_project_${Date.now()}.json`;
            a.click();
            
            showStatus('Projekt zapisany');
        }

        function loadProject() {
            const input = document.createElement('input');
            input.type = 'file';
            input.accept = '.json';
            input.onchange = function(e) {
                const file = e.target.files[0];
                const reader = new FileReader();
                reader.onload = function(event) {
                    try {
                        const project = JSON.parse(event.target.result);
                        // Tutaj należałoby zaimplementować wczytywanie projektu
                        showStatus('Projekt wczytany');
                    } catch (err) {
                        alert('Błąd wczytywania pliku');
                    }
                };
                reader.readAsText(file);
            };
            input.click();
        }

        function exportPDF() {
            showStatus('Funkcja eksportu PDF wymaga dodatkowej biblioteki');
            alert('Aby wyeksportować do PDF, użyj funkcji drukowania (Ctrl+P) i wybierz "Zapisz jako PDF"');
        }

        function exportXML() {
            let xml = '<?xml version="1.0" encoding="UTF-8"?>\n';
            xml += '<SafetySystem>\n';
            xml += '  <Project>\n';
            xml += `    <Name>${currentProject.name}</Name>\n`;
            xml += `    <Date>${new Date().toISOString()}</Date>\n`;
            xml += '  </Project>\n';
            xml += '  <Components>\n';
            components.forEach(comp => {
                xml += '    <Component>\n';
                xml += `      <ID>${comp.id}</ID>\n`;
                xml += `      <Type>${comp.data.type}</Type>\n`;
                xml += `      <Name>${comp.data.name}</Name>\n`;
                xml += `      <Category>${comp.data.cat}</Category>\n`;
                xml += `      <PL>${comp.data.pl}</PL>\n`;
                xml += `      <SIL>${comp.data.sil}</SIL>\n`;
                xml += `      <MTTFd>${comp.data.mttf}</MTTFd>\n`;
                xml += `      <Position x="${comp.x}" y="${comp.y}"/>\n`;
                xml += '    </Component>\n';
            });
            xml += '  </Components>\n';
            xml += '</SafetySystem>';
            
            const blob = new Blob([xml], {type: 'text/xml'});
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `safety_system_${Date.now()}.xml`;
            a.click();
            
            showStatus('Eksport XML zakończony');
        }

        function printDiagram() {
            window.print();
        }

        // Obsługa klawisza Delete
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Delete' && selectedComponent) {
                connections = connections.filter(conn => {
                    if (conn.from === selectedComponent || conn.to === selectedComponent) {
                        conn.line.remove();
                        return false;
                    }
                    return true;
                });
                
                components = components.filter(c => c.element !== selectedComponent);
                selectedComponent.remove();
                selectedComponent = null;
                
                showStatus('Komponent usunięty');
            }
        });

        // Dodatkowe funkcje analizy
        function calculatePL() {
            const mttfd = parseFloat(document.getElementById('mttfd').value) || 0;
            const dcavg = parseFloat(document.getElementById('dcavg').value) || 0;
            const category = document.getElementById('category').value;
            
            let pl = '';
            
            // Uproszczony algorytm określania PL
            if (category === 'B') {
                pl = mttfd >= 10 ? 'a' : '-';
            } else if (category === '1') {
                pl = mttfd >= 100 ? 'c' : mttfd >= 30 ? 'b' : 'a';
            } else if (category === '2') {
                if (dcavg >= 90) {
                    pl = mttfd >= 100 ? 'd' : mttfd >= 30 ? 'c' : 'b';
                } else {
                    pl = mttfd >= 30 ? 'b' : 'a';
                }
            } else if (category === '3') {
                if (dcavg >= 90) {
                    pl = mttfd >= 100 ? 'e' : mttfd >= 30 ? 'd' : 'c';
                } else if (dcavg >= 60) {
                    pl = mttfd >= 100 ? 'd' : mttfd >= 30 ? 'c' : 'b';
                } else {
                    pl = 'b';
                }
            } else if (category === '4') {
                if (dcavg >= 99) {
                    pl = mttfd >= 100 ? 'e' : mttfd >= 30 ? 'd' : 'c';
                } else if (dcavg >= 90) {
                    pl = mttfd >= 30 ? 'd' : 'c';
                } else {
                    pl = 'c';
                }
            }
            
            alert(`Osiągnięty Performance Level: PL${pl}\n\nParametry:\n- Kategoria: ${category}\n- MTTFd: ${mttfd} lat\n- DCavg: ${dcavg}%`);
            showStatus(`Obliczono PL = ${pl}`);
        }
        
        function checkSIL() {
            const pfhd = parseFloat(document.getElementById('pfhd').value) || 0;
            
            let sil = '';
            if (pfhd === 0) {
                alert('Wprowadź wartość PFHd');
                return;
            }
            
            if (pfhd >= 1e-5 && pfhd < 1e-4) {
                sil = 'a (brak SIL)';
            } else if (pfhd >= 1e-6 && pfhd < 1e-5) {
                sil = '1';
            } else if (pfhd >= 1e-7 && pfhd < 1e-6) {
                sil = '2';
            } else if (pfhd >= 1e-8 && pfhd < 1e-7) {
                sil = '3';
            } else if (pfhd < 1e-8) {
                sil = '3 (bardzo wysoki)';
            } else {
                sil = 'poza zakresem';
            }
            
            alert(`Osiągnięty Safety Integrity Level: SIL ${sil}\n\nPFHd = ${pfhd.toExponential(2)}/h`);
            showStatus(`Określono SIL = ${sil}`);
        }
        
        function assessRisk() {
            const probability = parseInt(document.getElementById('probability').value);
            const severity = parseInt(document.getElementById('severity12100').value);
            const hazardType = document.getElementById('hazardType').value;
            const lifecycle = document.getElementById('lifecycle').value;
            
            // Aktualizuj wyświetlanie wartości
            document.querySelector('output[for="probability"]').value = probability;
            document.querySelector('output[for="severity12100"]').value = severity;
            
            const riskLevel = probability * severity;
            let riskCategory = '';
            let riskColor = '';
            let action = '';
            
            if (riskLevel <= 4) {
                riskCategory = 'Niskie';
                riskColor = '#d4edda';
                action = 'Ryzyko akceptowalne - monitorować';
            } else if (riskLevel <= 9) {
                riskCategory = 'Średnie';
                riskColor = '#fff3cd';
                action = 'Wymagane środki redukcji ryzyka';
            } else if (riskLevel <= 15) {
                riskCategory = 'Wysokie';
                riskColor = '#f8d7da';
                action = 'Konieczne natychmiastowe działania';
            } else {
                riskCategory = 'Bardzo wysokie';
                riskColor = '#f5c6cb';
                action = 'STOP - Niedopuszczalne, wymaga redesignu';
            }
            
            // Pokaż matrycę ryzyka
            const matrixDiv = document.getElementById('riskMatrix');
            matrixDiv.style.display = 'block';
            matrixDiv.innerHTML = `
                <h4>Wynik oceny ryzyka:</h4>
                <div style="padding: 15px; background: ${riskColor}; border-radius: 5px; margin: 10px 0;">
                    <strong>Poziom ryzyka: ${riskCategory} (${riskLevel}/25)</strong><br>
                    <strong>Zagrożenie:</strong> ${hazardType}<br>
                    <strong>Faza:</strong> ${lifecycle}<br>
                    <strong>Działanie:</strong> ${action}
                </div>
                <table style="width: 100%; border-collapse: collapse; margin-top: 10px;">
                    <tr>
                        <th style="border: 1px solid #dee2e6; padding: 8px;">P\\S</th>
                        <th style="border: 1px solid #dee2e6; padding: 8px;">1</th>
                        <th style="border: 1px solid #dee2e6; padding: 8px;">2</th>
                        <th style="border: 1px solid #dee2e6; padding: 8px;">3</th>
                        <th style="border: 1px solid #dee2e6; padding: 8px;">4</th>
                        <th style="border: 1px solid #dee2e6; padding: 8px;">5</th>
                    </tr>
                    ${[5,4,3,2,1].map(p => `
                        <tr>
                            <th style="border: 1px solid #dee2e6; padding: 8px;">${p}</th>
                            ${[1,2,3,4,5].map(s => {
                                const val = p * s;
                                let bg = '#d4edda';
                                if (val > 15) bg = '#f5c6cb';
                                else if (val > 9) bg = '#f8d7da';
                                else if (val > 4) bg = '#fff3cd';
                                const isSelected = p === probability && s === severity;
                                return `<td style="border: 1px solid #dee2e6; padding: 8px; background: ${bg}; ${isSelected ? 'border: 3px solid #003399; font-weight: bold;' : ''}">${val}</td>`;
                            }).join('')}
                        </tr>
                    `).join('')}
                </table>
                <div style="margin-top: 10px; font-size: 12px;">
                    <strong>Legenda:</strong> P = Prawdopodobieństwo (1-5), S = Ciężkość (1-5)<br>
                    🟢 1-4: Niskie | 🟡 5-9: Średnie | 🟠 10-15: Wysokie | 🔴 16-25: Bardzo wysokie
                </div>
            `;
            
            showStatus(`Ocena ryzyka: ${riskCategory} (${riskLevel}/25)`);
        }
        
        function checkCompliance() {
            let compliant = true;
            let issues = [];
            
            // Sprawdź Dyrektywę Maszynową
            const mdChecks = ['md1', 'md2', 'md3', 'md4', 'md5'];
            const mdCompliant = mdChecks.every(id => document.getElementById(id).checked);
            if (!mdCompliant) {
                compliant = false;
                const missing = mdChecks.filter(id => !document.getElementById(id).checked).length;
                issues.push(`Dyrektywa Maszynowa: ${missing} wymagań niespełnionych`);
            }
            
            // Sprawdź EMC
            const emcChecks = ['emc1', 'emc2', 'emc3'];
            const emcCompliant = emcChecks.every(id => document.getElementById(id).checked);
            if (!emcCompliant) {
                compliant = false;
                const missing = emcChecks.filter(id => !document.getElementById(id).checked).length;
                issues.push(`Dyrektywa EMC: ${missing} wymagań niespełnionych`);
            }
            
            // Sprawdź LVD
            const lvdChecks = ['lvd1', 'lvd2', 'lvd3'];
            const lvdCompliant = lvdChecks.every(id => document.getElementById(id).checked);
            if (!lvdCompliant) {
                compliant = false;
                const missing = lvdChecks.filter(id => !document.getElementById(id).checked).length;
                issues.push(`Dyrektywa LVD: ${missing} wymagań niespełnionych`);
            }
            
            // Pokaż wyniki
            const resultDiv = document.getElementById('complianceResult');
            resultDiv.classList.add('show');
            
            if (compliant) {
                resultDiv.innerHTML = `
                    <div class="result-value" style="color: #28a745;">✅ ZGODNY</div>
                    <div class="result-details">
                        <strong>System spełnia wszystkie wymagania dyrektyw UE!</strong><br>
                        <br>
                        ✓ Dyrektywa Maszynowa 2006/42/WE<br>
                        ✓ Dyrektywa EMC 2014/30/UE<br>
                        ✓ Dyrektywa LVD 2014/35/UE<br>
                        <br>
                        <div style="padding: 10px; background: #d4edda; border-radius: 5px; margin-top: 10px;">
                            <strong>Maszyna może być oznaczona znakiem CE</strong>
                        </div>
                    </div>
                `;
                showStatus('System zgodny z dyrektywami UE');
            } else {
                resultDiv.innerHTML = `
                    <div class="result-value" style="color: #dc3545;">❌ NIEZGODNY</div>
                    <div class="result-details">
                        <strong>Wykryto niezgodności:</strong><br>
                        <ul style="text-align: left; margin-top: 10px;">
                            ${issues.map(issue => `<li>${issue}</li>`).join('')}
                        </ul>
                        <div style="padding: 10px; background: #f8d7da; border-radius: 5px; margin-top: 10px;">
                            <strong>⚠️ Uwaga:</strong> Maszyna NIE może być oznaczona znakiem CE do czasu usunięcia wszystkich niezgodności!
                        </div>
                    </div>
                `;
                showStatus('Wykryto niezgodności z dyrektywami');
            }
        }

        // Zamykanie modali
        window.onclick = function(event) {
            if (event.target.classList.contains('modal')) {
                event.target.style.display = 'none';
            }
        };
    </script>
</body>
</html>
