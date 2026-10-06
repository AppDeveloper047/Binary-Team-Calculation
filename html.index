<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2x2 बाइनरी नेटवर्किंग लेवल कैलकुलेटर</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f0f4f8;
            margin: 0;
            padding: 20px;
            color: #333;
        }
        .container {
            max-width: 900px;
            margin: 0 auto;
            background: #fff;
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }
        h2 {
            text-align: center;
            color: #1e3a8a;
            margin-bottom: 25px;
        }
        .controls-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            background: #f8fafc;
            padding: 20px;
            border-radius: 8px;
            border: 1px solid #e2e8f0;
            margin-bottom: 25px;
        }
        .control-group label {
            display: block;
            font-weight: bold;
            margin-bottom: 8px;
            color: #475569;
            font-size: 14px;
        }
        .control-group input {
            width: 100%;
            padding: 10px;
            border: 1px solid #cbd5e1;
            border-radius: 6px;
            font-size: 16px;
            box-sizing: border-box;
        }
        .summary-banner {
            background: #eff6ff;
            border: 1px solid #bfdbfe;
            padding: 15px 20px;
            border-radius: 8px;
            margin-bottom: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 16px;
            flex-wrap: wrap;
            gap: 10px;
        }
        .summary-banner span {
            font-weight: bold;
            color: #1d4ed8;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
            background: #fff;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 1px 3px rgba(0,0,0,0.05);
        }
        th, td {
            padding: 12px 15px;
            text-align: center;
            border-bottom: 1px solid #e2e8f0;
        }
        th {
            background-color: #1e3a8a;
            color: white;
            font-weight: 600;
        }
        tr:hover {
            background-color: #f8fafc;
        }
        .total-row {
            background-color: #ecfdf5 !important;
            font-weight: bold;
            color: #065f46;
            font-size: 16px;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>2x2 बाइनरी नेटवर्किंग लेवल और इनकम कैलकुलेटर</h2>
    
    <!-- ऊपर दिए गए ऑप्शंस -->
    <div class="controls-grid">
        <div class="control-group">
            <label for="maxLevels">1. कुल लेवल्स (Levels) डालें:</label>
            <input type="number" id="maxLevels" value="6" min="1" max="15" oninput="calculateNetwork()">
        </div>
        <div class="control-group">
            <label for="perPairAmount">2. प्रति मैचिंग अमाउंट (₹ प्रति जोड़ा):</label>
            <input type="number" id="perPairAmount" value="900" min="0" oninput="calculateNetwork()">
        </div>
    </div>

    <!-- कुल समरी -->
    <div class="summary-banner">
        <div>कुल टीम सदस्य (Total Team): <span id="totalMembersSum">0</span></div>
        <div>कुल संभावित कमाई (Total Earning): ₹<span id="totalEarningSum">0</span></div>
    </div>

    <!-- लेवल-वाइज डिटेल्स टेबल -->
    <table>
        <thead>
            <tr>
                <th>लेवल (Level)</th>
                <th>इस लेवल पर सदस्य (Members)</th>
                <th>कुल टीम सदस्य (Cumulative Team)</th>
                <th>मैचिंग जोड़े (Pairs)</th>
                <th>इस लेवल का पेमेंट (Level Income)</th>
            </tr>
        </thead>
        <tbody id="tableBody">
            <!-- डायनेमिक रूप से जनरेट होगा -->
        </tbody>
    </table>
</div>

<script>
    function calculateNetwork() {
        let maxLevels = parseInt(document.getElementById('maxLevels').value) || 0;
        let perPairAmount = parseFloat(document.getElementById('perPairAmount').value) || 0;
        
        let tbody = document.getElementById('tableBody');
        tbody.innerHTML = '';

        let cumulativeTeam = 0;
        let totalEarnings = 0;

        if (maxLevels <= 0) {
            document.getElementById('totalMembersSum').innerText = 0;
            document.getElementById('totalEarningSum').innerText = '0';
            return;
        }

        for (let i = 1; i <= maxLevels; i++) {
            // 2*2 बाइनरी स्ट्रक्चर के अनुसार हर लेवल पर सदस्य (2, 4, 8, 16, 32...)
            let membersAtLevel = Math.pow(2, i);
            cumulativeTeam += membersAtLevel;
            
            // जोड़े (Pairs) = सदस्यों की संख्या का आधा
            let pairsAtLevel = membersAtLevel / 2;
            let levelIncome = pairsAtLevel * perPairAmount;
            totalEarnings += levelIncome;

            let row = document.createElement('tr');
            row.innerHTML = `
                <td><strong>Level ${i}</strong></td>
                <td>${membersAtLevel}</td>
                <td>${cumulativeTeam}</td>
                <td>${pairsAtLevel} Pair${pairsAtLevel > 1 ? 's' : ''}</td>
                <td>₹${levelIncome.toLocaleString('en-IN')}</td>
            `;
            tbody.appendChild(row);
        }

        // कुल योग की पंक्ति (Total Row)
        let totalRow = document.createElement('tr');
        totalRow.className = 'total-row';
        totalRow.innerHTML = `
            <td>Total / कुल</td>
            <td>-</td>
            <td>${cumulativeTeam.toLocaleString('en-IN')} लोग</td>
            <td>-</td>
            <td>₹${totalEarnings.toLocaleString('en-IN')}</td>
        `;
        tbody.appendChild(totalRow);

        document.getElementById('totalMembersSum').innerText = cumulativeTeam.toLocaleString('en-IN');
        document.getElementById('totalEarningSum').innerText = totalEarnings.toLocaleString('en-IN');
    }

    // पेज लोड होते ही कैलकुलेशन रन करें
    window.onload = calculateNetwork;
</script>

</body>
</html>
