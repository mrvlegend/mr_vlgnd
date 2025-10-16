<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Power Grid Fault Monitoring System</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: #0a0e27;
            color: #fff;
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* Animated electrical background */
        .background-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #0a0e27 0%, #1a1f3a 50%, #0a0e27 100%);
            z-index: -1;
        }

        .grid-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(0, 255, 255, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 255, 255, 0.03) 1px, transparent 1px);
            background-size: 50px 50px;
            z-index: -1;
        }

        /* Header Section */
        header {
            background: linear-gradient(135deg, rgba(255, 193, 7, 0.1), rgba(255, 87, 34, 0.1));
            border-bottom: 3px solid #ffc107;
            padding: 25px 20px;
            box-shadow: 0 5px 30px rgba(255, 193, 7, 0.3);
            position: relative;
            overflow: hidden;
        }

        header::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 193, 7, 0.2), transparent);
            animation: scan 3s infinite;
        }

        @keyframes scan {
            0% { left: -100%; }
            100% { left: 100%; }
        }

        .header-content {
            max-width: 1400px;
            margin: 0 auto;
            display: flex;
            align-items: center;
            justify-content: space-between;
            position: relative;
            z-index: 1;
        }

        .logo-section {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .logo {
            width: 70px;
            height: 70px;
            background: linear-gradient(135deg, #ffc107, #ff5722);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.5em;
            box-shadow: 0 0 20px rgba(255, 193, 7, 0.5);
            animation: pulse-glow 2s infinite;
        }

        @keyframes pulse-glow {
            0%, 100% { box-shadow: 0 0 20px rgba(255, 193, 7, 0.5); }
            50% { box-shadow: 0 0 30px rgba(255, 193, 7, 0.8); }
        }

        .header-text h1 {
            font-size: 2em;
            color: #ffc107;
            text-shadow: 0 0 10px rgba(255, 193, 7, 0.5);
            margin-bottom: 5px;
        }

        .header-text p {
            color: #00e5ff;
            font-size: 0.95em;
        }

        .status-badge {
            background: rgba(76, 175, 80, 0.2);
            border: 2px solid #4caf50;
            padding: 10px 20px;
            border-radius: 25px;
            display: flex;
            align-items: center;
            gap: 10px;
            box-shadow: 0 0 15px rgba(76, 175, 80, 0.3);
        }

        .status-dot {
            width: 12px;
            height: 12px;
            background: #4caf50;
            border-radius: 50%;
            animation: blink 1.5s infinite;
        }

        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.3; }
        }

        /* Main Container */
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 30px 20px;
        }

        /* Stats Cards */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .stat-card {
            background: linear-gradient(135deg, rgba(255, 193, 7, 0.1), rgba(255, 87, 34, 0.1));
            border: 2px solid rgba(255, 193, 7, 0.3);
            border-radius: 15px;
            padding: 25px;
            position: relative;
            overflow: hidden;
            transition: all 0.3s;
        }

        .stat-card:hover {
            transform: translateY(-5px);
            border-color: #ffc107;
            box-shadow: 0 10px 30px rgba(255, 193, 7, 0.3);
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 193, 7, 0.1), transparent);
            transition: 0.5s;
        }

        .stat-card:hover::before {
            left: 100%;
        }

        .stat-icon {
            font-size: 2.5em;
            margin-bottom: 15px;
        }

        .stat-label {
            color: #00e5ff;
            font-size: 0.9em;
            margin-bottom: 8px;
        }

        .stat-value {
            font-size: 2em;
            font-weight: bold;
            color: #ffc107;
            text-shadow: 0 0 10px rgba(255, 193, 7, 0.5);
        }

        /* Main Content Grid */
        .main-grid {
            display: grid;
            grid-template-columns: 1.5fr 1fr;
            gap: 30px;
            margin-bottom: 30px;
        }

        .panel {
            background: linear-gradient(135deg, rgba(26, 31, 58, 0.9), rgba(10, 14, 39, 0.9));
            border: 2px solid rgba(0, 229, 255, 0.3);
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
        }

        .panel-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 2px solid rgba(0, 229, 255, 0.2);
        }

        .panel-title {
            font-size: 1.5em;
            color: #00e5ff;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .panel-icon {
            font-size: 1.3em;
        }

        /* ESP32 Monitor Section */
        .monitor-container {
            position: relative;
            background: #000;
            border: 3px solid #ffc107;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 0 30px rgba(255, 193, 7, 0.4);
        }

        .monitor-header {
            background: linear-gradient(135deg, #ffc107, #ff5722);
            padding: 12px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            font-weight: bold;
            color: #000;
        }

        .monitor-controls {
            display: flex;
            gap: 8px;
        }

        .control-btn {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: #fff;
            cursor: pointer;
        }

        .control-btn.close { background: #f44336; }
        .control-btn.minimize { background: #ffc107; }
        .control-btn.maximize { background: #4caf50; }

        .monitor-display {
            width: 100%;
            height: 550px;
            background: #000;
            position: relative;
        }

        .monitor-display iframe {
            width: 100%;
            height: 100%;
            border: none;
        }

        .server-link {
            margin-top: 15px;
            padding: 15px;
            background: rgba(255, 193, 7, 0.1);
            border-left: 4px solid #ffc107;
            border-radius: 5px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .open-new-tab {
            background: linear-gradient(135deg, #ffc107, #ff5722);
            color: #000;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
        }

        .open-new-tab:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(255, 193, 7, 0.4);
        }

        /* Complaint Form */
        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            color: #00e5ff;
            font-weight: 600;
            margin-bottom: 8px;
            font-size: 0.95em;
        }

        input, textarea, select {
            width: 100%;
            padding: 12px;
            background: rgba(0, 229, 255, 0.05);
            border: 2px solid rgba(0, 229, 255, 0.3);
            border-radius: 8px;
            color: #fff;
            font-size: 1em;
            transition: all 0.3s;
        }

        input:focus, textarea:focus, select:focus {
            outline: none;
            border-color: #00e5ff;
            background: rgba(0, 229, 255, 0.1);
            box-shadow: 0 0 15px rgba(0, 229, 255, 0.2);
        }

        textarea {
            resize: vertical;
            min-height: 120px;
            font-family: inherit;
        }

        select {
            cursor: pointer;
        }

        option {
            background: #1a1f3a;
            color: #fff;
        }

        .submit-btn {
            width: 100%;
            padding: 15px;
            background: linear-gradient(135deg, #ffc107, #ff5722);
            color: #000;
            border: none;
            border-radius: 8px;
            font-size: 1.1em;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 30px rgba(255, 193, 7, 0.4);
        }

        .submit-btn:active {
            transform: translateY(0);
        }

        .success-message {
            display: none;
            background: rgba(76, 175, 80, 0.2);
            border: 2px solid #4caf50;
            color: #4caf50;
            padding: 15px;
            border-radius: 8px;
            margin-top: 15px;
            text-align: center;
            animation: slideIn 0.3s;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Alert Section */
        .alert-section {
            grid-column: 1 / -1;
        }

        .alerts-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 15px;
        }

        .alert-item {
            background: rgba(255, 87, 34, 0.1);
            border-left: 4px solid #ff5722;
            padding: 15px;
            border-radius: 8px;
            display: flex;
            align-items: center;
            gap: 15px;
            transition: all 0.3s;
        }

        .alert-item:hover {
            background: rgba(255, 87, 34, 0.2);
            transform: translateX(5px);
        }

        .alert-icon {
            font-size: 2em;
        }

        .alert-content h4 {
            color: #ff5722;
            margin-bottom: 5px;
        }

        .alert-content p {
            color: #aaa;
            font-size: 0.9em;
        }

        /* Footer */
        footer {
            background: rgba(26, 31, 58, 0.5);
            border-top: 2px solid rgba(0, 229, 255, 0.3);
            padding: 20px;
            text-align: center;
            color: #00e5ff;
            margin-top: 30px;
        }

        /* Responsive */
        @media (max-width: 968px) {
            .main-grid {
                grid-template-columns: 1fr;
            }

            .header-content {
                flex-direction: column;
                gap: 15px;
                text-align: center;
            }

            .stats-grid {
                grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            }

            .header-text h1 {
                font-size: 1.5em;
            }

            .monitor-display {
                height: 400px;
            }
        }
    </style>
</head>
<body>
    <div class="background-animation"></div>
    <div class="grid-overlay"></div>

    <header>
        <div class="header-content">
            <div class="logo-section">
                <div class="logo">⚡</div>
                <div class="header-text">
                    <h1>POWER GRID MONITORING SYSTEM</h1>
                    <p>Real-Time Fault Detection & Transmission Line Analysis</p>
                </div>
            </div>
            <div class="status-badge">
                <div class="status-dot"></div>
                <span>SYSTEM ONLINE</span>
            </div>
        </div>
    </header>

    <div class="container">
        <!-- Statistics Cards -->
        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-icon">🔌</div>
                <div class="stat-label">Active Lines</div>
                <div class="stat-value" id="activeLines">24</div>
            </div>
            <div class="stat-card">
                <div class="stat-icon">⚠</div>
                <div class="stat-label">Active Faults</div>
                <div class="stat-value" id="activeFaults">3</div>
            </div>
            <div class="stat-card">
                <div class="stat-icon">📊</div>
                <div class="stat-label">Load Factor</div>
                <div class="stat-value" id="loadFactor">87%</div>
            </div>
            <div class="stat-card">
                <div class="stat-icon">🔋</div>
                <div class="stat-label">System Health</div>
                <div class="stat-value" id="systemHealth">GOOD</div>
            </div>
        </div>

        <!-- Main Content -->
        <div class="main-grid">
            <!-- Live Monitor Panel -->
            <div class="panel">
                <div class="panel-header">
                    <div class="panel-title">
                        <span class="panel-icon">📡</span>
                        LIVE TRANSMISSION MONITOR
                    </div>
                </div>
                
                <div class="monitor-container">
                    <div class="monitor-header">
                        <span>ESP32 Server - 10.158.232.148</span>
                        <div class="monitor-controls">
                            <div class="control-btn close"></div>
                            <div class="control-btn minimize"></div>
                            <div class="control-btn maximize"></div>
                        </div>
                    </div>
                    <div class="monitor-display">
                        <iframe src="http://10.158.232.148" title="ESP32 Fault Monitor"></iframe>
                    </div>
                </div>

                <div class="server-link">
                    <span>🔗 Direct Server Access: http://10.158.232.148</span>
                    <button class="open-new-tab" onclick="window.open('http://10.158.232.148', '_blank')">
                        OPEN IN NEW TAB ↗
                    </button>
                </div>
            </div>

            <!-- Complaint Form Panel -->
            <div class="panel">
                <div class="panel-header">
                    <div class="panel-title">
                        <span class="panel-icon">📝</span>
                        FAULT REPORTING
                    </div>
                </div>

                <form id="complaintForm">
                    <div class="form-group">
                        <label for="name">NAME *</label>
                        <input type="text" id="name" name="name" placeholder="Enter your full name" required>
                    </div>

                    <div class="form-group">
                        <label for="contact">CONTACT NUMBER *</label>
                        <input type="tel" id="contact" name="contact" placeholder="+91 XXXXX XXXXX" required>
                    </div>

                    <div class="form-group">
                        <label for="email">EMAIL ADDRESS</label>
                        <input type="email" id="email" name="email" placeholder="your.email@example.com">
                    </div>
                    <div class="form-group">
                        <label for="faultType">FAULT TYPE *</label>
                        <select id="faultType" name="faultType" required>
                            <option value="">-- Select Fault Type --</option>
                            <option value="power_outage">⚫ Complete Power Outage</option>
                            <option value="voltage_fluctuation">⚡ Voltage Fluctuation</option>
                            <option value="line_damage">🔧 Transmission Line Damage</option>
                            <option value="sparking">💥 Electrical Sparking</option>
                            <option value="transformer_issue">🔋 Transformer Malfunction</option>
                            <option value="short_circuit">⚠ Short Circuit</option>
                            <option value="cable_theft">🚨 Cable Theft/Vandalism</option>
                            <option value="other">📌 Other Issue</option>
                        </select>
                    </div>

                    <div class="form-group">
                        <label for="description">DETAILED DESCRIPTION *</label>
                        <textarea id="description" name="description" placeholder="Provide detailed information about the fault..." required></textarea>
                    </div>

                    <button type="submit" class="submit-btn">⚡ Submit Complaint</button>
                    
                    <div class="success-message" id="successMessage">
                        ✅ COMPLAINT REGISTERED SUCCESSFULLY!<br>
                        <strong>Reference ID: <span id="refId"></span></strong><br>
                        Your complaint has been forwarded to the electricity supplier.
                    </div>
                </form>
            </div>
        </div>

        <!-- Recent Alerts -->
        <div class="panel alert-section">
            <div class="panel-header">
                <div class="panel-title">
                    <span class="panel-icon">🚨</span>
                    RECENT ALERTS
                </div>
            </div>
            <div class="alerts-container">
                <div class="alert-item">
                    <div class="alert-icon">⚠</div>
                    <div class="alert-content">
                        <h4>Voltage Spike Detected</h4>
                        <p>Line 7B - 2 minutes ago</p>
                    </div>
                </div>
                <div class="alert-item">
                    <div class="alert-icon">🔧</div>
                    <div class="alert-content">
                        <h4>Maintenance Required</h4>
                        <p>Transformer T-12 - 15 minutes ago</p>
                    </div>
                </div>
                <div class="alert-item">
                    <div class="alert-icon">📉</div>
                    <div class="alert-content">
                        <h4>Load Imbalance</h4>
                        <p>Sector 3 - 28 minutes ago</p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <footer>
        <p>⚡ Power Grid Monitoring System | Real-Time Fault Detection & Analysis</p>
        <p style="margin-top: 5px; font-size: 0.9em; color: #888;">
            Emergency Helpline: 1912 | System Status: Operational
        </p>
    </footer>

    <script>
        // Form submission handler
        document.getElementById('complaintForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const refId = 'FLT' + Date.now().toString().slice(-8);
            
            const formData = {
                refId: refId,
                name: document.getElementById('name').value,
                contact: document.getElementById('contact').value,
                email: document.getElementById('email').value,
                location: document.getElementById('location').value,
                faultType: document.getElementById('faultType').value,
                description: document.getElementById('description').value,
                timestamp: new Date().toLocaleString('en-IN')
            };
            
            console.log('Fault Report Submitted:', formData);
            
            document.getElementById('refId').textContent = refId;
            document.getElementById('successMessage').style.display = 'block';
            
            this.reset();
            
            setTimeout(() => {
                document.getElementById('successMessage').style.display = 'none';
            }, 6000);
        });

        // Dynamic stats animation
        function updateStats() {
            const activeFaults = Math.floor(Math.random() * 5) + 1;
            const loadFactor = Math.floor(Math.random() * 20) + 75;
            
            document.getElementById('activeFaults').textContent = activeFaults;
            document.getElementById('loadFactor').textContent = loadFactor + '%';
        }

        setInterval(updateStats, 5000);
    </script>
</body>
</html>
