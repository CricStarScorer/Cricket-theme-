<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CricScorer Ticker Theme - Transparent</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: transparent !important;
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            height: 100vh;
            margin: 0;
        }

        /* ट्रांसपेरेंट टिकर बैनर */
        .ticker-container {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 80px;
            background: rgba(20, 20, 35, 0.85) !important; /* थोड़ा ट्रांसपेरेंट */
            backdrop-filter: blur(10px); /* ग्लास मॉर्फिक इफेक्ट */
            -webkit-backdrop-filter: blur(10px);
            border-top: 3px solid #e94560;
            display: flex;
            align-items: center;
            padding: 0 20px;
            z-index: 9999;
            box-shadow: 0 -5px 20px rgba(0, 0, 0, 0.3);
        }

        /* लाइव बैज */
        .live-badge {
            background: rgba(233, 69, 96, 0.9);
            color: white;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: bold;
            margin-right: 20px;
            display: flex;
            align-items: center;
            animation: blink 1.5s infinite;
            backdrop-filter: blur(5px);
        }

        .live-dot {
            width: 8px;
            height: 8px;
            background: white;
            border-radius: 50%;
            margin-right: 5px;
        }

        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }

        /* टीम और स्कोर */
        .match-info {
            display: flex;
            align-items: center;
            flex: 1;
        }

        .team {
            display: flex;
            align-items: center;
            margin: 0 15px;
        }

        .team-flag {
            width: 30px;
            height: 30px;
            border-radius: 50%;
            background: rgba(233, 69, 96, 0.9);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            font-size: 12px;
            margin-right: 10px;
            backdrop-filter: blur(5px);
        }

        .team-name {
            font-size: 16px;
            color: white;
            font-weight: bold;
            min-width: 100px;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.8);
        }

        .score {
            font-size: 24px;
            font-weight: bold;
            color: #ffd700;
            margin-left: 15px;
            text-shadow: 0 0 10px rgba(255, 215, 0, 0.5), 2px 2px 4px rgba(0, 0, 0, 0.8);
        }

        .overs {
            font-size: 14px;
            color: #ffffff;
            margin-left: 8px;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.8);
            font-weight: bold;
        }

        /* बल्लेबाज और गेंदबाज */
        .players-section {
            display: flex;
            background: rgba(255, 255, 255, 0.15);
            padding: 8px 15px;
            border-radius: 10px;
            margin: 0 20px;
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .player {
            margin: 0 15px;
            text-align: center;
            min-width: 100px;
        }

        .player-name {
            font-size: 14px;
            color: #ffd700;
            margin-bottom: 3px;
            font-weight: bold;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.8);
        }

        .player-stats {
            font-size: 20px;
            color: white;
            font-weight: bold;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.8);
        }

        .player-type {
            font-size: 10px;
            color: #ffffff;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-top: 2px;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.8);
        }

        /* रन रेट */
        .match-stats {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin: 0 20px;
            background: rgba(78, 204, 163, 0.2);
            padding: 8px 15px;
            border-radius: 10px;
            backdrop-filter: blur(5px);
            border: 1px solid rgba(78, 204, 163, 0.3);
        }

        .run-rate {
            font-size: 18px;
            color: #4ecca3;
            font-weight: bold;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.8);
        }

        .rr-label {
            font-size: 10px;
            color: #ffffff;
            text-transform: uppercase;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.8);
        }

        /* सेपरेटर */
        .separator {
            color: #e94560;
            font-size: 20px;
            font-weight: bold;
            margin: 0 10px;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.8);
        }

        /* ऑप्शनल: टिकर को ऊपर भी रख सकते हैं */
        .ticker-top {
            top: 0;
            bottom: auto;
            border-top: none;
            border-bottom: 3px solid #e94560;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.3);
        }

        /* टॉगल बटन (पोजीशन बदलने के लिए) */
        .toggle-btn {
            position: fixed;
            top: 10px;
            right: 10px;
            z-index: 10000;
            padding: 5px 10px;
            background: rgba(233, 69, 96, 0.9);
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            backdrop-filter: blur(5px);
            font-size: 12px;
        }

        /* मोबाइल रेस्पॉन्सिव */
        @media (max-width: 1200px) {
            .ticker-container {
                height: 70px;
                padding: 0 10px;
            }
            
            .team-name {
                font-size: 14px;
                min-width: 80px;
            }
            
            .score {
                font-size: 20px;
            }
            
            .player {
                margin: 0 8px;
                min-width: 80px;
            }
            
            .player-stats {
                font-size: 18px;
            }
            
            .players-section {
                margin: 0 10px;
            }
        }

        @media (max-width: 768px) {
            .players-section {
                display: none;
            }
            
            .match-stats {
                margin: 0 10px;
            }
            
            .live-badge {
                margin-right: 10px;
                padding: 3px 8px;
            }
        }
    </style>
</head>
<body>
    <!-- ट्रांसपेरेंट टिकर बैनर -->
    <div class="ticker-container" id="ticker">
        <!-- लाइव बैज -->
        <div class="live-badge">
            <span class="live-dot"></span>
            LIVE
        </div>

        <!-- मैच की जानकारी -->
        <div class="match-info">
            <!-- टीम A -->
            <div class="team">
                <div class="team-flag" id="teamAFlag">ABH</div>
                <div class="team-name" id="teamAName">ABHINAV</div>
            </div>
            <div class="score" id="teamAScore">150-2</div>
            <div class="overs" id="teamAOvers">(8.2)</div>

            <div class="separator">|</div>

            <!-- टीम B -->
            <div class="team">
                <div class="team-flag" id="teamBFlag">GAG</div>
                <div class="team-name" id="teamBName">GAGAN</div>
            </div>
            <div class="score" id="teamBScore">6.6</div>
            <div class="overs" id="teamBOvers">(10)</div>
        </div>

        <!-- बल्लेबाज और गेंदबाज -->
        <div class="players-section" id="playersSection">
            <div class="player">
                <div class="player-name" id="batsman1Name">MOHIT</div>
                <div class="player-stats" id="batsman1Stats">22.8</div>
                <div class="player-type">Batsman 1</div>
            </div>

            <div class="player">
                <div class="player-name" id="batsman2Name">DEEPAK</div>
                <div class="player-stats" id="batsman2Stats">81.27</div>
                <div class="player-type">Batsman 2</div>
            </div>

            <div class="player">
                <div class="player-name" id="bowlerName">GAGAN</div>
                <div class="player-stats" id="bowlerStats">8.2</div>
                <div class="player-type">Bowler</div>
            </div>
        </div>

        <!-- रन रेट -->
        <div class="match-stats">
            <div class="run-rate" id="runRate">18.00</div>
            <div class="rr-label">Run Rate</div>
        </div>
    </div>

    <!-- टॉगल बटन (पोजीशन बदलने के लिए) -->
    <button class="toggle-btn" id="toggleBtn">⬆️ Move to Top</button>

    <!-- पृष्ठ का बाकी हिस्सा पूरी तरह ट्रांसपेरेंट होगा -->
    <!-- यहाँ CricScorer का वीडियो/लाइव स्ट्रीम दिखेगा -->

    <script>
        // CricScorer से डेटा अपडेट करने का फंक्शन
        function updateScore(matchData) {
            // टीम A
            document.getElementById('teamAName').textContent = matchData.teamA || 'TEAM A';
            document.getElementById('teamAFlag').textContent = (matchData.teamA || 'A').substring(0, 3).toUpperCase();
            document.getElementById('teamAScore').textContent = (matchData.scoreA || '0') + '-' + (matchData.wicketsA || '0');
            document.getElementById('teamAOvers').textContent = '(' + (matchData.oversA || '0.0') + ')';
            
            // टीम B
            if (matchData.teamB) {
                document.getElementById('teamBName').textContent = matchData.teamB;
                document.getElementById('teamBFlag').textContent = matchData.teamB.substring(0, 3).toUpperCase();
                document.getElementById('teamBScore').textContent = (matchData.scoreB || '0') + '-' + (matchData.wicketsB || '0');
                document.getElementById('teamBOvers').textContent = '(' + (matchData.oversB || '0.0') + ')';
            } else {
                // अगर एक ही टीम बैटिंग कर रही है
                document.getElementById('teamBName').textContent = 'Required';
                document.getElementById('teamBFlag').textContent = 'REQ';
                document.getElementById('teamBScore').textContent = (matchData.target || '0');
                document.getElementById('teamBOvers').textContent = '(10)';
            }
            
            // बल्लेबाज
            if (matchData.batsman1) {
                document.getElementById('batsman1Name').textContent = matchData.batsman1.name || 'Batsman 1';
                document.getElementById('batsman1Stats').textContent = 
                    (matchData.batsman1.runs || '0') + '/' + (matchData.batsman1.balls || '0');
            }
            
            if (matchData.batsman2) {
                document.getElementById('batsman2Name').textContent = matchData.batsman2.name || 'Batsman 2';
                document.getElementById('batsman2Stats').textContent = 
                    (matchData.batsman2.runs || '0') + '/' + (matchData.batsman2.balls || '0');
            }
            
            // गेंदबाज
            if (matchData.bowler) {
                document.getElementById('bowlerName').textContent = matchData.bowler.name || 'Bowler';
                document.getElementById('bowlerStats').textContent = 
                    (matchData.bowler.overs || '0') + '.' + (matchData.bowler.balls || '0');
            }
            
            // रन रेट
            if (matchData.runRate) {
                document.getElementById('runRate').textContent = matchData.runRate;
            } else if (matchData.oversA) {
                // ऑटो कैलकुलेट
                const runs = parseFloat(matchData.scoreA || 0);
                const overs = parseFloat(matchData.oversA || 1);
                const rr = (runs / overs).toFixed(2);
                document.getElementById('runRate').textContent = rr;
            }
            
            // लाइव बैज अपडेट
            if (matchData.isLive === false) {
                document.querySelector('.live-badge').style.background = 'rgba(102, 102, 102, 0.9)';
                document.querySelector('.live-badge').innerHTML = '<span class="live-dot"></span>ENDED';
            }
        }
        
        // टेस्ट डेटा (आपकी इमेज के अनुसार)
        const testData = {
            teamA: "ABHINAV",
            teamB: "GAGAN",
            scoreA: 150,
            wicketsA: 2,
            oversA: 8.2,
            scoreB: 6.6,
            wicketsB: 0,
            oversB: 10,
            batsman1: { name: "MOHIT", runs: 22, balls: 8 },
            batsman2: { name: "DEEPAK", runs: 81, balls: 27 },
            bowler: { name: "GAGAN", overs: 8, balls: 2, wickets: 0 },
            runRate: "18.00",
            isLive: true
        };
        
        // पेज लोड होते ही डेटा दिखाएं
        document.addEventListener('DOMContentLoaded', function() {
            updateScore(testData);
            
            // टॉगल बटन कार्य
            const ticker = document.getElementById('ticker');
            const toggleBtn = document.getElementById('toggleBtn');
            
            toggleBtn.onclick = function() {
                ticker.classList.toggle('ticker-top');
                this.innerHTML = ticker.classList.contains('ticker-top') ? '⬇️ Move to Bottom' : '⬆️ Move to Top';
            };
            
            // ऑटो हाइड/शो प्लेयर सेक्शन (मोबाइल पर)
            function checkScreenSize() {
                const playersSection = document.getElementById('playersSection');
                if (window.innerWidth <= 768) {
                    playersSection.style.display = 'none';
                } else {
                    playersSection.style.display = 'flex';
                }
            }
            
            checkScreenSize();
            window.addEventListener('resize', checkScreenSize);
        });
        
        // CricScorer के लिए इंटरफ़ेस
        window.updateMatchData = updateScore;
        
        // ऑटो अपडेट (हर 10 सेकंड पर)
        setInterval(function() {
            // यहाँ आप API से लाइव डेटा फ़ेच कर सकते हैं
            // console.log('Auto-updating...');
        }, 10000);
    </script>
</body>
</html>
