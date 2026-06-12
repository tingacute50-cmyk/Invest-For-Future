<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TrendX | Elite Clearing Platform</title>
    <!-- Tailwind CSS Engine -->
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Poppins:wght@300;400;600&display=swap');
        
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #070414 0%, #0f0822 50%, #030107 100%);
        }
        .heading-font {
            font-family: 'Orbitron', sans-serif;
        }
        .glow-pink {
            text-shadow: 0 0 15px rgba(236, 72, 153, 0.6);
        }
        .gradient-border {
            background: linear-gradient(135deg, #ec4899, #8b5cf6, #22d3ee);
            padding: 2px;
            border-radius: 1.25rem;
        }
        .inner-card {
            background: #0b061a;
            border-radius: 1.15rem;
        }
        @keyframes marquee {
            0% { transform: translateX(100%); }
            100% { transform: translateX(-100%); }
        }
        .animate-ticker {
            display: inline-block;
            animation: marquee 30s linear infinite;
        }
    </style>
</head>
<body class="text-white min-h-screen flex flex-col justify-between">

    <!-- ================= AUTH GATEKEEPER SCREEN (Shown by default if not logged in) ================= -->
    <div id="authGatekeeper" class="flex-grow flex items-center justify-center p-4">
        <div class="gradient-border max-w-md w-full shadow-2xl shadow-pink-500/10">
            <div class="inner-card p-8 relative">
                <div class="text-center mb-8">
                    <h1 class="heading-font text-4xl font-extrabold tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-pink-500 via-purple-500 to-cyan-400 glow-pink">TrendX</h1>
                    <p class="text-gray-400 text-xs mt-2 font-mono uppercase tracking-widest">Institutional Asset Desk</p>
                </div>

                <!-- Tab Selectors for Gatekeeper -->
                <div class="flex border-b border-white/10 mb-6 text-sm">
                    <button id="tabLoginBtn" onclick="switchAuthTab('login')" class="w-1/2 pb-3 text-center font-semibold border-b-2 border-pink-500 text-pink-400">SIGN IN</button>
                    <button id="tabRegisterBtn" onclick="switchAuthTab('register')" class="w-1/2 pb-3 text-center font-semibold border-b-2 border-transparent text-gray-400 hover:text-white">REGISTER ACC</button>
                </div>

                <form onsubmit="handleAuthSubmit(event)" class="space-y-4">
                    <div>
                        <label class="block text-xs font-medium text-gray-400 mb-1.5">Username Identifier</label>
                        <input id="inputUser" type="text" required placeholder="Enter username" class="w-full bg-black/50 border border-purple-500/30 rounded-xl p-3 text-sm focus:outline-none focus:border-pink-500 text-white">
                    </div>
                    <div>
                        <label class="block text-xs font-medium text-gray-400 mb-1.5">Security Password</label>
                        <input id="inputPass" type="password" required placeholder="••••••••" class="w-full bg-black/50 border border-purple-500/30 rounded-xl p-3 text-sm focus:outline-none focus:border-pink-500 text-white">
                    </div>
                    <button type="submit" id="authSubmitBtn" class="w-full mt-4 bg-gradient-to-r from-pink-500 via-purple-600 to-cyan-500 py-3 rounded-xl font-bold tracking-wide uppercase shadow-lg shadow-purple-500/20 hover:opacity-90 transition">
                        Access Terminal
                    </button>
                </form>
                <p id="authFeedback" class="text-xs text-rose-400 text-center mt-3 hidden"></p>
            </div>
        </div>
    </div>


    <!-- ================= MAIN INTERNAL SECURE APPLICATION VIEW (Hidden by default) ================= -->
    <div id="appDashboard" class="hidden flex-grow flex flex-col justify-between w-full">
        
        <!-- Live Running Ticker -->
        <div class="w-full bg-purple-950/40 border-b border-white/5 py-2 overflow-hidden whitespace-nowrap text-xs font-mono tracking-wide">
            <div class="animate-ticker space-x-12">
                <span class="text-pink-400">⚡ MARKET TICKER:</span>
                <span>BTC/USD: <span class="text-emerald-400">$67,420.50 ▲</span></span>
                <span>TXC/USD: <span class="text-purple-400">$1,000.00 ▬</span></span>
                <span>EUR/USD: <span class="text-emerald-400">1.0924 ▲</span></span>
                <span>GBP/USD: <span class="text-rose-400">1.2712 ▼</span></span>
                <span>ETH/USD: <span class="text-cyan-400">$3,480.25 ▲</span></span>
                <span>USD/JPY: <span class="text-emerald-400">156.44 ▲</span></span>
            </div>
        </div>

        <!-- Dashboard Navigation Header -->
        <nav class="border-b border-white/5 bg-black/20 backdrop-blur-md px-6 py-4 flex justify-between items-center">
            <span class="heading-font text-2xl font-bold tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-pink-500 to-cyan-400">TrendX</span>
            <div class="flex items-center space-x-4">
                <span class="text-xs text-gray-400">Account: <span id="dashboardUser" class="text-cyan-400 font-bold"></span></span>
                <button onclick="logoutSession()" class="bg-rose-500/20 hover:bg-rose-600 border border-rose-500/40 px-4 py-1.5 rounded-lg text-xs font-semibold transition">
                    Logout Terminal
                </button>
            </div>
        </nav>

        <!-- Dynamic Explanatory Banner -->
        <div class="max-w-7xl mx-auto px-6 mt-6 w-full">
            <div class="bg-gradient-to-r from-purple-950/60 to-black/40 border border-purple-500/20 rounded-xl p-4 text-xs md:text-sm text-gray-300">
                🚀 <span class="text-pink-400 font-bold">Deferred Payment Window:</span> You can instantly buy assets right now and hold them for up to <span class="text-cyan-400 font-bold">24 hours with no verified email or bank linked</span>! Pay only original rate at maturity. (e.g., 10 coins at $1,000 cost $10,000 even if the coin surges above $5,000 later).
            </div>
        </div>

        <!-- Core Workspace Framework -->
        <main class="max-w-7xl mx-auto px-6 py-6 grid md:grid-cols-3 gap-6 w-full items-start">
            
            <!-- Column 1: Live Interactive Analytics Chart Component -->
            <section class="bg-white/5 border border-white/5 rounded-2xl p-4 backdrop-blur-md md:col-span-2">
                <div class="flex justify-between items-center mb-4">
                    <div>
                        <h2 class="heading-font text-base font-bold text-white">TrendX Live Market Index</h2>
                        <p class="text-[10px] text-gray-500 font-mono">Simulated Real-Time Exchange Candlesticks</p>
                    </div>
                    <span class="text-xs bg-emerald-500/20 text-emerald-400 border border-emerald-500/30 px-2 py-0.5 rounded font-mono font-bold">LIVE STREAM</span>
                </div>
                
                <!-- SVG Vector Candlestick Chart Simulation -->
                <div class="w-full bg-black/50 border border-white/5 rounded-xl p-4 flex flex-col justify-between h-64 relative">
                    <svg class="w-full h-full" viewBox="0 0 400 150" preserveAspectRatio="none">
                        <!-- Horizontal Grid Lines -->
                        <line x1="0" y1="37" x2="400" y2="37" stroke="rgba(255,255,255,0.05)" stroke-dasharray="4"/>
                        <line x1="0" y1="75" x2="400" y2="75" stroke="rgba(255,255,255,0.05)" stroke-dasharray="4"/>
                        <line x1="0" y1="112" x2="400" y2="112" stroke="rgba(255,255,255,0.05)" stroke-dasharray="4"/>
                        
                        <!-- Simulated Candlestick Bars (Shares/Crypto Style) -->
                        <!-- Bar 1 (Green) -->
                        <line x1="40" y1="100" x2="40" y2="130" stroke="#10b981" stroke-width="1.5"/>
                        <rect x="33" y="105" width="14" height="20" fill="#10b981" rx="1"/>
                        <!-- Bar 2 (Green) -->
                        <line x1="100" y1="70" x2="100" y2="115" stroke="#10b981" stroke-width="1.5"/>
                        <rect x="93" y="80" width="14" height="25" fill="#10b981" rx="1"/>
                        <!-- Bar 3 (Red) -->
                        <line x1="160" y1="85" x2="160" y2="130" stroke="#f43f5e" stroke-width="1.5"/>
                        <rect x="153" y="90" width="14" height="30" fill="#f43f5e" rx="1"/>
                        <!-- Bar 4 (Green) -->
                        <line x1="220" y1="40" x2="220" y2="100" stroke="#10b981" stroke-width="1.5"/>
                        <rect x="213" y="50" width="14" height="45" fill="#10b981" rx="1"/>
                        <!-- Bar 5 (Red) -->
                        <line x1="280" y1="60" x2="280" y2="110" stroke="#f43f5e" stroke-width="1.5"/>
                        <rect x="273" y="65" width="14" height="25" fill="#f43f5e" rx="1"/>
                        <!-- Bar 6 (Green Trend Surge) -->
                        <line x1="340" y1="20" x2="340" y2="80" stroke="#10b981" stroke-width="1.5"/>
                        <rect x="333" y="30" width="14" height="40" fill="#10b981" rx="1"/>
                    </svg>
                    <!-- Chart Legend Axes -->
                    <div class="flex justify-between text-[10px] text-gray-500 font-mono mt-2 border-t border-white/5 pt-2">
                        <span>09:00 AM</span>
                        <span>11:00 AM</span>
                        <span>01:00 PM</span>
                        <span>03:00 PM</span>
                    </div>
                </div>
            </section>

            <!-- Column 2: Buy & Sell Desk Section -->
            <section class="bg-white/5 border border-white/5 rounded-2xl p-5 backdrop-blur-md">
                <div class="flex border-b border-white/10 mb-4 text-xs font-bold">
                    <button id="orderBuyTab" onclick="toggleOrderMode('buy')" class="w-1/2 pb-2 text-center border-b-2 border-pink-500 text-pink-400">BUY ACTION</button>
                    <button id="orderSellTab" onclick="toggleOrderMode('sell')" class="w-1/2 pb-2 text-center border-b-2 border-transparent text-gray-400 hover:text-white">SELL ACTION</button>
                </div>

                <div class="space-y-4 text-xs">
                    <div>
                        <label class="block text-gray-400 mb-1.5">Asset Listing Target</label>
                        <select id="tradingAsset" onchange="runCalculationEngine()" class="w-full bg-black/40 border border-purple-500/20 rounded-xl p-3 text-white focus:outline-none focus:border-pink-500">
                            <option value="1000">Crypto: TrendX (TXC) — $1,000.00</option>
                            <option value="67420">Crypto: Bitcoin (BTC) — $67,420.00</option>
                            <option value="10000">Forex: EUR/USD Block — $10,000.00</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-gray-400 mb-1.5">Quantity Size</label>
                        <input id="tradingQty" type="number" value="10" min="1" oninput="runCalculationEngine()" class="w-full bg-black/40 border border-purple-500/20 rounded-xl p-3 text-white focus:outline-none focus:border-pink-500">
                    </div>

                    <div class="bg-purple-950/20 border border-purple-500/20 rounded-xl p-3 space-y-2 font-mono">
                        <div class="flex justify-between text-gray-400">
                            <span>Locked Basis Price:</span>
                            <span id="calcBasisPrice">$1,000.00</span>
                        </div>
                        <div class="flex justify-between font-bold text-pink-400 border-t border-white/5 pt-1.5">
                            <span>Maturity Outlay Due:</span>
                            <span id="calcTotalDue">$10,000.00</span>
                        </div>
                    </div>

                    <button onclick="submitTradeOrder()" class="w-full bg-gradient-to-r from-pink-500 to-purple-600 py-3 rounded-xl font-bold uppercase tracking-wider shadow-md hover:opacity-95 transition">
                        <span id="tradeButtonText">Execute Deferred Buy</span>
                    </button>
                </div>
            </section>
        </main>

        <!-- Lower Grid Layer: Email Update, Verification Vault Status & Orders -->
        <div class="max-w-7xl mx-auto px-6 pb-12 grid md:grid-cols-3 gap-6 w-full items-start">
            
            <!-- Email & Vault Details Verification Panel -->
            <section class="bg-white/5 border border-white/5 rounded-2xl p-5 backdrop-blur-md">
                <h3 class="heading-font text-sm font-bold text-cyan-400 mb-1.5">🔒 Profile Custody Vault</h3>
                <p class="text-[11px] text-gray-400 mb-4">Update routing channels to preserve custody past the 24-Hour sandbox exemption window.</p>
                
                <div class="space-y-3 text-xs">
                    <div>
                        <label class="block text-gray-400 mb-1">Email Coordinates</label>
                        <input id="vaultEmail" type="email" placeholder="client@trendx-network.com" class="w-full bg-black/40 border border-purple-500/20 rounded-xl p-2.5 text-white focus:outline-none focus:border-cyan-400">
                    </div>
                    <div>
                        <label class="block text-gray-400 mb-1">Clearing Bank Account Routing</label>
                        <input id="vaultBank" type="text" placeholder="US12 3456 7890 1234" class="w-full bg-black/40 border border-purple-500/20 rounded-xl p-2.5 text-white focus:outline-none focus:border-cyan-400">
                    </div>
                    <button onclick="saveVaultInformation()" class="w-full bg-cyan-500/20 hover:bg-cyan-500 border border-cyan-400 text-cyan-300 hover:text-white font-semibold py-2 rounded-xl transition">
                        Update Contact & Account Vault
                    </button>
                </div>
            </section>

            <!-- Ledger Activity Table Components -->
            <section class="bg-white/5 border border-white/5 rounded-2xl p-5 backdrop-blur-md md:col-span-2 overflow-x-auto">
                <h3 class="heading-font text-sm font-bold text-purple-400 mb-3">📋 Open Sandbox Ledger Positions</h3>
                <table class="w-full text-left border-collapse text-[11px]">
                    <thead>
                        <tr class="border-b border-white/10 text-gray-500">
                            <th class="pb-2">Asset Allocation</th>
                            <th class="pb-2">Size</th>
                            <th class="pb-2">Locked Cost</th>
                            <th class="pb-2">Exemption Status</th>
                        </tr>
                    </thead>
                    <tbody id="ledgerRows" class="text-gray-300 divide-y divide-white/5">
                        <tr>
                            <td colspan="4" class="pt-4 text-center text-gray-600 italic">No assets committed during this session context.</td>
                        </tr>
                    </tbody>
                </table>
            </section>
        </div>
    </div>

    <!-- Footer Security Banner -->
    <footer class="w-full text-center py-3 bg-black/40 border-t border-white/5 text-[10px] text-gray-600 font-mono">
        TrendX Node Ledger Interface Core • Powered by Persistent Memory Cache System © 2026.
    </footer>


    <!-- ================= SYSTEM ENGINE JAVASCRIPT ARCHITECTURE ================= -->
    <script>
        let currentAuthMode = 'login';
        let internalTradeMode = 'buy';
        let dynamicActiveSessionUser = null;

        // Auto-check for existing credentials or login state during boot sequence
        window.onload = function() {
            const preservedUser = sessionStorage.getItem('activeUser');
            if (preservedUser) {
                initializeDashboardView(preservedUser);
            } else {
                showAuthGatekeeper();
            }
        };

        function switchAuthTab(targetTab) {
            currentAuthMode = targetTab;
            const loginBtn = document.getElementById('tabLoginBtn');
            const registerBtn = document.getElementById('tabRegisterBtn');
            const submitBtn = document.getElementById('authSubmitBtn');
            const modalTitle = document.getElementById('modalTitle');

            if (targetTab === 'login') {
                loginBtn.className = "w-1/2 pb-3 text-center font-semibold border-b-2 border-pink-500 text-pink-400";
                registerBtn.className = "w-1/2 pb-3 text-center font-semibold border-b-2 border-transparent text-gray-400 hover:text-white";
                submitBtn.innerText = "Access Terminal";
            } else {
                registerBtn.className = "w-1/2 pb-3 text-center font-semibold border-b-2 border-cyan-400 text-cyan-400";
                loginBtn.className = "w-1/2 pb-3 text-center font-semibold border-b-2 border-transparent text-gray-400 hover:text-white";
                submitBtn.innerText = "Register Perpetual Account";
            }
        }

        function handleAuthSubmit(event) {
            event.preventDefault();
            const usernameInput = document.getElementById('inputUser').value.trim();
            const passwordInput = document.getElementById('inputPass').value;
            const feedback = document.getElementById('authFeedback');
            feedback.classList.add('hidden');

            if (!usernameInput || !passwordInput) return;

            if (currentAuthMode === 'register') {
                // Check if account name already exists in perpetual localStorage
                if (localStorage.getItem('trendx_user_' + usernameInput)) {
                    feedback.innerText = "Identity conflict: That username exists forever.";
                    feedback.classList.remove('hidden');
                    return;
                }
                // Save credentials indefinitely into localStorage
                localStorage.setItem('trendx_user_' + usernameInput, passwordInput);
                alert("🎉 Perpetual Account Created! You can now use these credentials to log in forever.");
                switchAuthTab('login');
            } else {
                // Login validation process
                const absoluteSavedPassword = localStorage.getItem('trendx_user_' + usernameInput);
                if (absoluteSavedPassword && absoluteSavedPassword === passwordInput) {
                    sessionStorage.setItem('activeUser', usernameInput);
                    initializeDashboardView(usernameInput);
                } else {
                    feedback.innerText = "Access Denied: Invalid credentials pattern.";
                    feedback.classList.remove('hidden');
                }
            }
        }

        function initializeDashboardView(user) {
            dynamicActiveSessionUser = user;
            document.getElementById('dashboardUser').innerText = user;
            
            // Layout View Shifting Sequence
            document.getElementById('authGatekeeper').classList.add('hidden');
            document.getElementById('appDashboard').classList.remove('hidden');
            
            // Sync values
            runCalculationEngine();
            loadSavedVaultData();
        }

        function logoutSession() {
            sessionStorage.removeItem('activeUser');
            dynamicActiveSessionUser = null;
            
            // Clear temporary execution input entries
            document.getElementById('inputUser').value = '';
            document.getElementById('inputPass').value = '';
            
            showAuthGatekeeper();
        }

        function showAuthGatekeeper() {
            document.getElementById('appDashboard').classList.add('hidden');
            document.getElementById('authGatekeeper').classList.remove('hidden');
            switchAuthTab('login');
        }

        function toggleOrderMode(mode) {
            internalTradeMode = mode;
            const buyTab = document.getElementById('orderBuyTab');
            const sellTab = document.getElementById('orderSellTab');
            const btnText = document.getElementById('tradeButtonText');

            if (mode === 'buy') {
                buyTab.className = "w-1/2 pb-2 text-center border-b-2 border-pink-500 text-pink-400";
                sellTab.className = "w-1/2 pb-2 text-center border-b-2 border-transparent text-gray-400 hover:text-white";
                btnText.innerText = "Execute Deferred Buy";
            } else {
                sellTab.className = "w-1/2 pb-2 text-center border-b-2 border-cyan-400 text-cyan-400";
                buyTab.className = "w-1/2 pb-2 text-center border-b-2 border-transparent text-gray-400 hover:text-white";
                btnText.innerText = "Execute Instant Sell Action";
            }
        }

        function runCalculationEngine() {
            const price = parseFloat(document.getElementById('tradingAsset').value);
            const volume = parseFloat(document.getElementById('tradingQty').value) || 0;
            const total = price * volume;

            document.getElementById('calcBasisPrice').innerText = `$${price.toLocaleString()}`;
            document.getElementById('calcTotalDue').innerText = `$${total.toLocaleString(undefined, {minimumFractionDigits: 2})}`;
        }

        function submitTradeOrder() {
            const selector = document.getElementById('tradingAsset');
            const assetName = selector.options[selector.selectedIndex].text.split('—')[0].trim();
            const volume = parseFloat(document.getElementById('tradingQty').value) || 0;
            const price = parseFloat(selector.value);
            const finalCost = price * volume;

            if (volume <= 0) {
                alert("Please designate an asset volume size value.");
                return;
            }

            const body = document.getElementById('ledgerRows');
            if (body.children.length === 1 && body.children[0].cells.length === 1) {
                body.innerHTML = '';
            }

            const tr = document.createElement('tr');
            tr.className = "hover:bg-white/5 transition-colors font-mono";
            tr.innerHTML = `
                <td class="py-3 font-semibold text-white">${assetName}</td>
                <td class="py-3 text-cyan-400">${volume}</td>
                <td class="py-3 text-pink-400 font-bold">$${finalCost.toLocaleString()}</td>
                <td class="py-3"><span class="bg-emerald-500/10 text-emerald-400 border border-emerald-500/20 px-2 py-0.5 rounded text-[10px]">24H Exemption Active</span></td>
            `;
            body.appendChild(tr);

            alert(`Order Verified!\nAllocated ${volume} of ${assetName}. Position locked at $${finalCost.toLocaleString()} for 24 Hours without email/bank dependencies.`);
        }

        function saveVaultInformation() {
            const email = document.getElementById('vaultEmail').value.trim();
            const bank = document.getElementById('vaultBank').value.trim();

            if(dynamicActiveSessionUser) {
                // Storing user configuration parameters connected to active username
                localStorage.setItem(`trendx_email_${dynamicActiveSessionUser}`, email);
                localStorage.setItem(`trendx_bank_${dynamicActiveSessionUser}`, bank);
                alert("⚙️ Profile parameters saved permanently inside localized memory banks!");
            }
        }

        function loadSavedVaultData() {
            if (dynamicActiveSessionUser) {
                document.getElementById('vaultEmail').value = localStorage.getItem(`trendx_email_${dynamicActiveSessionUser}`) || '';
                document.getElementById('vaultBank').value = localStorage.getItem(`trendx_bank_${dynamicActiveSessionUser}`) || '';
            }
        }
    </script>
</body>
</html>
