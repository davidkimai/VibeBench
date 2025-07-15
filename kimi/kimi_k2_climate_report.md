# [Chat Log](https://www.kimi.com/share/d1r9gboonf4p9j7uqasg)

<img width="1894" height="1094" alt="image" src="https://github.com/user-attachments/assets/3e8a105b-dd6f-45b8-87db-c18e2c255460" />

# Prompt

## Design a deep-dive report on climate change. Let users explore animated maps, select regions, toggle between temperature/CO2/sea level charts, and reveal key findings by clicking sections. Vibe: scientific but visually immersive, blue/green palette, smooth transitions. Use HTML, CSS, JS, and D3 or Chart.js.


# Kimi

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Climate Change Deep-Dive Report</title>
    <script src="https://d3js.org/d3.v7.min.js"></script>
    <script src="https://d3js.org/topojson.v3.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        :root {
            --primary-blue: #0a3d62;
            --secondary-blue: #3c6382;
            --accent-teal: #38ada9;
            --light-teal: #78e08f;
            --background: #f5f6fa;
            --text-dark: #2c3e50;
            --text-light: #f5f6fa;
            --warning: #e58e26;
            --danger: #b71540;
            --gradient-1: linear-gradient(135deg, #0a3d62, #3c6382);
            --gradient-2: linear-gradient(135deg, #38ada9, #78e08f);
            --shadow: 0 10px 30px rgba(10, 61, 98, 0.15);
            --shadow-hover: 0 15px 40px rgba(10, 61, 98, 0.25);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            color: var(--text-dark);
            line-height: 1.6;
            overflow-x: hidden;
            scroll-behavior: smooth;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            background: var(--gradient-1);
            color: var(--text-light);
            padding: 60px 0;
            text-align: center;
            border-radius: 0 0 30px 30px;
            box-shadow: var(--shadow);
            margin-bottom: 40px;
            position: relative;
            overflow: hidden;
        }

        header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="20" cy="20" r="1" fill="rgba(255,255,255,0.1)"/><circle cx="80" cy="40" r="1" fill="rgba(255,255,255,0.1)"/><circle cx="40" cy="80" r="1" fill="rgba(255,255,255,0.1)"/><circle cx="90" cy="90" r="1" fill="rgba(255,255,255,0.1)"/></svg>');
            animation: float 20s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(180deg); }
        }

        h1 {
            font-size: 3.5rem;
            margin-bottom: 15px;
            background: linear-gradient(45deg, #fff, #78e08f);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            position: relative;
            z-index: 1;
        }

        .subtitle {
            font-size: 1.3rem;
            opacity: 0.9;
            font-weight: 300;
            position: relative;
            z-index: 1;
        }

        .controls {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            flex-wrap: wrap;
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            padding: 25px;
            border-radius: 20px;
            box-shadow: var(--shadow);
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: all 0.3s ease;
        }

        .controls:hover {
            box-shadow: var(--shadow-hover);
            transform: translateY(-2px);
        }

        .data-selector {
            display: flex;
            gap: 15px;
        }

        .btn {
            padding: 12px 24px;
            border: none;
            border-radius: 50px;
            background: var(--gradient-2);
            color: white;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
            font-size: 0.9rem;
            letter-spacing: 0.5px;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.5s;
        }

        .btn:hover::before {
            left: 100%;
        }

        .btn:hover {
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 8px 25px rgba(56, 173, 169, 0.4);
        }

        .btn.active {
            background: var(--gradient-1);
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(10, 61, 98, 0.4);
        }

        .btn.active::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 50%;
            transform: translateX(-50%);
            width: 60%;
            height: 2px;
            background: var(--light-teal);
            border-radius: 2px;
        }

        .map-container {
            position: relative;
            height: 500px;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: var(--shadow);
            background: linear-gradient(135deg, #e3f2fd, #bbdefb);
            border: 1px solid rgba(255, 255, 255, 0.3);
            transition: all 0.3s ease;
        }

        .map-container:hover {
            box-shadow: var(--shadow-hover);
            transform: translateY(-5px);
        }

        .map {
            width: 100%;
            height: 100%;
        }

        .country {
            fill: #a7c5eb;
            stroke: #fff;
            stroke-width: 0.5px;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            cursor: pointer;
        }

        .country:hover {
            fill: var(--accent-teal);
            stroke-width: 1.5px;
            filter: brightness(1.1);
        }

        .country.selected {
            fill: var(--primary-blue);
            stroke-width: 2px;
            stroke: var(--light-teal);
            filter: drop-shadow(0 0 10px rgba(56, 173, 169, 0.5));
        }

        .tooltip {
            position: absolute;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            padding: 15px 20px;
            border-radius: 15px;
            pointer-events: none;
            font-size: 0.9rem;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            opacity: 0;
            transition: all 0.3s ease;
            z-index: 1000;
        }

        .tooltip strong {
            color: var(--primary-blue);
            font-size: 1rem;
        }

        .chart-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin-top: 40px;
        }

        .chart-card {
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            border-radius: 25px;
            padding: 30px;
            box-shadow: var(--shadow);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .chart-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: var(--gradient-2);
            border-radius: 25px 25px 0 0;
        }

        .chart-card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: var(--shadow-hover);
        }

        .chart-title {
            font-size: 1.3rem;
            margin-bottom: 20px;
            color: var(--primary-blue);
            font-weight: 700;
            position: relative;
        }

        .chart-title::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 50px;
            height: 2px;
            background: var(--accent-teal);
            border-radius: 2px;
        }

        .chart-wrapper {
            height: 300px;
            position: relative;
        }

        .key-findings {
            margin-top: 60px;
            background: var(--gradient-1);
            color: var(--text-light);
            padding: 60px 40px;
            border-radius: 30px;
            box-shadow: var(--shadow);
            position: relative;
            overflow: hidden;
        }

        .key-findings::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(120, 224, 143, 0.1) 0%, transparent 70%);
            animation: pulse 4s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); opacity: 0.5; }
            50% { transform: scale(1.1); opacity: 0.8; }
        }

        .key-findings h2 {
            margin-bottom: 30px;
            font-size: 2.2rem;
            position: relative;
            z-index: 1;
            text-align: center;
        }

        .findings-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 30px;
        }

        .finding-card {
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            cursor: pointer;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .finding-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1), transparent);
            transition: left 0.5s;
        }

        .finding-card:hover::before {
            left: 100%;
        }

        .finding-card:hover {
            transform: translateY(-8px) scale(1.02);
            background: rgba(255, 255, 255, 0.25);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
        }

        .finding-card::after {
            content: '';
            position: absolute;
            top: 10px;
            right: 10px;
            width: 8px;
            height: 8px;
            background: var(--light-teal);
            border-radius: 50%;
            opacity: 0.7;
        }

        .finding-title {
            font-size: 1.3rem;
            margin-bottom: 15px;
            color: var(--light-teal);
            font-weight: 700;
            position: relative;
            z-index: 1;
        }

        .finding-summary {
            font-size: 1rem;
            opacity: 0.9;
            position: relative;
            z-index: 1;
            line-height: 1.7;
        }

        .finding-details {
            height: 0;
            overflow: hidden;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            opacity: 0;
            margin-top: 0;
            font-size: 0.95rem;
            line-height: 1.8;
        }

        .finding-details p {
            margin-top: 15px;
            padding-top: 15px;
            border-top: 1px solid rgba(255, 255, 255, 0.2);
        }

        .finding-card.active .finding-details {
            height: auto;
            opacity: 1;
            margin-top: 15px;
        }

        .finding-card.active {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-5px);
        }

        .legend {
            position: absolute;
            bottom: 20px;
            right: 20px;
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            padding: 15px;
            border-radius: 15px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: all 0.3s ease;
        }

        .legend:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.15);
        }

        .legend-item {
            display: flex;
            align-items: center;
            margin-bottom: 8px;
            transition: all 0.2s ease;
        }

        .legend-item:hover {
            transform: translateX(5px);
        }

        .legend-color {
            width: 20px;
            height: 20px;
            margin-right: 10px;
            border-radius: 50%;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }

        .loading {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 1.2rem;
            color: var(--primary-blue);
            background: rgba(255, 255, 255, 0.9);
            padding: 20px 30px;
            border-radius: 15px;
            box-shadow: var(--shadow);
            display: none;
        }

        .loading::after {
            content: '';
            display: inline-block;
            width: 20px;
            height: 20px;
            margin-left: 10px;
            border: 2px solid var(--accent-teal);
            border-radius: 50%;
            border-top-color: transparent;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        .year-slider {
            width: 100%;
            margin: 20px 0;
            -webkit-appearance: none;
            height: 8px;
            border-radius: 5px;
            background: linear-gradient(to right, var(--accent-teal), var(--warning), var(--danger));
            outline: none;
            opacity: 0.8;
            transition: opacity 0.2s;
        }

        .year-slider:hover {
            opacity: 1;
        }

        .year-slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: white;
            cursor: pointer;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
        }

        .year-slider::-moz-range-thumb {
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: white;
            cursor: pointer;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
        }

        .year-display {
            text-align: center;
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--primary-blue);
            margin: 10px 0;
        }

        @media (max-width: 768px) {
            .chart-container {
                grid-template-columns: 1fr;
            }
            
            .controls {
                flex-direction: column;
                align-items: flex-start;
                gap: 15px;
            }
            
            h1 {
                font-size: 2.5rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <h1>Climate Change Deep-Dive Report</h1>
            <p class="subtitle">Interactive exploration of global climate trends</p>
        </div>
    </header>

    <div class="container">
        <div class="controls">
            <div class="data-selector">
                <button class="btn active" data-type="temperature">Temperature</button>
                <button class="btn" data-type="co2">CO₂ Levels</button>
                <button class="btn" data-type="seaLevel">Sea Level</button>
            </div>
            <div>
                <input type="range" min="1970" max="2023" value="2023" class="year-slider" id="yearSlider">
                <div class="year-display" id="yearDisplay">2023</div>
            </div>
        </div>

        <div class="map-container">
            <div class="map" id="worldMap"></div>
            <div class="tooltip" id="mapTooltip"></div>
            <div class="loading" id="mapLoading">Loading map data...</div>
            <div class="legend" id="mapLegend">
                <div class="legend-item">
                    <div class="legend-color" style="background-color: #78e08f"></div>
                    <span>Low</span>
                </div>
                <div class="legend-item">
                    <div class="legend-color" style="background-color: #38ada9"></div>
                    <span>Medium</span>
                </div>
                <div class="legend-item">
                    <div class="legend-color" style="background-color: #e58e26"></div>
                    <span>High</span>
                </div>
                <div class="legend-item">
                    <div class="legend-color" style="background-color: #b71540"></div>
                    <span>Extreme</span>
                </div>
            </div>
        </div>

        <div class="chart-container">
            <div class="chart-card">
                <h3 class="chart-title">Global Trend Over Time</h3>
                <div class="chart-wrapper">
                    <canvas id="globalTrendChart"></canvas>
                </div>
            </div>
            <div class="chart-card">
                <h3 class="chart-title">Regional Comparison</h3>
                <div class="chart-wrapper">
                    <canvas id="regionalChart"></canvas>
                </div>
            </div>
        </div>

        <div class="key-findings">
            <h2>Key Findings</h2>
            <div class="findings-grid">
                <div class="finding-card">
                    <h3 class="finding-title">Accelerating Temperature Rise</h3>
                    <p class="finding-summary">Global average temperature has risen by 1.1°C since pre-industrial times.</p>
                    <div class="finding-details">
                        <p>The rate of warming has accelerated significantly in recent decades, with the last decade being the warmest on record. Most of this warming has occurred since 1975, at a rate of approximately 0.15-0.20°C per decade. This acceleration is primarily driven by increased greenhouse gas emissions from human activities.</p>
                        <p>Without significant mitigation, global temperatures are projected to rise by 2.7-3.1°C above pre-industrial levels by 2100 based on current policies.</p>
                    </div>
                </div>
                
                <div class="finding-card">
                    <h3 class="finding-title">CO₂ Concentration Milestone</h3>
                    <p class="finding-summary">Atmospheric CO₂ levels have surpassed 420 ppm, a 50% increase since pre-industrial times.</p>
                    <div class="finding-details">
                        <p>CO₂ concentrations have increased from approximately 280 ppm in the pre-industrial era to over 420 ppm today. This represents the highest level in at least 3 million years. The annual growth rate has accelerated from about 0.8 ppm per year in the 1960s to over 2.3 ppm per year in the last decade.</p>
                        <p>Global carbon emissions from fossil fuels reached a record high of 36.8 billion tonnes of CO₂ in 2023.</p>
                    </div>
                </div>
                
                <div class="finding-card">
                    <h3 class="finding-title">Sea Level Acceleration</h3>
                    <p class="finding-summary">Global sea level is rising 3.7 mm per year, accelerating from 1.4 mm/year last century.</p>
                    <div class="finding-details">
                        <p>Sea level rise has accelerated from approximately 1.4 mm per year throughout most of the 20th century to 3.7 mm per year from 2006-2015. The acceleration is primarily due to increased melting of land ice (Greenland and Antarctica) and thermal expansion of warming ocean water.</p>
                        <p>Projections indicate sea levels could rise by 0.44-0.76 m by 2100 under moderate warming scenarios, and up to 2 m under high emission scenarios, threatening hundreds of millions of people in coastal areas.</p>
                    </div>
                </div>
                
                <div class="finding-card">
                    <h3 class="finding-title">Regional Disparities</h3>
                    <p class="finding-summary">Arctic regions are warming 3-4 times faster than the global average.</p>
                    <div class="finding-details">
                        <p>The Arctic is experiencing the most rapid warming on Earth, a phenomenon known as Arctic amplification. This has led to significant sea ice loss, permafrost thaw, and ecosystem disruption. In contrast, some regions like the Southern Ocean have warmed more slowly due to ocean circulation patterns.</p>
                        <p>Developing nations and small island states face disproportionate impacts despite contributing the least to historical emissions, highlighting the climate injustice dimension of global warming.</p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Global variables
        let currentDataType = 'temperature';
        let selectedRegion = null;
        let worldMap = null;
        let globalTrendChart = null;
        let regionalChart = null;
        let globalData = {
            temperature: [],
            co2: [],
            seaLevel: []
        };
        let regionalData = {
            temperature: {},
            co2: {},
            seaLevel: {}
        };
        let currentYear = 2023;

        // Initialize the application
        document.addEventListener('DOMContentLoaded', function() {
            initializeData();
            initializeMap();
            initializeCharts();
            setupEventListeners();
        });

        // Generate sample data
        function initializeData() {
            // Global temperature data (anomaly from 1951-1980 average)
            const baseTemp = 14.0;
            for (let year = 1880; year <= 2023; year++) {
                const anomaly = -0.2 + (year - 1880) * 0.008 + Math.sin((year - 1880) * 0.1) * 0.1;
                const adjustedAnomaly = year > 1970 ? anomaly + (year - 1970) * 0.018 : anomaly;
                globalData.temperature.push({
                    year: year,
                    value: baseTemp + adjustedAnomaly
                });
                
                // CO2 data (parts per million)
                const baseCO2 = 280;
                let co2Value;
                if (year < 1950) {
                    co2Value = baseCO2 + (year - 1880) * 0.3;
                } else {
                    co2Value = 310 + (year - 1950) * 1.8 + Math.pow(Math.max(0, year - 2000), 1.5) * 0.05;
                }
                globalData.co2.push({
                    year: year,
                    value: co2Value
                });
                
                // Sea level data (mm above 1993-2008 average)
                let seaLevelValue;
                if (year < 1900) {
                    seaLevelValue = -150 + (year - 1880) * 1.2;
                } else if (year < 1990) {
                    seaLevelValue = -75 + (year - 1900) * 1.5;
                } else {
                    seaLevelValue = (year - 1990) * 3.0 + Math.pow(Math.max(0, year - 2000), 1.8) * 0.2;
                }
                globalData.seaLevel.push({
                    year: year,
                    value: seaLevelValue
                });
            }
            
            // Regional data
            const regions = ['North America', 'Europe', 'Asia', 'Africa', 'South America', 'Oceania', 'Arctic'];
            regions.forEach(region => {
                regionalData.temperature[region] = [];
                regionalData.co2[region] = [];
                regionalData.seaLevel[region] = [];
                
                for (let year = 1970; year <= 2023; year++) {
                    let tempMultiplier = 1.0;
                    if (region === 'Arctic') tempMultiplier = 3.5;
                    if (region === 'Europe') tempMultiplier = 1.2;
                    if (region === 'Oceania') tempMultiplier = 0.9;
                    
                    const globalTemp = globalData.temperature.find(d => d.year === year).value;
                    regionalData.temperature[region].push({
                        year: year,
                        value: globalTemp + (Math.random() - 0.5) * tempMultiplier
                    });
                    
                    const globalCO2 = globalData.co2.find(d => d.year === year).value;
                    regionalData.co2[region].push({
                        year: year,
                        value: globalCO2 + (Math.random() - 0.5) * 5
                    });
                    
                    const globalSea = globalData.seaLevel.find(d => d.year === year).value;
                    let seaMultiplier = 1.0;
                    if (region === 'Oceania') seaMultiplier = 1.3;
                    
                    regionalData.seaLevel[region].push({
                        year: year,
                        value: globalSea * seaMultiplier + (Math.random() - 0.5) * 20
                    });
                }
            });
        }

        // Initialize the world map
        async function initializeMap() {
            document.getElementById('mapLoading').style.display = 'block';
            
            const width = document.getElementById('worldMap').clientWidth;
            const height = 500;
            
            const svg = d3.select('#worldMap')
                .append('svg')
                .attr('width', width)
                .attr('height', height);
            
            const projection = d3.geoNaturalEarth1()
                .scale(width / 6.5)
                .translate([width / 2, height / 2]);
            
            const path = d3.geoPath().projection(projection);
            
            try {
                const response = await fetch('https://cdn.jsdelivr.net/npm/world-atlas@2/countries-110m.json');
                const data = await response.json();
                
                const countries = topojson.feature(data, data.objects.countries);
                
                svg.selectAll('.country')
                    .data(countries.features)
                    .enter()
                    .append('path')
                    .attr('class', 'country')
                    .attr('d', path)
                    .attr('data-name', d => d.properties.name)
                    .on('mouseover', function(event, d) {
                        const tooltip = document.getElementById('mapTooltip');
                        tooltip.style.opacity = 1;
                        tooltip.style.left = (event.pageX + 10) + 'px';
                        tooltip.style.top = (event.pageY - 28) + 'px';
                        
                        const value = getDataForRegion(d.properties.name, currentDataType, currentYear);
                        const unit = getUnitForDataType(currentDataType);
                        
                        tooltip.innerHTML = `
                            <strong>${d.properties.name}</strong><br>
                            ${currentDataType}: ${value.toFixed(2)} ${unit}
                        `;
                    })
                    .on('mouseout', function() {
                        document.getElementById('mapTooltip').style.opacity = 0;
                    })
                    .on('click', function(event, d) {
                        // Toggle selection
                        d3.selectAll('.country').classed('selected', false);
                        if (selectedRegion !== d.properties.name) {
                            d3.select(this).classed('selected', true);
                            selectedRegion = d.properties.name;
                        } else {
                            selectedRegion = null;
                        }
                        updateCharts();
                    });
                
                updateMapColors();
                document.getElementById('mapLoading').style.display = 'none';
                
            } catch (error) {
                console.error('Error loading map data:', error);
                document.getElementById('mapLoading').textContent = 'Error loading map data';
            }
        }

        // Update map colors based on selected data type and year
        function updateMapColors() {
            const colorScale = d3.scaleSequential()
                .domain(getColorDomain())
                .interpolator(d3.interpolateYlOrRd);
            
            d3.selectAll('.country')
                .transition()
                .duration(750)
                .attr('fill', function() {
                    const region = d3.select(this).attr('data-name');
                    const value = getDataForRegion(region, currentDataType, currentYear);
                    return isNaN(value) ? '#ccc' : colorScale(value);
                });
            
            // Update legend
            updateLegend();
        }

        function updateLegend() {
            const legend = document.getElementById('mapLegend');
            const [min, max] = getColorDomain();
            
            legend.innerHTML = `
                <div class="legend-item">
                    <div class="legend-color" style="background-color: ${d3.interpolateYlOrRd(0)}"></div>
                    <span>${min.toFixed(1)} ${getUnitForDataType(currentDataType)}</span>
                </div>
                <div class="legend-item">
                    <div class="legend-color" style="background-color: ${d3.interpolateYlOrRd(0.33)}"></div>
                    <span>${(min + (max - min) * 0.33).toFixed(1)}</span>
                </div>
                <div class="legend-item">
                    <div class="legend-color" style="background-color: ${d3.interpolateYlOrRd(0.66)}"></div>
                    <span>${(min + (max - min) * 0.66).toFixed(1)}</span>
                </div>
                <div class="legend-item">
                    <div class="legend-color" style="background-color: ${d3.interpolateYlOrRd(1)}"></div>
                    <span>${max.toFixed(1)}</span>
                </div>
            `;
        }

        function getColorDomain() {
            const data = Object.values(regionalData[currentDataType]).flat();
            const values = data.map(d => d.value);
            return [d3.min(values), d3.max(values)];
        }

        function getDataForRegion(region, type, year) {
            // Map country names to regions (simplified)
            const regionMapping = {
                'United States of America': 'North America',
                'Canada': 'North America',
                'Mexico': 'North America',
                'Germany': 'Europe',
                'France': 'Europe',
                'United Kingdom': 'Europe',
                'Italy': 'Europe',
                'Spain': 'Europe',
                'China': 'Asia',
                'India': 'Asia',
                'Japan': 'Asia',
                'Russia': 'Asia',
                'Brazil': 'South America',
                'Argentina': 'South America',
                'Egypt': 'Africa',
                'South Africa': 'Africa',
                'Nigeria': 'Africa',
                'Australia': 'Oceania',
                'New Zealand': 'Oceania',
                'Greenland': 'Arctic'
            };
            
            const mappedRegion = regionMapping[region] || 'Global';
            const data = regionalData[type][mappedRegion];
            if (!data) return 0;
            
            const yearData = data.find(d => d.year === year);
            return yearData ? yearData.value : 0;
        }

        function getUnitForDataType(type) {
            switch(type) {
                case 'temperature': return '°C';
                case 'co2': return 'ppm';
                case 'seaLevel': return 'mm';
                default: return '';
            }
        }

        // Initialize charts
        function initializeCharts() {
            // Global trend chart
            const ctx1 = document.getElementById('globalTrendChart').getContext('2d');
            globalTrendChart = new Chart(ctx1, {
                type: 'line',
                data: {
                    labels: globalData[currentDataType].map(d => d.year),
                    datasets: [{
                        label: `Global ${currentDataType}`,
                        data: globalData[currentDataType].map(d => d.value),
                        borderColor: '#38ada9',
                        backgroundColor: 'rgba(56, 173, 169, 0.1)',
                        fill: true,
                        tension: 0.4
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            display: false
                        },
                        tooltip: {
                            mode: 'index',
                            intersect: false
                        }
                    },
                    scales: {
                        x: {
                            display: true,
                            title: {
                                display: true,
                                text: 'Year'
                            }
                        },
                        y: {
                            display: true,
                            title: {
                                display: true,
                                text: getUnitForDataType(currentDataType)
                            }
                        }
                    }
                }
            });
            
            // Regional comparison chart
            const ctx2 = document.getElementById('regionalChart').getContext('2d');
            const regions = Object.keys(regionalData[currentDataType]);
            const latestYear = Math.max(...regionalData[currentDataType][regions[0]].map(d => d.year));
            
            regionalChart = new Chart(ctx2, {
                type: 'bar',
                data: {
                    labels: regions,
                    datasets: [{
                        label: `${currentDataType} in ${latestYear}`,
                        data: regions.map(region => {
                            const data = regionalData[currentDataType][region];
                            return data.find(d => d.year === latestYear)?.value || 0;
                        }),
                        backgroundColor: '#3c6382',
                        borderColor: '#0a3d62',
                        borderWidth: 1
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            display: false
                        }
                    },
                    scales: {
                        x: {
                            display: true,
                            title: {
                                display: true,
                                text: 'Region'
                            }
                        },
                        y: {
                            display: true,
                            title: {
                                display: true,
                                text: getUnitForDataType(currentDataType)
                            }
                        }
                    }
                }
            });
        }

        // Update charts based on selected data type and region
        function updateCharts() {
            // Update global trend chart
            globalTrendChart.data.labels = globalData[currentDataType].map(d => d.year);
            globalTrendChart.data.datasets[0].data = globalData[currentDataType].map(d => d.value);
            globalTrendChart.data.datasets[0].label = `Global ${currentDataType}`;
            globalTrendChart.options.scales.y.title.text = getUnitForDataType(currentDataType);
            
            if (selectedRegion) {
                // Map country to region
                const regionMapping = {
                    'United States of America': 'North America',
                    'Canada': 'North America',
                    'Germany': 'Europe',
                    'China': 'Asia',
                    'Brazil': 'South America',
                    'Australia': 'Oceania',
                    'Greenland': 'Arctic'
                };
                
                const region = regionMapping[selectedRegion] || selectedRegion;
                
                if (regionalData[currentDataType][region]) {
                    const regionData = regionalData[currentDataType][region];
                    
                    // Check if we already have a regional dataset
                    if (globalTrendChart.data.datasets.length > 1) {
                        globalTrendChart.data.datasets[1].data = regionData.map(d => d.value);
                        globalTrendChart.data.datasets[1].label = `${region} ${currentDataType}`;
                    } else {
                        globalTrendChart.data.datasets.push({
                            label: `${region} ${currentDataType}`,
                            data: regionData.map(d => d.value),
                            borderColor: '#e58e26',
                            backgroundColor: 'rgba(229, 142, 38, 0.1)',
                            fill: false,
                            tension: 0.4
                        });
                    }
                }
            } else if (globalTrendChart.data.datasets.length > 1) {
                globalTrendChart.data.datasets.pop();
            }
            
            globalTrendChart.update();
            
            // Update regional chart
            const regions = Object.keys(regionalData[currentDataType]);
            const latestYear = Math.max(...regionalData[currentDataType][regions[0]].map(d => d.year));
            
            regionalChart.data.labels = regions;
            regionalChart.data.datasets[0].data = regions.map(region => {
                const data = regionalData[currentDataType][region];
                return data.find(d => d.year === latestYear)?.value || 0;
            });
            regionalChart.data.datasets[0].label = `${currentDataType} in ${latestYear}`;
            regionalChart.options.scales.y.title.text = getUnitForDataType(currentDataType);
            regionalChart.update();
            
            // Update map colors
            updateMapColors();
        }

        // Set up event listeners
        function setupEventListeners() {
            // Data type selector buttons
            document.querySelectorAll('.data-selector .btn').forEach(button => {
                button.addEventListener('click', function() {
                    document.querySelectorAll('.data-selector .btn').forEach(b => b.classList.remove('active'));
                    this.classList.add('active');
                    currentDataType = this.getAttribute('data-type');
                    updateCharts();
                });
            });
            
            // Key findings cards
            document.querySelectorAll('.finding-card').forEach(card => {
                card.addEventListener('click', function() {
                    this.classList.toggle('active');
                });
            });
            
            // Year slider
            const yearSlider = document.getElementById('yearSlider');
            const yearDisplay = document.getElementById('yearDisplay');
            
            yearSlider.addEventListener('input', function() {
                currentYear = parseInt(this.value);
                yearDisplay.textContent = currentYear;
                updateMapColors();
                
                // Update regional chart to show the selected year
                const regions = Object.keys(regionalData[currentDataType]);
                regionalChart.data.datasets[0].data = regions.map(region => {
                    const data = regionalData[currentDataType][region];
                    return data.find(d => d.year === currentYear)?.value || 0;
                });
                regionalChart.data.datasets[0].label = `${currentDataType} in ${currentYear}`;
                regionalChart.update();
            });
            
            // Handle window resize
            window.addEventListener('resize', function() {
                if (globalTrendChart) globalTrendChart.resize();
                if (regionalChart) regionalChart.resize();
            });
        }
    </script>
</body>
</html>
```
