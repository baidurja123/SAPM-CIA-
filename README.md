<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Financial Lifecycle Dashboard - Aarav Sharma</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/apexcharts"></script>
    <style>
        .slider-container {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }
        .kpi-card {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            transition: all 0.3s ease;
        }
        .kpi-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }
        .section-title {
            background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
    </style>
</head>
<body class="bg-gray-50">
    <!-- Main Header -->
    <div class="bg-white shadow-lg">
        <div class="max-w-7xl mx-auto px-4 py-6">
            <h1 class="text-4xl font-bold text-gray-800 mb-2">Financial Lifecycle Dashboard</h1>
            <p class="text-xl text-gray-600">Aarav Sharma's Financial Journey</p>
        </div>
    </div>

    <!-- Age Slider Controller -->
    <div class="slider-container py-8">
        <div class="max-w-7xl mx-auto px-4">
            <div class="bg-white rounded-xl shadow-lg p-6">
                <div class="text-center mb-6">
                    <h2 class="text-2xl font-bold text-gray-800 mb-2">Interactive Age Controller</h2>
                    <p class="text-gray-600">Slide to explore different phases of Aarav's financial journey</p>
                </div>
                
                <div class="relative">
                    <input type="range" id="ageSlider" min="23" max="85" value="23" 
                           class="w-full h-3 bg-gray-200 rounded-lg appearance-none cursor-pointer slider">
                    <div class="flex justify-between text-sm text-gray-600 mt-2">
                        <span>Age 23</span>
                        <span>Age 30 (Goal)</span>
                        <span>Age 60 (Retirement)</span>
                        <span>Age 85</span>
                    </div>
                </div>
                
                <div class="text-center mt-6">
                    <div class="text-5xl font-bold text-indigo-600" id="currentAge">23</div>
                    <div class="text-lg text-gray-600">Current Age</div>
                </div>
            </div>
        </div>
    </div>

    <!-- Section A: Wealth Accumulation Dashboard -->
    <div id="sectionA" class="max-w-7xl mx-auto px-4 py-8">
        <h2 class="text-3xl font-bold section-title mb-8">Wealth Accumulation Phase (Age 23-59)</h2>
        
        <!-- KPI Cards -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
            <div class="kpi-card text-white p-6 rounded-xl">
                <div class="text-sm opacity-80">Projected Portfolio Value</div>
                <div class="text-2xl font-bold" id="portfolioValue">₹2,79,446</div>
                <div class="text-xs opacity-70" id="ageDisplay">at Age 23</div>
            </div>
            
            <div class="kpi-card text-white p-6 rounded-xl">
                <div class="text-sm opacity-80">Time to Primary Goal</div>
                <div class="text-2xl font-bold" id="timeToGoal">7 years</div>
                <div class="text-xs opacity-70">Until age 30</div>
            </div>
            
            <div class="kpi-card text-white p-6 rounded-xl">
                <div class="text-sm opacity-80">Primary Goal Target</div>
                <div class="text-2xl font-bold">₹60,00,000</div>
                <div class="text-xs opacity-70">Startup Fund</div>
            </div>
            
            <div class="kpi-card text-white p-6 rounded-xl">
                <div class="text-sm opacity-80">Goal Achievement</div>
                <div class="text-2xl font-bold" id="goalProgress">4.7%</div>
                <div class="text-xs opacity-70">Progress made</div>
            </div>
        </div>

        <!-- Charts Row -->
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 mb-8">
            <!-- Goal Progress Gauge -->
            <div class="bg-white rounded-xl shadow-lg p-6">
                <h3 class="text-xl font-bold text-gray-800 mb-4">Goal Progress Gauge</h3>
                <div id="goalGauge"></div>
            </div>
            
            <!-- Asset Allocation -->
            <div class="bg-white rounded-xl shadow-lg p-6">
                <h3 class="text-xl font-bold text-gray-800 mb-4">Strategic Asset Allocation</h3>
                <div id="assetAllocation"></div>
            </div>
        </div>

        <!-- Corpus Growth Chart -->
        <div class="bg-white rounded-xl shadow-lg p-6">
            <h3 class="text-xl font-bold text-gray-800 mb-4">Corpus Growth Projection</h3>
            <div id="corpusGrowth"></div>
        </div>
    </div>

    <!-- Section B: Business Performance Dashboard -->
    <div id="sectionB" class="max-w-7xl mx-auto px-4 py-8" style="display: none;">
        <h2 class="text-3xl font-bold section-title mb-8">Hypothetical Business Performance (Post-Launch)</h2>
        
        <!-- Business KPI Cards -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-8">
            <div class="kpi-card text-white p-6 rounded-xl">
                <div class="text-sm opacity-80">Projected Company Valuation</div>
                <div class="text-2xl font-bold">₹120 Crore</div>
                <div class="text-xs opacity-70">Year 5 Post-Launch</div>
            </div>
            
            <div class="kpi-card text-white p-6 rounded-xl">
                <div class="text-sm opacity-80">Founder's Equity Value</div>
                <div class="text-2xl font-bold">₹30 Crore</div>
                <div class="text-xs opacity-70">25% Ownership</div>
            </div>
        </div>

        <!-- ARR Growth Chart -->
        <div class="bg-white rounded-xl shadow-lg p-6">
            <h3 class="text-xl font-bold text-gray-800 mb-4">Annual Recurring Revenue (ARR) Growth</h3>
            <div id="arrGrowth"></div>
        </div>
    </div>

    <!-- Section C: Retirement Analysis Dashboard -->
    <div id="sectionC" class="max-w-7xl mx-auto px-4 py-8" style="display: none;">
        <h2 class="text-3xl font-bold section-title mb-8">Retirement Phase Analysis (Age 60+)</h2>
        
        <!-- Retirement KPI Cards -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
            <div class="kpi-card text-white p-6 rounded-xl">
                <div class="text-sm opacity-80">Corpus at Retirement</div>
                <div class="text-2xl font-bold">₹21.49 Crore</div>
                <div class="text-xs opacity-70">At age 60</div>
            </div>
            
            <div class="kpi-card text-white p-6 rounded-xl">
                <div class="text-sm opacity-80">Annual Withdrawal</div>
                <div class="text-2xl font-bold">₹66.35 Lakhs</div>
                <div class="text-xs opacity-70">Initial amount</div>
            </div>
            
            <div class="kpi-card text-white p-6 rounded-xl">
                <div class="text-sm opacity-80">Withdrawal Rate</div>
                <div class="text-2xl font-bold">3.08%</div>
                <div class="text-xs opacity-70">Initial rate</div>
            </div>
            
            <div class="kpi-card text-white p-6 rounded-xl">
                <div class="text-sm opacity-80">Sustainability Status</div>
                <div class="text-2xl font-bold">Sustainable</div>
                <div class="text-xs opacity-70">Below 4% rule</div>
            </div>
        </div>

        <!-- Corpus Drawdown Chart -->
        <div class="bg-white rounded-xl shadow-lg p-6">
            <h3 class="text-xl font-bold text-gray-800 mb-4">Retirement Corpus Drawdown</h3>
            <div id="corpusDrawdown"></div>
        </div>
    </div>

    <script>
        // Data Sets
        const accumulationData = [
            { age: 23, corpus: 279446 },
            { age: 24, corpus: 947335 },
            { age: 25, corpus: 1781062 },
            { age: 26, corpus: 2764436 },
            { age: 27, corpus: 3920809 },
            { age: 28, corpus: 5277596 },
            { age: 29, corpus: 6867060 }
        ];

        const businessData = [
            { year: 1, arr: 1500000, valuation: 10500000, equity: 7350000 },
            { year: 2, arr: 5000000, valuation: 35000000, equity: 24500000 },
            { year: 3, arr: 15000000, valuation: 120000000, equity: 48000000 },
            { year: 4, arr: 50000000, valuation: 500000000, equity: 175000000 },
            { year: 5, arr: 120000000, valuation: 1200000000, equity: 300000000 }
        ];

        const retirementData = [
            { age: 60, corpus: 214982835 },
            { age: 65, corpus: 204300000 },
            { age: 70, corpus: 189800000 },
            { age: 75, corpus: 169500000 },
            { age: 80, corpus: 139800000 },
            { age: 85, corpus: 95000000 }
        ];

        // Chart instances
        let goalGaugeChart, assetAllocationChart, corpusGrowthChart, arrGrowthChart, corpusDrawdownChart;

        // Initialize charts
        function initializeCharts() {
            // Goal Progress Gauge
            const goalGaugeOptions = {
                series: [4.7],
                chart: { type: 'radialBar', height: 350 },
                plotOptions: {
                    radialBar: {
                        hollow: { size: '60%' },
                        dataLabels: {
                            name: { fontSize: '22px' },
                            value: { fontSize: '16px', formatter: val => `${val}%` },
                            total: { show: true, label: 'Progress', formatter: () => '4.7%' }
                        }
                    }
                },
                labels: ['Goal Progress'],
                colors: ['#4f46e5']
            };
            goalGaugeChart = new ApexCharts(document.querySelector("#goalGauge"), goalGaugeOptions);
            goalGaugeChart.render();

            // Asset Allocation
            const assetAllocationOptions = {
                series: [75, 20, 5],
                chart: { type: 'donut', height: 350 },
                labels: ['Equity', 'Debt', 'Gold'],
                colors: ['#10b981', '#f59e0b', '#ef4444'],
                legend: { position: 'bottom' }
            };
            assetAllocationChart = new ApexCharts(document.querySelector("#assetAllocation"), assetAllocationOptions);
            assetAllocationChart.render();

            // Corpus Growth
            const corpusGrowthOptions = {
                series: [{
                    name: 'Projected Corpus',
                    data: accumulationData.map(d => ({ x: d.age, y: d.corpus }))
                }],
                chart: { type: 'line', height: 400 },
                xaxis: { title: { text: 'Age' } },
                yaxis: { 
                    title: { text: 'Corpus (₹)' },
                    labels: { formatter: val => `₹${(val/100000).toFixed(1)}L` }
                },
                annotations: {
                    yaxis: [{
                        y: 6000000,
                        borderColor: '#ef4444',
                        label: { text: 'Goal: ₹60L', style: { color: '#fff', background: '#ef4444' } }
                    }]
                },
                colors: ['#4f46e5']
            };
            corpusGrowthChart = new ApexCharts(document.querySelector("#corpusGrowth"), corpusGrowthOptions);
            corpusGrowthChart.render();

            // ARR Growth
            const arrGrowthOptions = {
                series: [{
                    name: 'ARR',
                    data: businessData.map(d => ({ x: `Year ${d.year}`, y: d.arr }))
                }],
                chart: { type: 'bar', height: 400 },
                yaxis: { 
                    title: { text: 'ARR (₹)' },
                    labels: { formatter: val => `₹${(val/10000000).toFixed(1)}Cr` }
                },
                colors: ['#10b981']
            };
            arrGrowthChart = new ApexCharts(document.querySelector("#arrGrowth"), arrGrowthOptions);
            arrGrowthChart.render();

            // Corpus Drawdown
            const corpusDrawdownOptions = {
                series: [{
                    name: 'Remaining Corpus',
                    data: retirementData.map(d => ({ x: d.age, y: d.corpus }))
                }],
                chart: { type: 'line', height: 400 },
                xaxis: { title: { text: 'Age' } },
                yaxis: { 
                    title: { text: 'Corpus (₹)' },
                    labels: { formatter: val => `₹${(val/10000000).toFixed(1)}Cr` }
                },
                colors: ['#ef4444']
            };
            corpusDrawdownChart = new ApexCharts(document.querySelector("#corpusDrawdown"), corpusDrawdownOptions);
            corpusDrawdownChart.render();
        }

        // Format currency
        function formatCurrency(amount) {
            if (amount >= 10000000) {
                return `₹${(amount / 10000000).toFixed(2)} Crore`;
            } else if (amount >= 100000) {
                return `₹${(amount / 100000).toFixed(2)} Lakhs`;
            } else {
                return `₹${amount.toLocaleString('en-IN')}`;
            }
        }

        // Interpolate value for given age
        function interpolateValue(age, dataArray, ageKey = 'age', valueKey = 'corpus') {
            if (age <= dataArray[0][ageKey]) return dataArray[0][valueKey];
            if (age >= dataArray[dataArray.length - 1][ageKey]) return dataArray[dataArray.length - 1][valueKey];
            
            for (let i = 0; i < dataArray.length - 1; i++) {
                if (age >= dataArray[i][ageKey] && age <= dataArray[i + 1][ageKey]) {
                    const ratio = (age - dataArray[i][ageKey]) / (dataArray[i + 1][ageKey] - dataArray[i][ageKey]);
                    return dataArray[i][valueKey] + ratio * (dataArray[i + 1][valueKey] - dataArray[i][valueKey]);
                }
            }
            return dataArray[0][valueKey];
        }

        // Update dashboard based on age
        function updateDashboard(age) {
            document.getElementById('currentAge').textContent = age;
            
            const sectionA = document.getElementById('sectionA');
            const sectionB = document.getElementById('sectionB');
            const sectionC = document.getElementById('sectionC');

            if (age >= 60) {
                // Retirement Phase
                sectionA.style.display = 'none';
                sectionB.style.display = 'none';
                sectionC.style.display = 'block';
                
                const remainingCorpus = interpolateValue(age, retirementData);
                document.getElementById('portfolioValue').textContent = formatCurrency(remainingCorpus);
                document.getElementById('ageDisplay').textContent = `at Age ${age}`;
            } else {
                // Accumulation Phase
                sectionA.style.display = 'block';
                sectionC.style.display = 'none';
                
                let portfolioValue;
                if (age <= 29) {
                    portfolioValue = interpolateValue(age, accumulationData);
                } else if (age >= 35) {
                    // Interpolate from retirement data backwards
                    const retirementAt60 = 214982835;
                    const yearsToRetirement = 60 - age;
                    const growthRate = 0.12; // Assumed 12% growth
                    portfolioValue = retirementAt60 / Math.pow(1 + growthRate, yearsToRetirement);
                } else {
                    // Gap years 30-34
                    portfolioValue = 6867060; // Last known value
                }
                
                document.getElementById('portfolioValue').textContent = formatCurrency(portfolioValue);
                document.getElementById('ageDisplay').textContent = `at Age ${age}`;
                
                const yearsToGoal = Math.max(0, 30 - age);
                document.getElementById('timeToGoal').textContent = yearsToGoal > 0 ? `${yearsToGoal} years` : 'Achieved!';
                
                const goalProgress = Math.min(100, (portfolioValue / 6000000) * 100);
                document.getElementById('goalProgress').textContent = `${goalProgress.toFixed(1)}%`;
                
                // Update gauge chart
                if (goalGaugeChart) {
                    goalGaugeChart.updateSeries([goalProgress]);
                }
                
                // Show business section if age >= 30
                if (age >= 30) {
                    sectionB.style.display = 'block';
                } else {
                    sectionB.style.display = 'none';
                }
            }
        }

        // Initialize
        document.addEventListener('DOMContentLoaded', function() {
            const ageSlider = document.getElementById('ageSlider');
            
            // Initialize charts
            setTimeout(initializeCharts, 100);
            
            // Update dashboard when slider changes
            ageSlider.addEventListener('input', function() {
                updateDashboard(parseInt(this.value));
            });
            
            // Initial update
            updateDashboard(23);
        });
    </script>
</body>
</html>
function showTime() {
	document.getElementById('currentTime').innerHTML = new Date().toUTCString();
}
showTime();
setInterval(function () {
	showTime();
}, 1000);
body{
  padding: 25px;
}
.title {
	color: #5C6AC4;
}
