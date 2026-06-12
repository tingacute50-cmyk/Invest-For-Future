<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TrendX | Premium Multi-Asset Clearing</title>
    <!-- Tailwind CSS for modern layout -->
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Poppins:wght@300;400;600&display=swap');
        
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #0b071e 0%, #130a2b 50%, #05020c 100%);
        }
        .heading-font {
            font-family: 'Orbitron', sans-serif;
        }
        .neon-text-pink {
            text-shadow: 0 0 10px rgba(236, 72, 153, 0.6);
        }
        .neon-text-cyan {
            text-shadow: 0 0 10px rgba(34, 211, 238, 0.6);
        }
        .gradient-border {
            background: linear-gradient(90deg, #ec4899, #8b5cf6, #22d3ee);
            padding: 2px;
            border-radius: 1rem;
        }
        .inner-card {
            background: #0f0a24;
            border-radius: 0.9rem;
        }
    </style>
</head>
<body class="text-white min-h-screen flex flex-col justify-between">

    <!-- Live Running Ticker (Forex & Crypto) -->
    <div class="w-full bg-purple-950/80 border-b border-pink-500/30 py-2.5 overflow-hidden whitespace-nowrap text-xs font-mono tracking-wider">
        <div class="inline-block animate-marquee space-x-12">
            <span class="text-yellow-400">⚡ CRYPTO LIVE:</span>
            <span>BTC/USD: <span class="text-emerald-400 font-bold">$67,420.50 ▲</span></span>
            <span>TXC/USD: <span class="text-pink-400 font-bold">$1,000.00 ▬</span></span>
            <span>ETH/USD: <span class="text-cyan-400 font-bold">$3,480.25 ▲</span></span>
            <span>SOL/USD: <span class="text-emerald-400 font-bold">$145.80 ▲</span></span>
            <span class="text-cyan-400">🌐 FOREX LIVE:</span>
            <span>EUR/USD: <span class="text-emerald-400 font-bold">1.0924 ▲</span></span>
            <span>GBP/USD: <span class="text-rose-400 font-bold">1.2712 ▼</span></span>
            <span>USD/JPY: <span class="text-emerald-400 font-bold">156.44 ▲</span></span>
            <span>AUD/USD: <span class="text-rose-400 font-bold">0.6618 ▼</span></span>
        </div>
    </div>

    <!-- Navbar -->
    <nav class="border-b border-purple-900/40 bg-black/40 backdrop-blur-md sticky top-0 z-50 px-6 py-4 flex justify-between items-center">
        <div class="flex items-center space-x-2">
            <span class="heading-font text-3xl font-bold tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-pink-500 via-purple-500 to-cyan-400 neon-text-pink">TrendX</span>
        </div>
        
        <!-- Auth Status Bar Controls -->
        <div class="flex items-center space-x-4">
            <!-- Unauthenticated State View -->
            <div id="loggedOutNav" class="flex items-center space-x-3">
                <button onclick="openAuthModal()" class="text-sm font-semibold hover:text-pink-400 transition">Login / Register</button>
            </div>
            <!-- Authenticated State View -->
            <div id="loggedInNav" class="hidden flex items-center space-x-4">
                <span class="text-sm text-gray-300">Welcome, <span id="userDisplay" class="text-cyan-400 font-bold"></span>!</span>
                <button onclick="handleLogout()" class="bg-rose-600/30 hover:bg-rose-600 border border-rose-500 px-4 py-1.5 rounded-lg text-xs font-semibold transition">
                    Logout
                </button>
            </div>
        </div>
    </nav>

    <!-- Marketing Intro Hero -->
    <header class="max-w-7xl mx-auto px-6 pt-12 pb-6 text-center">
        <div class="gradient-border max-w-3xl mx-auto shadow-2xl shadow-purple-500/10">
            <div class="inner-card p-6 text-left">
                <h3 class="text-pink-400 font-bold text-lg flex items-center gap-2 mb-2">
                    🔥 24-Hour Trial Multiplier Protection
                </h3>
                <p class="text-sm text-gray-300 leading-relaxed">
                    <span class="text-cyan-400 font-bold">No bank account or email required for your first 24 hours!</span> Buy instantly to lock in current positions. Example: Settle 10 coins at $1,000 ($10,000 total obligation). If the asset price hits $5,000 at maturity, your portfolio holds $50,000, while your clearing cost remains locked strictly at the $10,000 purchase-date value.
                </p>
            </div>
        </div>
    </header>

    <!-- Core Grid Workspace -->
    <main class="max-w-7xl mx-auto px-6 py-6 grid md:grid-cols-2 gap-8 w-full items-start">
        
        <!-- Interactive Multi-Asset Trading Panel -->
        <section class="bg-white/5 border border-white/10 rounded-2xl p-6 backdrop-blur-md">
            <h2 class="heading-font text-xl font-bold mb-4 text-pink-400 flex items-center gap-2">
                📊 Deferred Settlement Desk
            </h2>

            <div class="space-y-4">
                <div>
                    <label class="block text-xs font-medium text-gray-400 mb-2">Asset Universe Classification</label>
                    <select id="assetSelect" onchange="updateAssetPrice()" class="w-full bg-black/40 border border-purple-500/30 rounded-xl p-3 text-white focus:outline-none focus:border-pink-500">
                        <option value="1000" data-unit="Coins">Crypto: TrendX Token (TXC) — $1,000.00</option>
                        <option value="67420" data-unit="Coins">Crypto: Bitcoin (BTC) — $67,420.00</option>
                        <option value="3480" data-unit="Coins">Crypto: Ethereum (ETH) — $3,480.00</option>
                        <option value="10000" data-unit="Lots">Forex: EUR/USD Contract — $10,000.00 Base</option>
                        <option value="5000" data-unit="Lots">Forex: GBP/USD Contract — $5,000.00 Base</option>
                    </select>
                </div>

                <div>
                    <label class="block text-xs font-medium text-gray-400 mb-2">Transaction Volume (<span id="unitLabel">Coins</span>)</label>
                    <input id="assetVolume" type="number" value="10" min="1" oninput="runFinancialMath()" class="w-full bg-black/40 border border-purple-500/30 rounded-xl p-3 text-white focus:outline-none focus:border-pink-500">
                </div>

                <!-- Math Engine Yield Preview Summary -->
                <div class="bg-purple-950/40 border border-purple-500/20 rounded-xl p-4 space-y-2">
                    <div class="flex justify-between text-xs text-gray-400">
                        <span>Locked Purchase-Date Rate:</span>
                        <span id="rateDisplay">$1,000.00</span>
                    </div>
                    <div class="flex justify-between text-sm font-semibold border-b border-white/10 pb-2">
                        <span>Total Due at Settle Date:</span>
                        <span id="dueDisplay" class="text-pink-400">$10,000.00</span>
                    </div>
                    <div class="flex justify-between text-xs text-gray-400 pt-1">
                        <span>Projected Value (5y Maturity Forecast):</span>
                        <span id="projectionDisplay" class="text-cyan-400">$50,000.00</span>
                    </div>
                </div>
            </div>

            <button onclick="processOrder()" class="w-full mt-5 bg-gradient-to-r from-pink-500 via-purple-600 to-cyan-500 py-3.5 rounded-xl font-bold tracking-wide uppercase shadow-lg shadow-purple-500/20 hover:scale-[1.01] transition-transform">
                Lock Deferred Contract Position
            </button>
        </section>

        <!-- Profile Verification Channels & Vault Status -->
        <section class="bg-white/5 border border-white/10 rounded-2xl p-6 backdrop-blur-md">
            <div class="flex justify-between items-center mb-4">
                <h2 class="heading-font text-xl font-bold text-cyan-400">🔒 Account Security</h2>
                <span id="graceBadge" class="bg-cyan-500/20 border border-cyan-400 text-cyan-300 text-[10px] px-2.5 py-1 rounded-full uppercase tracking-wider font-bold animate-pulse">
                    24h Sandbox Mode Active
                </span>
            </div>
            
            <p class="text-xs text-gray-400 mb-6">
                Positions are fully operational right now. To maintain custody past the initial 24-hour verification window, finalize your profiles details below.
            </p>

            <form id="vaultDetailsForm" class="space-y-4 opacity-60 pointer-events-none transition-opacity duration-300">
                <div>
                    <label class="block text-xs font-medium text-gray-400 mb-1.5">Direct Communication Hub (Email)</label>
                    <input type="email" placeholder="user@trendx-vault.com" class="w-full bg-black/40 border border-purple-500/20 rounded-xl p-3 text-sm focus:outline-none focus:border-cyan-400">
                </div>
                <div>
                    <label class="block text-xs font-medium text-gray-400 mb-1.5">Maturity Ledger Routing Key (Bank Account Info)</label>
                    <input type="text" placeholder="US48 9900 1234 5678 90" class="w-full bg-black/40 border border-purple-500/20 rounded-xl p-3 text-sm focus:outline-none focus:border-cyan-400">
                </div>
                <button type="button" onclick="alert('Profile configurations updated successfully.')" class="w-full bg-cyan-500/20 hover:bg-cyan-500 border border-cyan-400 text-cyan-300 hover:text-white text-xs font-semibold py-3 rounded-xl transition">
                    Commit Validation Data
                </button>
            </form>
        </section>
    </main>

    <!-- Credentials Authentication Modal Backdrop Overlay -->
    <div id="authOverlay" class="fixed inset-0 bg-black/80 backdrop-blur-md flex items-center justify-center z-50 p-4 transition-opacity">
        <div class="gradient-border max-w-md w-full shadow-2xl">
            <div class="inner-card p-6 md:p-8 relative">
                <h2 id="modalTitle" class="heading-font text-2xl font-bold tracking-tight mb-2 text-transparent bg-clip-text bg-gradient-to-r from-pink-400 to-purple-500">
                    Create Profile Access
                </h2>
                <p class="text-xs text-gray-400 mb-6">Establish a security identity to access the trading platform.</p>
                
                <form onsubmit="submitAuthAction(event)" class="space-y-4">
                    <div>
                        <label class="block text-xs font-semibold text-gray-400 mb-1.5">Username</label>
                        <input id="authUsername" type="text" required placeholder="CryptoKing99" class="w-full bg-black/40 border border-purple-500/30 rounded-xl p-3 text-sm text-white focus:outline-none focus:border-pink-500">
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-gray-400 mb-1.5">Access Password</label>
                        <input id="authPassword" type="password" required placeholder="••••••••" class="w-full bg-black/40 border border-purple-500/30 rounded-xl p-3 text-sm text-white focus:outline-none focus:border-pink-500">
                    </div>
                    <button type="submit" class="w-full mt-2 bg-gradient-to-r from-pink-500 to-purple-600 py-3 rounded-xl font-bold tracking-wide uppercase transition hover:opacity-90">
                        Authorize Terminal Session
                    </button>
                </form>
            </div>
        </div>
    </div>

    <!-- Active Positions Portfolio Display Component -->
    <section class="max-w-7xl mx-auto px-6 pb-12 w-full">
        <h2 class="heading-font text-lg font-bold mb-4 text-purple-400 tracking-wide">💼 Active Custody Positions (24H Vault)</h2>
        <div class="bg-black/40 border border-white/5 rounded-xl overflow-x-auto">
            <table class="w-full text-left border-collapse text-xs">
                <thead>
                    <tr class="border-b border-purple-900/50 bg-purple-950/20 text-gray-400">
                        <th class="p-4">Position Asset</th>
                        <th class="p-4">Volume</th>
                        <th class="p-4">Execution Rate</th>
                        <th class="p-4">Maturity Clearing Cost</th>
                        <th class="p-4">Custody Status</th>
                    </tr>
                </thead>
                <tbody id="portfolioTableBody" class="divide-y divide-white/5 text-gray-300">
                    <tr>
                        <td colspan="5" class="p-4 text-center text-gray-500 italic">No assets currently held in custody. Assign parameters above to execute an initial contract.</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </section>

    <!-- Footer System Context Details -->
    <footer class="w-full text-center py-4 bg-black/20 border-t border-white/5 text-[10px] text-gray-600 font-mono">
        TrendX Engine Pipeline Infrastructure © 2026. Custom Marquee CSS Integration.
    </footer>

    <!-- CSS Animation Logic Core Injection -->
    <style>
        @keyframes marquee {
            0% { transform: translateX(100%); }
            100% { transform: translateX(-100%); }
        }
        .animate-marquee {
            display: inline-block;
            animation: marquee 25s linear infinite;
        }
        .animate-marquee:hover {
            animation-play-state: paused;
        }
    </style>

    <!-- Native Logical Architecture Operations -->
    <script>
        let currentSessionUser = null;

        // Initialize state variables on startup
        window.onload = function() {
            runFinancialMath();
        };

        function openAuthModal() {
            document.getElementById('authOverlay').classList.remove('opacity-0', 'pointer-events-none');
        }

        function closeAuthModal() {
            document.getElementById('authOverlay').classList.add('opacity-0', 'pointer-events-none');
        }

        function submitAuthAction(event) {
            event.preventDefault();
            const userVal = document.getElementById('authUsername').value.trim();
            if(!userVal) return;

            currentSessionUser = userVal;
            
            // UI Adjustments for logged-in profile context
            document.getElementById('userDisplay').innerText = currentSessionUser;
            document.getElementById('loggedOutNav').classList.add('hidden');
            document.getElementById('loggedInNav').classList.remove('hidden');
            
            // Enable the verified info forms on screen
            document.getElementById('vaultDetailsForm').classList.remove('opacity-60', 'pointer-events-none');
            
            closeAuthModal();
        }

        function handleLogout() {
            currentSessionUser = null;
            document.getElementById('loggedOutNav').classList.remove('hidden');
            document.getElementById('loggedInNav').classList.add('hidden');
            
            // Disable verified form context fields
            document.getElementById('vaultDetailsForm').classList.add('opacity-60', 'pointer-events-none');
            openAuthModal();
        }

        function updateAssetPrice() {
            const selector = document.getElementById('assetSelect');
            const selectedOption = selector.options[selector.selectedIndex];
            
            // Update custom labeling parameters
            document.getElementById('unitLabel').innerText = selectedOption.getAttribute('data-unit');
            runFinancialMath();
        }

        function runFinancialMath() {
            const assetCostBase = parseFloat(document.getElementById('assetSelect').value);
            const sizeMultiplier = parseFloat(document.getElementById('assetVolume').value) || 0;
            
            const principalObligation = sizeMultiplier * assetCostBase;
            // Simulated 5x multiplier escalation across long horizon index matching original premise 
            const expectedFutureRate = principalObligation * 5; 

            document.getElementById('rateDisplay').innerText = `$${assetCostBase.toLocaleString()}`;
            document.getElementById('dueDisplay').innerText = `$${principalObligation.toLocaleString(undefined, {minimumFractionDigits: 2})}`;
            document.getElementById('projectionDisplay').innerText = `$${expectedFutureRate.toLocaleString(undefined, {minimumFractionDigits: 2})}`;
        }

        function processOrder() {
            if (!currentSessionUser) {
                alert("⛔ Action Blocked: You must establish or authenticate your Username and Password credential set before launching deferred execution variables!");
                openAuthModal();
                return;
            }

            const selector = document.getElementById('assetSelect');
            const assetLabel = selector.options[selector.selectedIndex].text.split('—')[0];
            const sizeMultiplier = parseFloat(document.getElementById('assetVolume').value) || 0;
            const assetCostBase = parseFloat(selector.value);
            const allocationValue = sizeMultiplier * assetCostBase;

            if(sizeMultiplier <= 0) {
                alert("Please declare a valid operational token quantity amount.");
                return;
            }

            // Append live transaction instance parameters straight to screen data table
            const tableBody = document.getElementById('portfolioTableBody');
            
            // Clear default text filler row if present
            if(tableBody.children.length === 1 && tableBody.children[0].cells.length === 1) {
                tableBody.innerHTML = '';
            }

            const row = document.createElement('tr');
            row.className = "hover:bg-white/5 transition-colors";
            row.innerHTML = `
                <td class="p-4 font-semibold text-white">${assetLabel}</td>
                <td class="p-4 text-cyan-400">${sizeMultiplier}</td>
                <td class="p-4">$${assetCostBase.toLocaleString()}</td>
                <td class="p-4 font-bold text-pink-400">$${allocationValue.toLocaleString()}</td>
                <td class="p-4 text-xs"><span class="bg-emerald-500/20 text-emerald-400 px-2 py-0.5 rounded border border-emerald-500/30 font-semibold">24H Custody active</span></td>
            `;
            tableBody.appendChild(row);

            alert(`🎉 Success! Secured ${sizeMultiplier} allocations. Your purchase cost of $${allocationValue.toLocaleString()} is locked under the 24-Hour Sandbox Custody Rule without needing a bank or email address right now.`);
        }
    </script>
</body>
</html>
