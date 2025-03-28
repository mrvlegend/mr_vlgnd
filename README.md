<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Arduino Boards Reference</title>
    <style>
        :root {
            --primary: #9da9a9;
            --secondary: #5b6161;
            --accent: #2a2d2e;
            --light: #8e9090;
            --dark: #00272B;
            --text: #333;
            --bg: #f9f9f9;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: var(--text);
            background-color: var(--bg);
        }
        
        header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 2rem 0;
            text-align: center;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        nav {
            background-color: var(--secondary);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        nav ul {
            display: flex;
            list-style: none;
            overflow-x: auto;
            padding: 0.5rem 0;
        }
        
        nav li {
            margin: 0 1rem;
        }
        
        nav a {
            color: white;
            text-decoration: none;
            padding: 0.5rem 1rem;
            border-radius: 4px;
            transition: background-color 0.3s;
            white-space: nowrap;
        }
        
        nav a:hover {
            background-color: var(--accent);
        }
        
        .board-section {
            background-color: white;
            margin: 2rem 0;
            padding: 2rem;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }
        
        .board-section h2 {
            color: var(--primary);
            border-bottom: 2px solid var(--light);
            padding-bottom: 0.5rem;
            margin-bottom: 1.5rem;
        }
        
        .board-section h3 {
            color: var(--secondary);
            margin: 1.5rem 0 1rem;
        }
        
        .specs-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 1.5rem;
            margin: 1.5rem 0;
        }
        
        .spec-card {
            background-color: var(--light);
            padding: 1rem;
            border-radius: 6px;
        }
        
        .spec-card h4 {
            color: var(--secondary);
            margin-bottom: 0.5rem;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 1.5rem 0;
        }
        
        th, td {
            padding: 0.75rem;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        
        th {
            background-color: var(--light);
            color: var(--secondary);
        }
        
        tr:hover {
            background-color: rgba(0, 188, 212, 0.05);
        }
        
        .board-image {
            text-align: center;
            margin: 2rem 0;
            padding: 1rem;
            background-color: #f5f5f5;
            border-radius: 6px;
        }
        
        .board-image img {
            max-width: 100%;
            height: auto;
            border: 1px solid #ddd;
            max-height: 300px;
            object-fit: contain;
        }
        
        .board-image p {
            margin-top: 1rem;
            font-style: italic;
            color: #666;
        }
        
        .block-diagram {
            text-align: center;
            margin: 2rem 0;
            padding: 1rem;
            background-color: #f5f5f5;
            border-radius: 6px;
        }
        
        .block-diagram img {
            max-width: 100%;
            height: auto;
            border: 1px solid #ddd;
        }
        
        .block-diagram p {
            margin-top: 1rem;
            font-style: italic;
            color: #666;
        }
        
        footer {
            background-color: var(--dark);
            color: white;
            text-align: center;
            padding: 2rem 0;
            margin-top: 3rem;
        }
        
        @media (max-width: 768px) {
            nav ul {
                flex-wrap: wrap;
                justify-content: center;
            }
            
            nav li {
                margin: 0.25rem;
            }
            
            .specs-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <h1>Arduino Boards</h1>
            <p>Comprehensive technical specifications and documentation for all Arduino boards</p>
        </div>
    </header>
    
    <nav>
        <div class="container">
            <ul>
                <li><a href="#uno">Uno</a></li>
                <li><a href="#mega2560">Mega 2560</a></li>
                <li><a href="#nano">Nano</a></li>
                <li><a href="#leonardo">Leonardo</a></li>
                <li><a href="#due">Due</a></li>
                <li><a href="#mkr-series">MKR Series</a></li>
                <li><a href="#zero">Zero</a></li>
                <li><a href="#pro-mini">Pro Mini</a></li>
                <li><a href="#nano-33-iot">Nano 33 IoT</a></li>
                <li><a href="#esp8266">ESP8266</a></li>
            </ul>
        </div>
    </nav>
    
    <main class="container">
        <section id="uno" class="board-section">
            <h2>Arduino Uno</h2>
            
            <div class="board-image">
                <img src="https://github.com/mrvlegend/mr_vlgnd/blob/e9235a67128f23131fba2199451e4a128a98c3c8/uno.jpg" alt="Arduino Uno Board">
                <p>Arduino Uno R3 - The most popular Arduino board for beginners</p>
            </div>
            
            <div class="block-diagram">
                <img src="images/arduino-uno-diagram.png" alt="Arduino Uno Block Diagram">
                <p>Block diagram showing the architecture of Arduino Uno with ATmega328P microcontroller, voltage regulation, and I/O interfaces.</p>
            </div>
            
            <h3>Specifications</h3>
            <div class="specs-grid">
                <div class="spec-card">
                    <h4>Microcontroller</h4>
                    <p>ATmega328P</p>
                </div>
                <div class="spec-card">
                    <h4>Operating Voltage</h4>
                    <p>5V</p>
                </div>
                <div class="spec-card">
                    <h4>Input Voltage</h4>
                    <p>7-12V (recommended)</p>
                </div>
                <div class="spec-card">
                    <h4>Digital I/O Pins</h4>
                    <p>14 (6 provide PWM output)</p>
                </div>
                <div class="spec-card">
                    <h4>Analog Input Pins</h4>
                    <p>6</p>
                </div>
                <div class="spec-card">
                    <h4>Flash Memory</h4>
                    <p>32 KB (0.5 KB used by bootloader)</p>
                </div>
                <div class="spec-card">
                    <h4>SRAM</h4>
                    <p>2 KB</p>
                </div>
                <div class="spec-card">
                    <h4>EEPROM</h4>
                    <p>1 KB</p>
                </div>
                <div class="spec-card">
                    <h4>Clock Speed</h4>
                    <p>16 MHz</p>
                </div>
            </div>
            
            <h3>Pin Functions</h3>
            <table>
                <thead>
                    <tr>
                        <th>Pin</th>
                        <th>Function</th>
                        <th>Description</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>0 (RX)</td>
                        <td>Digital I/O, Serial RX</td>
                        <td>Receive pin for serial communication</td>
                    </tr>
                    <tr>
                        <td>1 (TX)</td>
                        <td>Digital I/O, Serial TX</td>
                        <td>Transmit pin for serial communication</td>
                    </tr>
                    <tr>
                        <td>2-13</td>
                        <td>Digital I/O</td>
                        <td>General purpose digital pins (pins 3,5,6,9,10,11 can do PWM)</td>
                    </tr>
                    <tr>
                        <td>A0-A5</td>
                        <td>Analog Input</td>
                        <td>6-channel 10-bit ADC inputs</td>
                    </tr>
                    <tr>
                        <td>RESET</td>
                        <td>Reset</td>
                        <td>Reset the microcontroller</td>
                    </tr>
                    <tr>
                        <td>3.3V</td>
                        <td>Power</td>
                        <td>3.3V power supply (50mA max)</td>
                    </tr>
                    <tr>
                        <td>5V</td>
                        <td>Power</td>
                        <td>5V power supply (from regulator or USB)</td>
                    </tr>
                    <tr>
                        <td>GND</td>
                        <td>Ground</td>
                        <td>Ground pins</td>
                    </tr>
                    <tr>
                        <td>Vin</td>
                        <td>Power</td>
                        <td>Input voltage to the board (7-12V recommended)</td>
                    </tr>
                </tbody>
            </table>
        </section>
        
        <!-- Arduino Mega 2560 -->
        <section id="mega2560" class="board-section">
            <h2>Arduino Mega 2560</h2>
            
            <div class="board-image">
                <img src="images/arduino-mega2560.jpg" alt="Arduino Mega 2560 Board">
                <p>Arduino Mega 2560 R3 - High-performance board with extensive I/O</p>
            </div>
            
            <div class="block-diagram">
                <img src="images/mega2560-block-diagram.png" alt="Arduino Mega 2560 Block Diagram">
                <p>Block diagram of Arduino Mega 2560 featuring ATmega2560 microcontroller with extensive I/O capabilities.</p>
            </div>
            
            <h3>Specifications</h3>
            <div class="specs-grid">
                <div class="spec-card">
                    <h4>Microcontroller</h4>
                    <p>ATmega2560</p>
                </div>
                <div class="spec-card">
                    <h4>Operating Voltage</h4>
                    <p>5V</p>
                </div>
                <div class="spec-card">
                    <h4>Input Voltage</h4>
                    <p>7-12V (recommended)</p>
                </div>
                <div class="spec-card">
                    <h4>Digital I/O Pins</h4>
                    <p>54 (15 provide PWM output)</p>
                </div>
                <div class="spec-card">
                    <h4>Analog Input Pins</h4>
                    <p>16</p>
                </div>
                <div class="spec-card">
                    <h4>Flash Memory</h4>
                    <p>256 KB (8 KB used by bootloader)</p>
                </div>
                <div class="spec-card">
                    <h4>SRAM</h4>
                    <p>8 KB</p>
                </div>
                <div class="spec-card">
                    <h4>EEPROM</h4>
                    <p>4 KB</p>
                </div>
                <div class="spec-card">
                    <h4>Clock Speed</h4>
                    <p>16 MHz</p>
                </div>
            </div>
            
            <h3>Pin Functions</h3>
            <table>
                <thead>
                    <tr>
                        <th>Pin</th>
                        <th>Function</th>
                        <th>Description</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>0-53</td>
                        <td>Digital I/O</td>
                        <td>General purpose digital pins (pins 2-13, 44-46 can do PWM)</td>
                    </tr>
                    <tr>
                        <td>A0-A15</td>
                        <td>Analog Input</td>
                        <td>16-channel 10-bit ADC inputs</td>
                    </tr>
                    <tr>
                        <td>Serial 0-3</td>
                        <td>UART</td>
                        <td>4 hardware serial ports (RX/TX on different pins)</td>
                    </tr>
                    <tr>
                        <td>SPI</td>
                        <td>SPI</td>
                        <td>SPI communication (pins 50-53)</td>
                    </tr>
                    <tr>
                        <td>I2C</td>
                        <td>I2C</td>
                        <td>I2C communication (pins 20-SDA, 21-SCL)</td>
                    </tr>
                </tbody>
            </table>
        </section>
        
        <!-- Arduino Nano -->
        <section id="nano" class="board-section">
            <h2>Arduino Nano</h2>
            
            <div class="board-image">
                <img src="images/arduino-nano.jpg" alt="Arduino Nano Board">
                <p>Arduino Nano - Compact breadboard-friendly version of the Uno</p>
            </div>
            
            <div class="block-diagram">
                <img src="images/nano-block-diagram.png" alt="Arduino Nano Block Diagram">
                <p>Block diagram of Arduino Nano featuring ATmega328 in a compact form factor.</p>
            </div>
            
            <h3>Specifications</h3>
            <div class="specs-grid">
                <div class="spec-card">
                    <h4>Microcontroller</h4>
                    <p>ATmega328 (or ATmega168 in older versions)</p>
                </div>
                <div class="spec-card">
                    <h4>Operating Voltage</h4>
                    <p>5V</p>
                </div>
                <div class="spec-card">
                    <h4>Input Voltage</h4>
                    <p>7-12V (recommended)</p>
                </div>
                <div class="spec-card">
                    <h4>Digital I/O Pins</h4>
                    <p>14 (6 provide PWM output)</p>
                </div>
                <div class="spec-card">
                    <h4>Analog Input Pins</h4>
                    <p>8</p>
                </div>
                <div class="spec-card">
                    <h4>Flash Memory</h4>
                    <p>32 KB (2 KB used by bootloader)</p>
                </div>
                <div class="spec-card">
                    <h4>SRAM</h4>
                    <p>2 KB</p>
                </div>
                <div class="spec-card">
                    <h4>EEPROM</h4>
                    <p>1 KB</p>
                </div>
                <div class="spec-card">
                    <h4>Clock Speed</h4>
                    <p>16 MHz</p>
                </div>
            </div>
        </section>
        
        <!-- Arduino Leonardo -->
        <section id="leonardo" class="board-section">
            <h2>Arduino Leonardo</h2>
            
            <div class="board-image">
                <img src="images/arduino-leonardo.jpg" alt="Arduino Leonardo Board">
                <p>Arduino Leonardo - Features built-in USB communication</p>
            </div>
            
            <div class="block-diagram">
                <img src="images/leonardo-block-diagram.png" alt="Arduino Leonardo Block Diagram">
                <p>Block diagram of Arduino Leonardo with ATmega32U4 featuring native USB.</p>
            </div>
            
            <h3>Specifications</h3>
            <div class="specs-grid">
                <div class="spec-card">
                    <h4>Microcontroller</h4>
                    <p>ATmega32U4</p>
                </div>
                <div class="spec-card">
                    <h4>Operating Voltage</h4>
                    <p>5V</p>
                </div>
                <div class="spec-card">
                    <h4>Input Voltage</h4>
                    <p>7-12V (recommended)</p>
                </div>
                <div class="spec-card">
                    <h4>Digital I/O Pins</h4>
                    <p>20 (7 provide PWM output)</p>
                </div>
                <div class="spec-card">
                    <h4>Analog Input Pins</h4>
                    <p>12</p>
                </div>
                <div class="spec-card">
                    <h4>Flash Memory</h4>
                    <p>32 KB (4 KB used by bootloader)</p>
                </div>
                <div class="spec-card">
                    <h4>SRAM</h4>
                    <p>2.5 KB</p>
                </div>
                <div class="spec-card">
                    <h4>EEPROM</h4>
                    <p>1 KB</p>
                </div>
                <div class="spec-card">
                    <h4>Clock Speed</h4>
                    <p>16 MHz</p>
                </div>
            </div>
        </section>
        
        <!-- Continue with all other Arduino boards -->
        
    </main>
    
    <footer>
        <div class="container">
            <p>&copy; 2023 Arduino Boards Reference Guide</p>
            <p>All Arduino trademarks are property of Arduino AG</p>
            <p>This is an unofficial reference site for educational purposes</p>
        </div>
    </footer>
</body>
</html>
