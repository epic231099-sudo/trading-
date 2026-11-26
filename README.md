# trading-<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>TradePulse | Trading profesional</title>
  <!-- Font Awesome para iconos -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,500;14..32,600;14..32,700&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Inter', sans-serif;
      background-color: #0b0e14;
      color: #e9edf5;
      line-height: 1.5;
    }

    /* Layout principal */
    .app {
      display: flex;
      min-height: 100vh;
    }

    /* Sidebar */
    .sidebar {
      width: 260px;
      background-color: #131823;
      border-right: 1px solid #1f2a3a;
      display: flex;
      flex-direction: column;
      padding: 24px 0;
      transition: all 0.2s;
    }

    .logo-area {
      padding: 0 24px 32px 24px;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .logo-icon {
      background: linear-gradient(135deg, #3b82f6, #8b5cf6);
      width: 34px;
      height: 34px;
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: 700;
      font-size: 18px;
      color: white;
    }

    .logo-text {
      font-weight: 700;
      font-size: 20px;
      letter-spacing: -0.5px;
      background: linear-gradient(to right, #f0f4ff, #cbd5e1);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .nav {
      display: flex;
      flex-direction: column;
      gap: 6px;
      padding: 0 16px;
    }

    .nav-item {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 12px 16px;
      border-radius: 12px;
      color: #8f9db2;
      font-weight: 500;
      font-size: 15px;
      transition: all 0.15s;
      cursor: pointer;
    }

    .nav-item i {
      width: 20px;
      font-size: 1.1rem;
    }

    .nav-item.active {
      background-color: #1e2a3a;
      color: #ffffff;
      box-shadow: inset 3px 0 0 #3b82f6;
    }

    .nav-item:hover:not(.active) {
      background-color: #1a2230;
      color: #d1d9e6;
    }

    .sidebar-footer {
      margin-top: auto;
      padding: 24px 16px 0;
      border-top: 1px solid #1f2a3a;
    }

    .user-profile {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 8px 12px;
      border-radius: 12px;
      background-color: #1a2230;
    }

    .avatar {
      width: 40px;
      height: 40px;
      background: linear-gradient(135deg, #f59e0b, #ef4444);
      border-radius: 12px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: 600;
      color: white;
    }

    .user-info h4 {
      font-size: 14px;
      font-weight: 600;
    }

    .user-info p {
      font-size: 12px;
      color: #8f9db2;
    }

    /* Contenido principal */
    .main {
      flex: 1;
      display: flex;
      flex-direction: column;
      overflow: hidden;
    }

    /* Header superior */
    .topbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 18px 32px;
      background-color: #0f141f;
      border-bottom: 1px solid #1f2a3a;
    }

    .search-bar {
      display: flex;
      align-items: center;
      background-color: #1a2230;
      border-radius: 40px;
      padding: 8px 18px;
      width: 320px;
      gap: 10px;
      border: 1px solid #2a3548;
    }

    .search-bar i {
      color: #6b7b92;
      font-size: 14px;
    }

    .search-bar input {
      background: transparent;
      border: none;
      outline: none;
      color: #e9edf5;
      font-size: 14px;
      width: 100%;
      font-family: 'Inter', sans-serif;
    }

    .search-bar input::placeholder {
      color: #5d6f88;
    }

    .header-actions {
      display: flex;
      align-items: center;
      gap: 20px;
    }

    .balance-badge {
      display: flex;
      align-items: center;
      gap: 8px;
      background: #1a2230;
      padding: 6px 16px 6px 12px;
      border-radius: 40px;
      font-size: 14px;
      font-weight: 500;
      border: 1px solid #2a3548;
    }

    .balance-badge i {
      color: #3b82f6;
    }

    .balance-amount {
      color: #22c55e;
      font-weight: 600;
    }

    .icon-btn {
      background-color: #1a2230;
      border: 1px solid #2a3548;
      border-radius: 50%;
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #b0c0d8;
      cursor: pointer;
      transition: 0.15s;
    }

    .icon-btn:hover {
      background-color: #232f42;
      color: white;
    }

    /* Dashboard grid */
    .dashboard {
      padding: 28px 32px 32px;
      display: flex;
      flex-direction: column;
      gap: 28px;
      overflow-y: auto;
      flex: 1;
    }

    /* Resumen de mercado */
    .market-summary {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 18px;
    }

    .card {
      background-color: #131b27;
      border: 1px solid #1f2a3a;
      border-radius: 18px;
      padding: 18px 20px;
      transition: 0.15s;
    }

    .card:hover {
      border-color: #2d3f57;
      background-color: #16202e;
    }

    .card-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 12px;
      color: #9aabbf;
      font-size: 13px;
      font-weight: 500;
    }

    .card-header i {
      font-size: 16px;
    }

    .card-value {
      font-size: 24px;
      font-weight: 700;
      letter-spacing: -0.5px;
      margin-bottom: 6px;
    }

    .card-change {
      font-size: 13px;
      font-weight: 500;
      display: flex;
      align-items: center;
      gap: 4px;
    }

    .positive {
      color: #22c55e;
    }

    .negative {
      color: #ef4444;
    }

    /* Sección principal: gráfico + watchlist */
    .trading-section {
      display: grid;
      grid-template-columns: 1fr 340px;
      gap: 24px;
      min-height: 420px;
    }

    .chart-container {
      background-color: #131b27;
      border: 1px solid #1f2a3a;
      border-radius: 20px;
      padding: 20px 20px 12px 20px;
      display: flex;
      flex-direction: column;
    }

    .chart-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 18px;
    }

    .pair-selector {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .pair-name {
      font-size: 20px;
      font-weight: 700;
      letter-spacing: -0.3px;
    }

    .pair-badge {
      background-color: #1e2b3c;
      padding: 4px 10px;
      border-radius: 40px;
      font-size: 12px;
      font-weight: 600;
      color: #a0b3cc;
    }

    .timeframe {
      display: flex;
      gap: 6px;
      background-color: #0f141f;
      padding: 4px;
      border-radius: 40px;
    }

    .tf-btn {
      background: transparent;
      border: none;
      color: #8f9db2;
      font-size: 12px;
      font-weight: 600;
      padding: 5px 12px;
      border-radius: 30px;
      cursor: pointer;
      transition: 0.15s;
      font-family: 'Inter', sans-serif;
    }

    .tf-btn.active {
      background-color: #2a3548;
      color: white;
    }

    .tf-btn:hover:not(.active) {
      color: #cbd5e1;
    }

    /* Gráfico simulado con SVG */
    .chart-canvas {
      flex: 1;
      position: relative;
      margin-bottom: 12px;
    }

    .chart-canvas svg {
      width: 100%;
      height: 100%;
      display: block;
    }

    .chart-footer {
      display: flex;
      justify-content: space-between;
      color: #6b7b92;
      font-size: 12px;
      padding: 8px 0 4px;
      border-top: 1px solid #1f2a3a;
    }

    /* Watchlist */
    .watchlist {
      background-color: #131b27;
      border: 1px solid #1f2a3a;
      border-radius: 20px;
      padding: 20px 0 8px 0;
      display: flex;
      flex-direction: column;
      overflow: hidden;
    }

    .watchlist-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0 18px 12px 18px;
    }

    .watchlist-header h3 {
      font-size: 16px;
      font-weight: 600;
      letter-spacing: -0.2px;
    }

    .watchlist-header a {
      font-size: 12px;
      color: #3b82f6;
      text-decoration: none;
      font-weight: 500;
    }

    .asset-list {
      display: flex;
      flex-direction: column;
      overflow-y: auto;
      max-height: 380px;
    }

    .asset-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 14px 18px;
      border-bottom: 1px solid #1a2230;
      transition: background 0.15s;
      cursor: pointer;
    }

    .asset-item:hover {
      background-color: #1a2230;
    }

    .asset-info {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .asset-icon {
      width: 36px;
      height: 36px;
      border-radius: 10px;
      background: #1e2b3c;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: 700;
      font-size: 14px;
    }

    .btc .asset-icon { background: #f7931a20; color: #f7931a; }
    .eth .asset-icon { background: #627eea20; color: #627eea; }
    .sol .asset-icon { background: #14f19520; color: #14f195; }
    .ada .asset-icon { background: #0d1e7a20; color: #3b82f6; }
    .dot .asset-icon { background: #e6007a20; color: #e6007a; }

    .asset-name {
      font-weight: 600;
      font-size: 14px;
    }

    .asset-symbol {
      font-size: 12px;
      color: #6b7b92;
    }

    .asset-price {
      text-align: right;
    }

    .price-value {
      font-weight: 600;
      font-size: 14px;
    }

    .price-change {
      font-size: 12px;
      font-weight: 500;
    }

    /* Órdenes y actividad */
    .orders-section {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 24px;
    }

    .orders-card {
      background-color: #131b27;
      border: 1px solid #1f2a3a;
      border-radius: 20px;
      padding: 18px 0 8px 0;
    }

    .orders-header {
      display: flex;
      justify-content: space-between;
      padding: 0 18px 12px 18px;
      font-weight: 600;
      font-size: 15px;
    }

    .order-row {
      display: flex;
      justify-content: space-between;
      padding: 12px 18px;
      border-bottom: 1px solid #1a2230;
      font-size: 13px;
    }

    .order-row span:first-child {
      color: #8f9db2;
    }

    .order-row span:last-child {
      font-weight: 500;
    }

    .badge-buy {
      background-color: #22c55e20;
      color: #22c55e;
      padding: 2px 10px;
      border-radius: 40px;
      font-size: 12px;
      font-weight: 600;
    }

    .badge-sell {
      background-color: #ef444420;
      color: #ef4444;
      padding: 2px 10px;
      border-radius: 40px;
      font-size: 12px;
      font-weight: 600;
    }

    /* Botones de trading */
    .trade-actions {
      display: flex;
      gap: 14px;
      margin-top: 6px;
    }

    .btn-buy, .btn-sell {
      flex: 1;
      padding: 12px 20px;
      border-radius: 14px;
      border: none;
      font-weight: 600;
      font-size: 15px;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      cursor: pointer;
      transition: 0.15s;
      font-family: 'Inter', sans-serif;
    }

    .btn-buy {
      background-color: #22c55e;
      color: #0b0e14;
    }

    .btn-buy:hover {
      background-color: #16a34a;
    }

    .btn-sell {
      background-color: #ef4444;
      color: white;
    }

    .btn-sell:hover {
      background-color: #dc2626;
    }

    /* Scroll personalizado */
    ::-webkit-scrollbar {
      width: 6px;
    }

    ::-webkit-scrollbar-track {
      background: #0f141f;
    }

    ::-webkit-scrollbar-thumb {
      background: #2a3548;
      border-radius: 10px;
    }

    /* Responsive */
    @media (max-width: 1200px) {
      .market-summary {
        grid-template-columns: repeat(2, 1fr);
      }
      .trading-section {
        grid-template-columns: 1fr;
      }
    }

    @media (max-width: 768px) {
      .sidebar {
        display: none;
      }
      .topbar {
        padding: 16px 20px;
      }
      .dashboard {
        padding: 20px;
      }
      .market-summary {
        grid-template-columns: 1fr;
      }
      .orders-section {
        grid-template-columns: 1fr;
      }
      .search-bar {
        width: 180px;
      }
    }
  </style>
</head>
<body>
  <div class="app">
    <!-- Sidebar -->
    <aside class="sidebar">
      <div class="logo-area">
        <div class="logo-icon">T</div>
        <span class="logo-text">TradePulse</span>
      </div>
      <nav class="nav">
        <div class="nav-item active"><i class="fas fa-chart-pie"></i> Dashboard</div>
        <div class="nav-item"><i class="fas fa-chart-line"></i> Mercados</div>
        <div class="nav-item"><i class="fas fa-exchange-alt"></i> Operar</div>
        <div class="nav-item"><i class="fas fa-wallet"></i> Cartera</div>
        <div class="nav-item"><i class="fas fa-history"></i> Historial</div>
        <div class="nav-item"><i class="fas fa-cog"></i> Configuración</div>
      </nav>
      <div class="sidebar-footer">
        <div class="user-profile">
          <div class="avatar">LM</div>
          <div class="user-info">
            <h4>Luis Mendoza</h4>
            <p>Cuenta Pro</p>
          </div>
        </div>
      </div>
    </aside>

    <!-- Main -->
    <main class="main">
      <!-- Topbar -->
      <header class="topbar">
        <div class="search-bar">
          <i class="fas fa-search"></i>
          <input type="text" placeholder="Buscar activos, pares...">
        </div>
        <div class="header-actions">
          <div class="balance-badge">
            <i class="fas fa-coins"></i>
            <span class="balance-amount">$28,460.32</span>
          </div>
          <button class="icon-btn"><i class="fas fa-bell"></i></button>
          <button class="icon-btn"><i class="fas fa-user"></i></button>
        </div>
      </header>

      <!-- Dashboard content -->
      <div class="dashboard">
        <!-- Market summary -->
        <div class="market-summary">
          <div class="card">
            <div class="card-header">
              <span>Balance total</span>
              <i class="fas fa-wallet" style="color:#3b82f6;"></i>
            </div>
            <div class="card-value">$28,460.32</div>
            <div class="card-change positive"><i class="fas fa-arrow-up"></i> +2.4% hoy</div>
          </div>
          <div class="card">
            <div class="card-header">
              <span>P&L no realizado</span>
              <i class="fas fa-chart-line" style="color:#8b5cf6;"></i>
            </div>
            <div class="card-value">$1,283.45</div>
            <div class="card-change positive"><i class="fas fa-arrow-up"></i> +8.2%</div>
          </div>
          <div class="card">
            <div class="card-header">
              <span>Volumen 24h</span>
              <i class="fas fa-chart-bar" style="color:#f59e0b;"></i>
            </div>
            <div class="card-value">$4.2M</div>
            <div class="card-change positive"><i class="fas fa-arrow-up"></i> +12.5%</div>
          </div>
          <div class="card">
            <div class="card-header">
              <span>Órdenes abiertas</span>
              <i class="fas fa-clock" style="color:#22c55e;"></i>
            </div>
            <div class="card-value">3</div>
            <div class="card-change" style="color:#8f9db2;">2 compra · 1 venta</div>
          </div>
        </div>

        <!-- Trading chart + watchlist -->
        <div class="trading-section">
          <div class="chart-container">
            <div class="chart-header">
              <div class="pair-selector">
                <span class="pair-name">BTC/USDT</span>
                <span class="pair-badge">Perpetuo</span>
              </div>
              <div class="timeframe">
                <button class="tf-btn">1H</button>
                <button class="tf-btn active">4H</button>
                <button class="tf-btn">1D</button>
                <button class="tf-btn">1W</button>
              </div>
            </div>
            <!-- Gráfico simulado SVG -->
            <div class="chart-canvas">
              <svg viewBox="0 0 600 220" preserveAspectRatio="none" style="width:100%; height:100%;">
                <!-- Cuadrícula -->
                <line x1="0" y1="40" x2="600" y2="40" stroke="#1f2a3a" stroke-width="1" stroke-dasharray="4 4" />
                <line x1="0" y1="80" x2="600" y2="80" stroke="#1f2a3a" stroke-width="1" stroke-dasharray="4 4" />
                <line x1="0" y1="120" x2="600" y2="120" stroke="#1f2a3a" stroke-width="1" stroke-dasharray="4 4" />
                <line x1="0" y1="160" x2="600" y2="160" stroke="#1f2a3a" stroke-width="1" stroke-dasharray="4 4" />
                <line x1="0" y1="200" x2="600" y2="200" stroke="#1f2a3a" stroke-width="1" stroke-dasharray="4 4" />
                <!-- Área de fondo -->
                <defs>
                  <linearGradient id="gradientArea" x1="0%" y1="0%" x2="0%" y2="100%">
                    <stop offset="0%" stop-color="#3b82f6" stop-opacity="0.25" />
                    <stop offset="100%" stop-color="#3b82f6" stop-opacity="0.0" />
                  </linearGradient>
                </defs>
                <!-- Línea de precio (simulada) -->
                <path d="M 0 170 L 30 168 L 60 160 L 90 165 L 120 150 L 150 155 L 180 135 L 210 130 L 240 110 L 270 115 L 300 90 L 330 95 L 360 75 L 390 80 L 420 65 L 450 55 L 480 60 L 510 45 L 540 50 L 570 35 L 600 30" 
                      fill="none" stroke="#3b82f6" stroke-width="2.5" stroke-linejoin="round" stroke-linecap="round" />
                <!-- Área bajo la línea -->
                <path d="M 0 170 L 30 168 L 60 160 L 90 165 L 120 150 L 150 155 L 180 135 L 210 130 L 240 110 L 270 115 L 300 90 L 330 95 L 360 75 L 390 80 L 420 65 L 450 55 L 480 60 L 510 45 L 540 50 L 570 35 L 600 30 L 600 220 L 0 220 Z"
                      fill="url(#gradientArea)" stroke="none" />
                <!-- Puntos de referencia -->
                <circle cx="300" cy="90" r="4" fill="#3b82f6" stroke="#0b0e14" stroke-width="2" />
                <circle cx="480" cy="60" r="4" fill="#3b82f6" stroke="#0b0e14" stroke-width="2" />
              </svg>
            </div>
            <div class="chart-footer">
              <span>Máx: $63,420.00</span>
              <span>Mín: $58,120.00</span>
              <span>Vol: 1.24B</span>
            </div>
            <div class="trade-actions">
              <button class="btn-buy" onclick="alert('Orden de compra simulada para BTC/USDT')"><i class="fas fa-arrow-up"></i> Comprar</button>
              <button class="btn-sell" onclick="alert('Orden de venta simulada para BTC/USDT')"><i class="fas fa-arrow-down"></i> Vender</button>
            </div>
          </div>

          <!-- Watchlist -->
          <div class="watchlist">
            <div class="watchlist-header">
              <h3>Lista de seguimiento</h3>
              <a href="#">Ver todo</a>
            </div>
            <div class="asset-list">
              <div class="asset-item btc">
                <div class="asset-info">
                  <div class="asset-icon">₿</div>
                  <div>
                    <div class="asset-name">Bitcoin</div>
                    <div class="asset-symbol">BTC/USDT</div>
                  </div>
                </div>
                <div class="asset-price">
                  <div class="price-value">$61,240.50</div>
                  <div class="price-change positive">+3.2%</div>
                </div>
              </div>
              <div class="asset-item eth">
                <div class="asset-info">
                  <div class="asset-icon">Ξ</div>
                  <div>
                    <div class="asset-name">Ethereum</div>
                    <div class="asset-symbol">ETH/USDT</div>
                  </div>
                </div>
                <div class="asset-price">
                  <div class="price-value">$3,420.80</div>
                  <div class="price-change positive">+1.8%</div>
                </div>
              </div>
              <div class="asset-item sol">
                <div class="asset-info">
                  <div class="asset-icon">S</div>
                  <div>
                    <div class="asset-name">Solana</div>
                    <div class="asset-symbol">SOL/USDT</div>
                  </div>
                </div>
                <div class="asset-price">
                  <div class="price-value">$148.25</div>
                  <div class="price-change negative">-0.9%</div>
                </div>
              </div>
              <div class="asset-item ada">
                <div class="asset-info">
                  <div class="asset-icon">A</div>
                  <div>
                    <div class="asset-name">Cardano</div>
                    <div class="asset-symbol">ADA/USDT</div>
                  </div>
                </div>
                <div class="asset-price">
                  <div class="price-value">$0.482</div>
                  <div class="price-change positive">+2.1%</div>
                </div>
              </div>
              <div class="asset-item dot">
                <div class="asset-info">
                  <div class="asset-icon">D</div>
                  <div>
                    <div class="asset-name">Polkadot</div>
                    <div class="asset-symbol">DOT/USDT</div>
                  </div>
                </div>
                <div class="asset-price">
                  <div class="price-value">$7.32</div>
                  <div class="price-change negative">-1.2%</div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Órdenes abiertas y actividad reciente -->
        <div class="orders-section">
          <div class="orders-card">
            <div class="orders-header">
              <span>Órdenes abiertas</span>
              <span style="color:#3b82f6; font-size:12px;">Gestionar</span>
            </div>
            <div class="order-row">
              <span>BTC/USDT <span class="badge-buy">Compra</span></span>
              <span>$59,800.00</span>
            </div>
            <div class="order-row">
              <span>ETH/USDT <span class="badge-buy">Compra</span></span>
              <span>$3,150.00</span>
            </div>
            <div class="order-row">
              <span>SOL/USDT <span class="badge-sell">Venta</span></span>
              <span>$152.40</span>
            </div>
            <div class="order-row" style="border-bottom: none;">
              <span>BTC/USDT <span class="badge-sell">Venta</span></span>
              <span>$63,200.00</span>
            </div>
          </div>
          <div class="orders-card">
            <div class="orders-header">
              <span>Actividad reciente</span>
              <span style="color:#3b82f6; font-size:12px;">Ver todo</span>
            </div>
            <div class="order-row">
              <span>Compra BTC</span>
              <span>0.025 BTC · $1,531.20</span>
            </div>
            <div class="order-row">
              <span>Venta ETH</span>
              <span>1.20 ETH · $4,104.96</span>
            </div>
            <div class="order-row">
              <span>Depósito USDT</span>
              <span>$2,000.00</span>
            </div>
            <div class="order-row" style="border-bottom: none;">
              <span>Comisión</span>
              <span>-$12.40</span>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>

  <!-- JavaScript interactivo -->
  <script>
    (function() {
      // Interactividad básica: timeframe buttons
      const tfButtons = document.querySelectorAll('.tf-btn');
      tfButtons.forEach(btn => {
        btn.addEventListener('click', function() {
          tfButtons.forEach(b => b.classList.remove('active'));
          this.classList.add('active');
          // Simular cambio de gráfico (solo alerta)
          console.log('Timeframe cambiado a: ' + this.textContent);
        });
      });

      // Simular clic en nav items
      const navItems = document.querySelectorAll('.nav-item');
      navItems.forEach(item => {
        item.addEventListener('click', function() {
          navItems.forEach(i => i.classList.remove('active'));
          this.classList.add('active');
        });
      });

      // Botones de compra/venta ya tienen onclick en HTML, pero podríamos mejorarlo
      // Watchlist: hacer clic en un activo muestra un mensaje
      const assetItems = document.querySelectorAll('.asset-item');
      assetItems.forEach(item => {
        item.addEventListener('click', function() {
          const name = this.querySelector('.asset-name')?.textContent || 'activo';
          alert(`Seleccionaste ${name}. Gráfico actualizado.`);
        });
      });

      // Balance badge y iconos: pequeña interactividad
      const iconBtns = document.querySelectorAll('.icon-btn');
      iconBtns.forEach(btn => {
        btn.addEventListener('click', () => {
          alert('Función de interfaz: notificaciones / perfil');
        });
      });

      // Simular que el balance cambia ligeramente cada 8 segundos (opcional, para realismo)
      const balanceAmount = document.querySelector('.balance-amount');
      if (balanceAmount) {
        let base = 28460.32;
        setInterval(() => {
          const variation = (Math.random() * 2 - 1) * 50; // ±50
          const newVal = base + variation;
          balanceAmount.textContent = `$${newVal.toFixed(2)}`;
        }, 8000);
      }

      // Efecto hover en las tarjetas resumen (ya está en CSS)
      console.log('Interfaz de trading cargada correctamente.');
    })();
  </script>
</body>
</html>