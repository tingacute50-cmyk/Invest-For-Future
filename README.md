<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TrendX Portal</title>
    <style>
        /* All CSS styles are now embedded directly here */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #020617;
            color: #ffffff;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        .ticker-wrap {
            width: 100%;
            background: linear-gradient(90deg, #10b981, #06b6d4, #6366f1);
            color: #020617;
            font-weight: bold;
            padding: 12px;
            overflow: hidden;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .ticker-text {
            display: inline-block;
            white-space: nowrap;
            padding-left: 100%;
            animation: marquee 25s linear infinite;
        }

        @keyframes marquee {
            0% { transform: translate3d(0, 0, 0); }
            100% { transform: translate3d(-100%, 0, 0); }
        }

        .container {
            max-width: 1200px;
            margin: 30px auto;
            padding: 0 20px;
            width: 100%;
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 30px;
        }

        @media (max-width: 768px) {
            .container {
                grid-template-columns: 1fr;
            }
        }

        .card {
            background-color: #0f172a;
            border: 2px solid #1e293b;
            border-radius: 16px;
            padding: 24px;
            margin-bottom: 24px;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.3);
        }

        .card-premium {
            border-color: rgba(16, 185, 129, 0.3);
            background: linear-gradient(135deg, #0f172a 0%, #030712 100%);
        }

        h1, h2, h3 {
            margin-bottom: 15px;
            font-weight: 800;
        }

        .text-gradient {
            background: linear-gradient(90deg, #34d399, #22d3ee);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .text-emerald { color: #10b981; }
        .text-cyan { color: #22d3ee; }

        .input-field {
            width: 100%;
            background-color: #1e293b;
            border: 2px solid #334155;
            border-radius: 8px;
            padding: 12px;
            color: white;
            font-size: 16px;
            margin-top: 8px;
            outline: none;
        }

        .input-field:focus {
            border-color: #10b981;
        }

        .btn-submit {
            width: 100%;
            background: linear-gradient(90deg, #10b981, #06b6d4);
            color: #020617;
            font-weight: bold;
            padding: 14px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
    </style>
</head>
<body>

    <div class="ticker-wrap">
        <div class="ticker-text">
            🔥 TRENDX CHAIN: PORTAL SYSTEM SECURED AND CONNECTED TO GLOBAL NODES ... 🚀 CRYPTO MARKET ALERTS: TOKEN STABILIZED AT FIXED ENTRY PROTECTION PRESETS ...
        </div>
    </div>

    <div class="container">
        <div>
            <div class="card card-premium">
                <h2 class="text-gradient">⭐ PORTAL INVESTMENT POLICIES</h2>
                <p style="color: #cbd5e1; line-height: 1.6; margin-bottom: 10px;">
                    <strong class="text-cyan">1. Fixed Term Holding:</strong> Assets placed within the ledger architecture undergo automated execution synchronization over a designated 5-year lock schedule.
                </p>
                <p style="color: #cbd5e1; line-height: 1.6;">
                    <strong class="text-emerald">2. Value Protection Entry:</strong> Ledger settlements default strictly to base rates recorded on the precise timestamp of configuration.
                </p>
            </div>

            <div class="card">
                <h3 class="text-emerald">💰 TRANSACTION TERMINAL</h3>
                <div style="margin-top: 20px;">
                    <label style="color: #94a3b8; font-size: 14px;">CURRENT ASSET BASE VALUE</label>
                    <div style="font-size: 32px; font-weight: bold; color: #34d399; margin-bottom: 20px;">₹1,000 INR</div>
                    
                    <label style="color: #94a3b8; font-size: 14px;">ENTER TARGET VOLUME</label>
                    <input type="number" class="input-field" value="10">
                </div>
                <div style="margin-top: 20px;">
                    <button class="btn-submit">Initialize Allocation Agreement</button>
                </div>
            </div>
        </div>

        <div>
            <div class="card">
                <h3 class="text-cyan">NETWORK FEEDS</h3>
                <p style="color: #94a3b8; font-size: 14px; margin-top: 10px;">
                    Device Status: <span class="text-emerald">Online</span>
                </p>
                <p style="color: #94a3b8; font-size: 14px; margin-top: 5px;">
                    Sync Protocol: <span class="text-cyan">Active</span>
                </p>
            </div>
        </div>
    </div>

</body>
</html>
