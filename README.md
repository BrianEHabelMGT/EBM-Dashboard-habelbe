# MGT-357
index.html 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My EBM Dashboard | MGT357 - Fall 2025</title>
    <style>
        :root {
            --primary-gradient: linear-gradient(135deg, #101820 0%, #FFB612 100%);
            --tab-active: #101820;
            --tab-inactive: #FFB612;
            --tab-active-text: #FFB612;
            --tab-inactive-text: #101820;
            --step-gold: #FFB612;
            --step-black: #101820;
            --border-radius: 15px;
            --transition-speed: 0.3s;
        }
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: var(--primary-gradient);
            min-height: 100vh;
            padding: 20px;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: var(--border-radius);
            box-shadow: 0 20px 60px rgba(0,0,0,0.1);
            overflow: hidden;
        }
        .header {
            background: linear-gradient(135deg, #101820, #FFB612);
            color: #101820;
            padding: 30px;
            text-align: center;
        }
        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            color: #FFB612;
            text-shadow: 2px 2px 0 #101820, 0 0 10px #10182022;
        }
        .header p {
            font-size: 1.2em;
            opacity: 0.9;
            color: #101820;
        }
        .student-info {
            background: rgba(255, 182, 18, 0.08);
            padding: 15px;
            margin-top: 20px;
            border-radius: 10px;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            font-size: 0.9em;
        }
        .tab-nav {
            display: flex;
            background: #FFFDE4;
            border-bottom: 3px solid #FFB612;
        }
        .tab-button {
            flex: 1;
            padding: 20px;
            text-align: center;
            cursor: pointer;
            background: var(--tab-inactive);
            color: var(--tab-inactive-text);
            font-weight: bold;
            font-size: 1.1em;
            transition: all var(--transition-speed);
            border: none;
            border-right: 2px solid #101820;
        }
        .tab-button:last-child { border-right: none; }
        .tab-button:hover {
            background: #ffe066;
            color: #101820;
            transform: translateY(-2px);
        }
        .tab-button.active {
            background: var(--tab-active);
            color: var(--tab-active-text);
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(255,182,18, 0.3);
        }
        .tab-content {
            position: relative;
            min-height: 500px;
        }
        .tab-panel {
            display: none;
            padding: 40px;
            animation: fadeIn 0.3s ease-in;
        }
        .tab-panel.active { display: block; }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateX(20px); }
            to { opacity: 1; transform: translateX(0); }
        }
        .flowchart-step {
            background: var(--step-gold);
            color: var(--step-black);
            padding: 15px 25px;
            border-radius: 25px;
            margin: 15px 0;
            font-weight: bold;
            text-align: center;
            box-shadow: 0 4px 15px rgba(255,182,18, 0.22);
            border: 2px solid #101820;
        }
        .decision-diamond {
            background: var(--step-black);
            color: var(--step-gold);
            padding: 15px 25px;
            border-radius: 10px;
            margin: 15px 0;
            text-align: center;
            position: relative;
            transform: rotate(45deg);
            border: 2px solid #FFB612;
        }
        .decision-diamond .text {
            transform: rotate(-45deg);
            font-weight: bold;
        }
        .content-file-preview {
            background: #FFFDE4;
            border: 2px dashed #FFB612;
            border-radius: 10px;
            padding: 20px;
            margin: 20px 0;
            font-family: 'Courier New', monospace;
            font-size: 0.9em;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        .content-file-preview:hover {
            border-color: #101820;
            background: #fff9c4;
        }
        .content-file-preview h4 {
            color: #FFB612;
            margin-bottom: 10px;
            font-family: 'Segoe UI', sans-serif;
        }
        .edit-notice {
            background: #fff8e1;
            border: 1px solid #FFB612;
            color: #101820;
            padding: 10px;
            border-radius: 5px;
            margin: 10px 0;
            font-size: 0.8em;
        }
        .evidence-type {
            display: inline-block;
            padding: 8px 15px;
            margin: 5px;
            border-radius: 20px;
            color: #101820;
            font-weight: bold;
            background: #FFB612;
            border: 1px solid #101820;
        }
        .scientific { background: #FFB612; color: #101820; }
        .practitioner { background: #FFFDE4; color: #101820; }
        .organizational { background: #101820; color: #FFB612; }
        .stakeholder { background: #FFB612; color: #101820; }
        .evidence-section {
            margin: 40px 0;
            padding: 25px;
            border-left: 5px solid #FFB612;
            background: #FFFDE4;
            border-radius: 10px;
        }
        .evidence-section h3 {
            margin-top: 0;
            margin-bottom: 20px;
            padding: 10px 20px;
            border-radius: 25px;
            display: inline-block;
        }
        .evidence-section .content-file-preview { margin: 15px 0; }
        .progress-indicator {
            display: flex;
            justify-content: space-between;
            padding: 20px;
            background: linear-gradient(135deg, #FFB612, #FFFDE4);
            margin: 0;
            border-bottom: 3px solid #101820;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0,0,0,0.08);
        }
        .progress-step {
            flex: 1;
            text-align: center;
            padding: 12px 8px;
            margin: 0 5px;
            border-radius: 8px;
            font-weight: bold;
            font-size: 0.9em;
            transition: all var(--transition-speed);
            position: relative;
            cursor: pointer;
            background: #FFFDE4;
            color: #101820;
            border: 2px solid #FFB612;
        }
        .progress-step.completed {
            background: linear-gradient(135deg, #101820, #444444);
            color: #FFB612;
            transform: scale(1.05);
            box-shadow: 0 4px 15px rgba(16,24,32, 0.22);
            border: 2px solid #FFB612;
        }
        .progress-step.active {
            background: linear-gradient(135deg, #FFB612, #fff3b0);
            color: #101820;
            transform: scale(1.05);
            box-shadow: 0 4px 15px rgba(255,182,18, 0.26);
            border: 2px solid #101820;
        }
        .progress-step.pending {
            background: #FFFDE4;
            color: #101820;
            border: 2px dashed #FFB612;
        }
        .progress-step::after {
            content: '';
            position: absolute;
            top: 50%;
            right: -15px;
            width: 0;
            height: 0;
            border-left: 10px solid;
            border-top: 10px solid transparent;
            border-bottom: 10px solid transparent;
            transform: translateY(-50%);
            z-index: 1;
        }
        .progress-step.completed::after { border-left-color: #101820; }
        .progress-step.active::after { border-left-color: #FFB612; }
        .progress-step.pending::after { border-left-color: #FFB612; }
        .progress-step:last-child::after { display: none; }
        .btn {
            background: linear-gradient(135deg, #101820, #444444);
            color: #FFB612;
            padding: 12px 25px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-weight: bold;
            margin: 10px 5px;
            transition: all var(--transition-speed);
            border: 2px solid #FFB612;
        }
        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(255,182,18, 0.22);
            background: #FFB612;
            color: #101820;
            border: 2px solid #101820;
        }
        .milestone-tracker {
            background: #FFFDE4;
            border-left: 4px solid #FFB612;
            padding: 20px;
            margin: 20px 0;
            border-radius: 8px;
        }
        .milestone-tracker h4 {
            color: #101820;
            margin-bottom: 10px;
        }
        .checklist {
            list-style: none;
            padding: 0;
        }
        .checklist li {
            padding: 5px 0;
            color: #101820;
        }
        .checklist li:before {
            content: "☐ ";
            color: #FFB612;
            font-weight: bold;
        }
    </style>
    <script>
        // Simple tab system
        document.addEventListener("DOMContentLoaded", function() {
            let buttons = document.querySelectorAll('.tab-button');
            let panels = document.querySelectorAll('.tab-panel');
            function activateTab(idx) {
                buttons.forEach((btn, i) => {
                    btn.classList.toggle('active', i === idx);
                    panels[i].classList.toggle('active', i === idx);
                });
            }
            buttons.forEach((btn, i) => {
                btn.addEventListener('click', () => activateTab(i));
            });
            activateTab(0); // activate first tab by default
        });
    </script>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>My EBM Dashboard</h1>
            <p>MGT357 - Fall 2025 | Steelers Edition</p>
        </div>
        <div class="student-info">
            <div><strong>Name:</strong> Brian Habel</div>
            <div><strong>Class:</strong> MGT357</div>
            <div><strong>Semester:</strong> Fall 2025</div>
            <div><strong>Favorite Team:</strong> Steelers 🏈</div>
        </div>
        <nav class="tab-nav">
            <button class="tab-button active">Overview</button>
            <button class="tab-button">Milestones</button>
            <button class="tab-button">Evidence</button>
        </nav>
        <div class="tab-content">
            <section class="tab-panel active">
                <h2>Welcome to your EBM Dashboard</h2>
                <div class="flowchart-step">Identify Problem</div>
                <div class="decision-diamond"><span class="text">Gather Evidence?</span></div>
                <div class="flowchart-step">Evaluate Evidence</div>
            </section>
            <section class="tab-panel">
                <h2>Milestone Tracker</h2>
                <div class="milestone-tracker">
                    <h4>Milestone 1: Problem Statement</h4>
                    <ul class="checklist">
                        <li>Write problem statement</li>
                        <li>Instructor approval</li>
                    </ul>
                </div>
                <div class="milestone-tracker">
                    <h4>Milestone 2: Evidence Review</h4>
                    <ul class="checklist">
                        <li>Collect articles</li>
                        <li>Summarize findings</li>
                    </ul>
                </div>
            </section>
            <section class="tab-panel">
                <h2>Evidence Types</h2>
                <span class="evidence-type scientific">Scientific</span>
                <span class="evidence-type practitioner">Practitioner</span>
                <span class="evidence-type organizational">Organizational</span>
                <span class="evidence-type stakeholder">Stakeholder</span>
                <div class="evidence-section">
                    <h3>Recent Evidence</h3>
                    <div class="content-file-preview">
                        <h4>Article: Teamwork in the NFL</h4>
                        <p><strong>Type:</strong> Scientific</p>
                        <p>Explores how effective teamwork boosts performance, with examples from the Steelers.</p>
                    </div>
                    <div class="content-file-preview">
                        <h4>Interview: Coach Mike Tomlin</h4>
                        <p><strong>Type:</strong> Practitioner</p>
                        <p>Insights from Coach Tomlin on evidence-based leadership in sports organizations.</p>
                    </div>
                </div>
            </section>
        </div>
    </div>
</body>
</html>
