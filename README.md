<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TrendX | Next-Gen Crypto Investing</title>
    <!-- Tailwind CSS for modern layout -->
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Poppins:wght@300;400;600&display=swap');
        
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #0f0c1b 0%, #161034 50%, #06040a 100%);
        }
        .heading-font {
            font-family: 'Orbitron', sans-serif;
        }
        .neon-glow {
            text-shadow: 0 0 10px rgba(236, 72, 153, 0.7), 0 0 20px rgba(139, 92, 246, 0.5);
        }
        .gradient-border {
            background: linear-gradient(90deg, #ec4899, #8b5cf6, #3b82f6);
            padding: 2px;
            border-radius: 1rem;
        }
        .inner-card {
            background: #110c26;
            border-radius: 0.9rem;
        }
    </style>
</head>
<body class="text-white min-h-screen">

    <!-- Navbar -->
    <nav class="border-b border-purple-900/40 bg-black/30 backdrop-blur-md sticky top-0 z-50 px-6 py-4 flex justify-between items-center">
        <div class="flex items-center space-x-2">
            <span class="heading-font text-3xl font-bold tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-pink-500 via-purple-500 to-cyan-400 neon-glow">TrendX</span>
        </div>
        <div class="hidden md:flex space-x-8 font-medium">
            <a href="#home" class="hover:text-pink-400 transition">Market</a>
            <a href="#invest" class="hover:text-purple-400 transition">Deferred Pay</a>
            <a href="#auth" class="text-cyan-400 hover:underline transition">Account Verification</a>
        </div>
        <button onclick="scrollToSection('invest')" class="bg-gradient-to-r from-pink-500 to-purple-600 px-6 py-2 rounded-full font-semibold shadow-lg shadow-pink-500/20 hover:scale-105 transition-transform">
            Trade Now
        </button>
    </nav>

    <!-- Hero / Promotional Banner Section -->
    <header id="home" class="max-w-7xl mx-auto px-6 pt-16 pb-12 text-center">
        <span class="bg-purple-900/50 text-pink-400 border border-pink-500/30 px-4 py-1.5 rounded-full text-sm font-semibold tracking-wide uppercase">
            Exclusive Launch Offer
        </span>
        <h1 class="heading-font text-4xl md:text-6xl font-extrabold tracking-tight mt-6 leading-tight">
            Buy Crypto Today.<br>Pay Only At <span class="text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 to-purple-500">Maturity.</span>
        </h1>
        <p class="mt-6 text-gray-400 max-w-2xl mx-auto text-lg">
            Lock in current market rates right now. Secure your coins today, watch your portfolio grow, and settle your original balance at the end of the term.
        </p>

        <!-- Dynamic Maturity Explanation Card -->
        <div class="gradient-border max-w-3xl mx-auto mt-10 shadow-2xl shadow-purple-500/10">
            <div class="inner-card p-6 md:p-8 text-left">
                <h3 class="text-pink-400 font-bold text-xl flex items-center gap-2">
                    💡 How It Works (Example Case)
                </h3>
                <p class="text-gray-300 mt-3 leading-relaxed">
                    If you buy <span class="text-white font-bold">10 coins</span> at the rate of <span class="text-cyan-400 font-bold">$1,000 per coin</span>, your locked price is <span class="text-white font-bold">$10,000</span>. After 5 years, if the coin rate surges above <span class="text-emerald-400 font-bold">$5,000</span>, your final asset value becomes <span class="text-emerald-400 font-bold">$50,000</span>—but you <span class="underline decoration-pink-500 decoration-2">only ever pay the initial $10,000</span> upon maturity date!
                </p>
            </div>
        </div>
    </header>

    <!-- Main Workspace (Investment & Verification) -->
    <main class="max-w-7xl mx-auto px-6 py-12 grid md:grid-cols-2 gap-12">
        
        <!-- Left Column: Buy / Sell Portal & Calculator -->
        <section id="invest" class="bg-white/5 border border-white/10 rounded-2xl p-6 backdrop-blur-md flex flex-col justify-between">
            <div>
                <div class="flex border-b border-white/10 mb-6">
                    <button id="buyTab" onclick="switchAction('buy')" class="w-1/2 py-3 text-center font-bold text-lg border-b-2 border-pink-500 text-pink-400">BUY COINS</button>
                    <button id="sellTab" onclick="switchAction('sell')" class="w-1/2 py-3 text-center font-bold text-lg border-b-2 border-transparent text-gray-400 hover:text-white">SELL COINS</button>
                </div>

                <div class="space-y-4">
                    <div>
                        <label class="block text-sm font-medium text-gray-400 mb-2">Select Cryptocurrency Asset</label>
                        <select class="w-full bg-black/40 border border-purple-500/30 rounded-xl p-3 text-white focus:outline-none focus:border-pink-500">
                            <option value="TXC">TrendX Coin (TXC) — $1,000.00</option>
                            <option value="BTC">Bitcoin (BTC) — $65,000.00</option>
                            <option value="ETH">Ethereum (ETH) — $3,500.00</option>
                        </select>
                    </div>

                    <div>
                        <label class="block text-sm font-medium text-gray-400 mb-2">Quantity (Number of Coins)</label>
                        <input id="coinAmount" type="number" value="10" min="1" oninput="calculateReturns()" class="w-full bg-black/40 border border-purple-500/30 rounded-xl p-3 text-white focus:outline-none focus:border-pink-500">
                    </div>

                    <!-- Realtime Math Display Box -->
                    <div class="bg-purple-950/40 border border-purple-500/20 rounded-xl p-4 mt-6 space-y-2">
                        <div class="flex justify-between text-sm text-gray-400">
                            <span>Locked Rate (Per Coin):</span>
                            <span id="ratePerCoin">$1,000.00</span>
                        </div>
                        <div class="flex justify-between text-base font-semibold border-b border-white/10 pb-2">
                            <span>Total Due at Maturity:</span>
                            <span id="totalDue" class="text-pink-400">$10,000.00</span>
                        </div>
                        <div class="flex justify-between text-xs text-gray-400 pt-1">
                            <span>Projected Value (Based on 5-Year Trend):</span>
                            <span id="projectedValue" class="text-emerald-400">$50,000.00</span>
                        </div>
                    </div>
                </div>
            </div>

            <button onclick="triggerTransaction()" class="w-full mt-6 bg-gradient-to-r from-pink-500 via-purple-600 to-cyan-500 py-4 rounded-xl font-bold tracking-wide uppercase shadow-lg shadow-purple-500/20 hover:opacity-90 transition">
                <span id="actionBtnText">Execute Deferred Buy</span>
            </button>
        </section>

        <!-- Right Column: Verification & Security (Email, OTP, Bank Account) -->
        <section id="auth" class="bg-white/5 border border-white/10 rounded-2xl p-6 backdrop-blur-md">
            <h2 class="heading-font text-2xl font-bold mb-2 text-cyan-400 flex items-center gap-2">
                🔒 Secure Verification Gateway
            </h2>
            <p class="text-sm text-gray-400 mb-6">To safely execute deferred contracts, please link your profile credentials and payment authorization routing details.</p>

            <form onsubmit="handleVerification(event)" class="space-y-5">
                <!-- Email Input & Verification Trigger -->
                <div>
                    <label class="block text-sm font-medium text-gray-400 mb-2">Email Address</label>
                    <div class="flex gap-2">
                        <input id="email" type="email" required placeholder="name@example.com" class="w-full bg-black/40 border border-purple-500/30 rounded-xl p-3 text-white focus:outline-none focus:border-pink-500">
                        <button type="button" onclick="sendOTP()" class="bg-purple-600/50 hover:bg-purple-600 border border-purple-500 text-sm font-semibold px-4 rounded-xl whitespace-nowrap transition">
                            Get OTP
                        </button>
                    </div>
                    <span id="otpStatus" class="text-xs text-emerald-400 mt-1 hidden">✓ Test OTP simulation dispatched! Enter '123456'</span>
                </div>

                <!-- OTP Entry -->
                <div>
                    <label class="block text-sm font-medium text-gray-400 mb-2">One-Time Password (OTP)</label>
                    <input id="otp" type="text" required maxlength="6" placeholder="------" class="w-full bg-black/40 border border-purple-500/30 rounded-xl p-3 tracking-widest font-mono text-center text-white focus:outline-none focus:border-pink-500">
                </div>

                <!-- Banking Integration -->
                <div>
                    <label class="block text-sm font-medium text-gray-400 mb-2">Maturity Clearing Bank Account (IBAN / Routing)</label>
                    <div class="relative">
                        <input id="bank" type="text" required placeholder="US99 1234 5678 9012 3456" class="w-full bg-black/40 border border-purple-500/30 rounded-xl p-3 text-white focus:outline-none focus:border-pink-500 pl-10">
                        <span class="absolute left-3 top-3.5 text-gray-500">🏦</span>
                    </div>
                    <p class="text-[11px] text-gray-500 mt-1.5">No immediate charges apply. Account details are secured via encryption and evaluated strictly for contract maturity verification.</p>
                </div>

                <!-- Form Submit -->
                <button type="submit" class="w-full bg-emerald-500 hover:bg-emerald-600 py-3.5 rounded-xl font-semibold transition tracking-wide mt-4">
                    Verify & Authenticate Profile
                </button>
            </form>
        </section>
    </main>

    <!-- Footer Dynamic Alert Context -->
    <footer class="max-w-7xl mx-auto px-6 py-8 border-t border-white/10 text-center text-xs text-gray-500">
        TrendX Crypto Forward Clearing House Portfolio Engine © 2026. Simulation purposes only.
    </footer>

    <!-- Simple Logical System Layer -->
    <script>
        let currentMode = 'buy';
        let isVerified = false;

        function switchAction(mode) {
            currentMode = mode;
            const buyTab = document.getElementById('buyTab');
            const sellTab = document.getElementById('sellTab');
            const actionBtnText = document.getElementById('actionBtnText');

            if(mode === 'buy') {
                buyTab.className = "w-1/2 py-3 text-center font-bold text-lg border-b-2 border-pink-500 text-pink-400";
                sellTab.className = "w-1/2 py-3 text-center font-bold text-lg border-b-2 border-transparent text-gray-400 hover:text-white";
                actionBtnText.innerText = "Execute Deferred Buy";
            } else {
                sellTab.className = "w-1/2 py-3 text-center font-bold text-lg border-b-2 border-cyan-400 text-cyan-400";
                buyTab.className = "w-1/2 py-3 text-center font-bold text-lg border-b-2 border-transparent text-gray-400 hover:text-white";
                actionBtnText.innerText = "Execute Instant Sell Order";
            }
            calculateReturns();
        }

        function calculateReturns() {
            const coins = parseFloat(document.getElementById('coinAmount').value) || 0;
            const pricePerCoin = 1000; 
            const estimatedFuturePrice = 5000; 

            const totalDue = coins * pricePerCoin;
            const futureValue = coins * estimatedFuturePrice;

            document.getElementById('totalDue').innerText = `$${totalDue.toLocaleString(undefined, {minimumFractionDigits: 2})}`;
            document.getElementById('projectedValue').innerText = `$${futureValue.toLocaleString(undefined, {minimumFractionDigits: 2})}`;
        }

        function sendOTP() {
            const emailInput = document.getElementById('email').value;
            if(!emailInput) {
                alert("Please type your email address first!");
                return;
            }
            document.getElementById('otpStatus').classList.remove('hidden');
        }

        function handleVerification(event) {
            event.preventDefault();
            const otp = document.getElementById('otp').value;
            
            if(otp === "123456") {
                isVerified = true;
                alert("✓ Verification Successful! Bank and Identity channels successfully mapped.");
            } else {
                alert("Verification Simulation: Try using the simulated OTP '123456'.");
            }
        }

        function triggerTransaction() {
            if(!isVerified) {
                alert("🔒 Order Halted: Please authenticate your Email, input the security OTP, and configure your clearing bank account details on the right panel first!");
                scrollToSection('auth');
                return;
            }
            
            const coins = document.getElementById('coinAmount').value;
            alert(`🎉 Success! Your contract for ${coins} TrendX Coins has been secured. You will settle your balance at the original purchase date valuation upon the contract maturity date.`);
        }

        function scrollToSection(id) {
            document.getElementById(id).scrollIntoView({ behavior: 'smooth' });
        }
    </script>
</body>
</html>
