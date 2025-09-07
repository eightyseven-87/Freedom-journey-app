<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SquadSense - Healthy Relationships App</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
        
        * { box-sizing: border-box; margin: 0; padding: 0; }
        
        :root {
            --primary: #6366f1;
            --primary-light: #a5b4fc;
            --secondary: #06b6d4;
            --accent: #f59e0b;
            --success: #10b981;
            --warning: #f59e0b;
            --danger: #ef4444;
            --dark: #1f2937;
            --gray: #6b7280;
            --light-gray: #f3f4f6;
            --white: #ffffff;
            --gradient-1: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            --gradient-2: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            --gradient-3: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
            --shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            --shadow-hover: 0 20px 40px rgba(0, 0, 0, 0.15);
        }
        
        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
            min-height: 100vh;
            padding: 20px;
            line-height: 1.6;
            color: var(--dark);
        }
        
        .container { max-width: 640px; margin: 0 auto; }
        
        .header {
            text-align: center;
            background: var(--white);
            padding: 40px 30px;
            border-radius: 24px;
            margin-bottom: 24px;
            box-shadow: var(--shadow);
            position: relative;
            overflow: hidden;
        }
        
        .header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: var(--gradient-1);
        }
        
        .card {
            background: var(--white);
            padding: 32px;
            margin: 24px 0;
            border-radius: 20px;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            border: 1px solid rgba(99, 102, 241, 0.1);
        }
        
        .card:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-hover);
        }
        
        .button {
            background: var(--primary);
            color: var(--white);
            padding: 16px 32px;
            border: none;
            border-radius: 16px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 500;
            margin: 12px 8px;
            display: inline-block;
            text-decoration: none;
            transition: all 0.3s ease;
            text-align: center;
            min-width: 200px;
            box-shadow: 0 4px 12px rgba(99, 102, 241, 0.3);
        }
        
        .button:hover { 
            background: #4f46e5; 
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(99, 102, 241, 0.4);
        }
        
        .nav-button { 
            background: var(--secondary); 
            display: block; 
            margin: 16px 0;
            box-shadow: 0 4px 12px rgba(6, 182, 212, 0.3);
        }
        .nav-button:hover { 
            background: #0891b2;
            box-shadow: 0 8px 20px rgba(6, 182, 212, 0.4);
        }
        
        .back-button { 
            background: var(--gray); 
            min-width: auto;
            box-shadow: 0 4px 12px rgba(107, 114, 128, 0.3);
        }
        .back-button:hover { background: #4b5563; }
        
        .energy-section {
            background: var(--gradient-3);
            color: var(--white);
            padding: 32px;
            border-radius: 20px;
            margin: 24px 0;
            text-align: center;
        }
        
        .energy-visual {
            font-size: 48px;
            margin: 20px 0;
            filter: drop-shadow(0 4px 8px rgba(0,0,0,0.1));
        }
        
        .insight-box {
            background: linear-gradient(135deg, #ecfdf5 0%, #d1fae5 100%);
            padding: 24px;
            border-radius: 16px;
            border-left: 4px solid var(--success);
            margin: 24px 0;
        }
        
        .awareness-box {
            background: linear-gradient(135deg, #fef3c7 0%, #fde68a 100%);
            padding: 24px;
            border-radius: 16px;
            border-left: 4px solid var(--warning);
            margin: 24px 0;
        }
        
        .boundary-box {
            background: linear-gradient(135deg, #fee2e2 0%, #fecaca 100%);
            padding: 24px;
            border-radius: 16px;
            border-left: 4px solid var(--danger);
            margin: 24px 0;
        }
        
        .truth-box {
            background: var(--gradient-1);
            color: var(--white);
            padding: 24px;
            border-radius: 16px;
            margin: 24px 0;
            text-align: center;
        }
        
        .rating-container {
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 24px 0;
            flex-wrap: wrap;
        }
        
        .rating-scale {
            display: flex;
            gap: 16px;
            margin: 16px 0;
            justify-content: center;
        }
        
        .rating-number {
            width: 48px;
            height: 48px;
            border-radius: 12px;
            background: var(--light-gray);
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 600;
            border: 2px solid transparent;
        }
        
        .rating-number:hover { 
            background: var(--primary-light); 
            color: var(--white);
            transform: scale(1.1);
        }
        
        .rating-number.selected { 
            background: var(--primary); 
            color: var(--white);
            border-color: var(--primary);
            transform: scale(1.1);
            box-shadow: 0 4px 12px rgba(99, 102, 241, 0.4);
        }
        
        .reflection-area {
            background: #f8fafc;
            padding: 24px;
            border-radius: 16px;
            margin: 24px 0;
            border: 1px solid #e2e8f0;
        }
        
        textarea, input[type="text"], select {
            width: 100%;
            padding: 16px;
            border: 2px solid #e5e7eb;
            border-radius: 12px;
            font-size: 16px;
            font-family: inherit;
            resize: vertical;
            min-height: 80px;
            margin: 12px 0;
            transition: border-color 0.3s ease;
        }
        
        select {
            min-height: auto;
            height: 50px;
        }
        
        textarea:focus, input[type="text"]:focus, select:focus { 
            border-color: var(--primary); 
            outline: none;
            box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
        }
        
        .hidden { display: none; }
        
        .progress-container {
            background: var(--white);
            padding: 24px;
            border-radius: 16px;
            margin: 24px 0;
            box-shadow: var(--shadow);
        }
        
        .progress-bar {
            width: 100%;
            height: 12px;
            background: #e5e7eb;
            border-radius: 6px;
            overflow: hidden;
            margin: 16px 0;
        }
        
        .progress-fill {
            height: 100%;
            background: var(--gradient-1);
            transition: width 0.5s ease;
            border-radius: 6px;
        }
        
        h1 { 
            color: var(--dark); 
            margin-bottom: 12px; 
            font-size: 2.5em; 
            font-weight: 700;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        h2 { 
            color: var(--dark); 
            margin-bottom: 20px; 
            font-size: 1.8em; 
            font-weight: 600;
        }
        
        h3 { 
            color: var(--dark); 
            margin-bottom: 16px; 
            font-size: 1.4em; 
            font-weight: 600;
        }
        
        h4 { 
            color: var(--gray); 
            margin-bottom: 12px; 
            font-size: 1.1em; 
            font-weight: 500;
        }
        
        p { margin-bottom: 16px; }
        strong { color: var(--dark); font-weight: 600; }
        em { font-style: italic; color: var(--gray); }
        
        .grid { 
            display: grid; 
            grid-template-columns: 1fr 1fr; 
            gap: 20px; 
            margin: 24px 0; 
        }
        
        .metric-card {
            background: var(--white);
            padding: 20px;
            border-radius: 16px;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.08);
            border: 1px solid #e5e7eb;
            transition: all 0.3s ease;
        }
        
        .metric-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.12);
        }
        
        .interaction-entry {
            background: var(--white);
            padding: 20px;
            margin: 16px 0;
            border-radius: 12px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.05);
            border-left: 4px solid var(--primary);
        }
        
        .interaction-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 12px;
            font-size: 14px;
            color: var(--gray);
        }
        
        @media (max-width: 600px) {
            .grid { grid-template-columns: 1fr; }
            .container { padding: 10px; }
            .rating-scale { gap: 12px; }
            .rating-number { width: 40px; height: 40px; }
            body { padding: 15px; }
        }
        
        .fade-in {
            animation: fadeIn 0.4s ease-out;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="header">
            <h1>SquadSense</h1>
            <p style="font-size: 18px; color: var(--gray); margin-top: 8px;"><strong>Learning healthy emotional boundaries</strong></p>
            <p style="font-size: 16px; color: var(--gray); margin-top: 12px;"><em>"Above all else, guard your heart, for everything you do flows from it." - Proverbs 4:23</em></p>
        </div>

        <!-- Dashboard -->
        <div id="dashboard">
            <div class="truth-box">
                <h3 style="color: white; margin-bottom: 12px;">Today's Truth</h3>
                <p id="verse-text" style="font-size: 18px; margin-bottom: 8px;"></p>
                <p><strong id="verse-ref" style="font-size: 16px;"></strong></p>
                <button class="button" onclick="newVerse()" style="background: rgba(255,255,255,0.2); font-size: 14px; padding: 8px 16px; min-width: auto; margin-top: 16px;">New Truth</button>
            </div>

            <div class="card">
                <h2>Your Tools</h2>
                <button class="button nav-button" onclick="showSection('energy')">⚡ Energy Check</button>
                <button class="button nav-button" onclick="showSection('friendship')">💭 Friendship Awareness</button>
                <button class="button nav-button" onclick="showSection('boundaries')">🛡️ Boundary Wisdom</button>
                <button class="button nav-button" onclick="showSection('practice')">🎭 Practice Lab</button>
                <button class="button nav-button" onclick="showSection('tracker')">📱 Interaction Insights</button>
            </div>

            <div class="progress-container">
                <h3>Your Growth Journey</h3>
                <div class="progress-bar">
                    <div class="progress-fill" id="progress-fill"></div>
                </div>
                <p id="progress-text" style="color: var(--gray); font-size: 16px;">0/10 insights recorded</p>
            </div>
        </div>

        <!-- Energy Check Section -->
        <div id="energy" class="hidden">
            <div class="card fade-in">
                <button class="button back-button" onclick="showSection('dashboard')">← Back</button>
                <h2>⚡ Your Emotional Energy</h2>
                
                <div class="energy-section">
                    <div class="energy-visual">🔋</div>
                    <h3 style="color: white;">How charged do you feel right now?</h3>
                    <div class="rating-scale">
                        <div class="rating-number" onclick="selectEnergy(1)" style="background: rgba(255,255,255,0.2); color: white;">1</div>
                        <div class="rating-number" onclick="selectEnergy(2)" style="background: rgba(255,255,255,0.2); color: white;">2</div>
                        <div class="rating-number" onclick="selectEnergy(3)" style="background: rgba(255,255,255,0.2); color: white;">3</div>
                        <div class="rating-number" onclick="selectEnergy(4)" style="background: rgba(255,255,255,0.2); color: white;">4</div>
                        <div class="rating-number" onclick="selectEnergy(5)" style="background: rgba(255,255,255,0.2); color: white;">5</div>
                    </div>
                    <p style="color: white; font-size: 16px;"><strong>1 = Completely Drained | 5 = Fully Energized</strong></p>
                </div>

                <div class="insight-box">
                    <h4>The Phone Charger Principle</h4>
                    <p><strong>Healthy:</strong> You charge your own emotional battery first, then share energy from your surplus.</p>
                    <p><strong>Unhealthy:</strong> You're constantly giving your charger to others while your own battery dies.</p>
                </div>

                <div class="grid">
                    <div class="metric-card">
                        <h4>Energy Boosters</h4>
                        <ul style="text-align: left; font-size: 12px;">
                            <li>Solo time with music</li>
                            <li>Creative activities (art, writing)</li>
                            <li>Nature walks or outdoor time</li>
                            <li>Prayer, meditation, or journaling</li>
                            <li>Quality sleep (7-9 hours)</li>
                            <li>Exercise or movement</li>
                            <li>Reading inspiring books</li>
                            <li>Taking a hot shower/bath</li>
                            <li>Organizing your space</li>
                            <li>Cooking or baking</li>
                            <li>Calling a life-giving friend</li>
                            <li>Setting small, achievable goals</li>
                        </ul>
                    </div>
                    <div class="metric-card">
                        <h4>Energy Drains</h4>
                        <ul style="text-align: left; font-size: 12px;">
                            <li>Drama-heavy conversations</li>
                            <li>People-pleasing behaviors</li>
                            <li>Overthinking social interactions</li>
                            <li>Being constantly available/on call</li>
                            <li>Managing others' emotions</li>
                            <li>Gossiping or negative talk</li>
                            <li>Social media comparison</li>
                            <li>Saying yes when you mean no</li>
                            <li>Staying up too late</li>
                            <li>Skipping meals</li>
                            <li>Being around critical people</li>
                            <li>Avoiding conflict that needs addressing</li>
                        </ul>
                    </div>
                </div>

                <div class="reflection-area">
                    <h4>What's affecting your energy lately?</h4>
                    <textarea id="energy-reflection" placeholder="What situations, people, or patterns have been impacting your emotional battery?"></textarea>
                    <button class="button" onclick="saveEnergyCheck()">Save Energy Check</button>
                </div>
            </div>
        </div>

        <!-- Friendship Awareness Section -->
        <div id="friendship" class="hidden">
            <div class="card fade-in">
                <button class="button back-button" onclick="showSection('dashboard')">← Back</button>
                <h2>💭 Friendship Awareness</h2>

                <div class="insight-box">
                    <h4>Two Types of Social Energy</h4>
                    <p><strong>Life-Giving:</strong> Conversations that leave you feeling understood, energized, and valued for who you are.</p>
                    <p><strong>Life-Draining:</strong> Interactions that leave you feeling anxious, depleted, or like you need to be someone else.</p>
                </div>

                <div class="grid">
                    <div style="background: linear-gradient(135deg, #d1fae5 0%, #a7f3d0 100%); padding: 24px; border-radius: 16px;">
                        <h4>Healthy Friendship Patterns:</h4>
                        <ul style="font-size: 15px;">
                            <li>Mutual curiosity about each other</li>
                            <li>Can disagree without drama</li>
                            <li>Celebrates your growth</li>
                            <li>Respects your other relationships</li>
                            <li>You feel like yourself around them</li>
                        </ul>
                    </div>
                    <div style="background: linear-gradient(135deg, #fee2e2 0%, #fecaca 100%); padding: 24px; border-radius: 16px;">
                        <h4>Draining Friendship Patterns:</h4>
                        <ul style="font-size: 15px;">
                            <li>Everything revolves around their needs</li>
                            <li>You feel responsible for their emotions</li>
                            <li>Walking on eggshells constantly</li>
                            <li>Guilt trips when you have boundaries</li>
                            <li>You lose yourself trying to please them</li>
                        </ul>
                    </div>
                </div>

                <div class="boundary-box">
                    <h4>SHAME Reality Check</h4>
                    <p><strong>S</strong>hould <strong>H</strong>ave <strong>A</strong>lready <strong>M</strong>astered <strong>E</strong>verything</p>
                    <p>If someone consistently makes you feel like you "should have already mastered" being perfect, that's shame speaking - not love.</p>
                    <p><em>"There is no fear in love. But perfect love drives out fear." - 1 John 4:18</em></p>
                </div>

                <div class="reflection-area">
                    <h4>Friendship Pattern Recognition</h4>
                    <textarea id="friendship-reflection" placeholder="Think about your closest friendships. What patterns do you notice? Which relationships energize you vs. drain you?"></textarea>
                    <button class="button" onclick="saveFriendshipCheck()">Save Insights</button>
                </div>
            </div>
        </div>

        <!-- Boundary Wisdom Section -->
        <div id="boundaries" class="hidden">
            <div class="card fade-in">
                <button class="button back-button" onclick="showSection('dashboard')">← Back</button>
                <h2>🛡️ Boundary Wisdom</h2>

                <div class="insight-box">
                    <h4>Boundaries Are Like a Garden Gate</h4>
                    <p>You decide who gets access to your inner world, who stays in the friendship zone, and who doesn't get invited in at all. Having a gate doesn't make you mean - it makes you wise.</p>
                </div>

                <div class="awareness-box">
                    <h4>Signs You Need Stronger Boundaries:</h4>
                    <ul>
                        <li>You feel responsible for fixing others' emotions</li>
                        <li>You say "yes" when every fiber wants to say "no"</li>
                        <li>You feel guilty for having different opinions</li>
                        <li>You're exhausted from managing someone else's problems</li>
                        <li>You feel like you're losing yourself in relationships</li>
                    </ul>
                </div>

                <div class="grid">
                    <div style="background: linear-gradient(135deg, #ecfdf5 0%, #d1fae5 100%); padding: 24px; border-radius: 16px;">
                        <h4>Healthy Boundaries Sound Like:</h4>
                        <ul style="font-size: 15px;">
                            <li>"I care about you, but I can't solve this for you"</li>
                            <li>"I need some time to process this"</li>
                            <li>"That doesn't feel right for me"</li>
                            <li>"I'm not available to discuss this right now"</li>
                        </ul>
                    </div>
                    <div style="background: linear-gradient(135deg, #fef3c7 0%, #fde68a 100%); padding: 24px; border-radius: 16px;">
                        <h4>Boundary Myths vs Reality:</h4>
                        <ul style="font-size: 15px;">
                            <li>❌ "Boundaries are selfish" → ✅ Boundaries are loving</li>
                            <li>❌ "Good friends don't need boundaries" → ✅ Good friends respect them</li>
                            <li>❌ "I'm being mean" → ✅ I'm being honest</li>
                        </ul>
                    </div>
                </div>

                <div class="truth-box">
                    <p style="color: white; font-size: 18px; text-shadow: 1px 1px 2px rgba(0,0,0,0.3);"><em>"Above all else, guard your heart, for everything you do flows from it."</em></p>
                    <p style="color: white; margin-top: 8px; text-shadow: 1px 1px 2px rgba(0,0,0,0.3);"><strong>- Proverbs 4:23</strong></p>
                    <p style="color: white; margin-top: 12px; text-shadow: 1px 1px 2px rgba(0,0,0,0.3);">God wants you to protect your heart, not give it away to everyone who asks.</p>
                </div>

                <div class="reflection-area">
                    <h4>Boundary Exploration</h4>
                    <textarea id="boundary-reflection" placeholder="What boundary do you sense you need to set? What situation keeps draining your emotional energy?"></textarea>
                    <button class="button" onclick="saveBoundaryCheck()">Save Boundary Insight</button>
                </div>
            </div>
        </div>

        <!-- Practice Lab Section -->
        <div id="practice" class="hidden">
            <div class="card fade-in">
                <button class="button back-button" onclick="showSection('dashboard')">← Back</button>
                <h2>🎭 Practice Lab</h2>

                <div class="insight-box">
                    <h4>Role-Play for Real Life</h4>
                    <p>Practice healthy responses to common social situations. Choose a scenario and think through how you'd respond using biblical wisdom.</p>
                </div>

                <div class="reflection-area">
                    <h4>Choose a scenario to practice:</h4>
                    <select id="scenario-selector" onchange="loadScenario()">
                        <option value="">Select a scenario...</option>
                        <option value="peer-pressure">Friend pressuring you to do something uncomfortable</option>
                        <option value="drama-involvement">Friend wants you to pick sides in drama</option>
                        <option value="constant-venting">Friend constantly vents but never listens</option>
                        <option value="guilt-trip">Friend guilt-trips you for having other plans</option>
                        <option value="boundary-pushback">Friend gets upset when you set a boundary</option>
                        <option value="approval-seeking">Feeling like you need everyone's approval</option>
                    </select>

                    <div id="scenario-content" style="margin: 20px 0;"></div>

                    <div id="practice-response" style="display: none;">
                        <h4>How would you respond?</h4>
                        <textarea id="practice-answer" placeholder="Write your response here..."></textarea>
                        <button class="button" onclick="getPracticeFeedback()">Get Biblical Feedback</button>
                    </div>

                    <div id="feedback-content" style="margin: 20px 0;"></div>
                </div>
            </div>
        </div>

        <!-- Interaction Insights Tracker -->
        <div id="tracker" class="hidden">
            <div class="card fade-in">
                <button class="button back-button" onclick="showSection('dashboard')">← Back</button>
                <h2>📱 Interaction Insights</h2>

                <div class="insight-box">
                    <h4>Self-Awareness Through Patterns</h4>
                    <p>Tracking how interactions affect you helps you understand your own emotional patterns and recognize which relationships are healthy vs. draining.</p>
                </div>

                <div class="reflection-area">
                    <h4>Reflect on your most recent social interaction:</h4>
                    
                    <div style="margin: 24px 0;">
                        <p><strong>How anxious did you feel? (1 = completely calm, 5 = very anxious)</strong></p>
                        <div class="rating-scale" id="anxiety-scale">
                            <div class="rating-number" onclick="selectAnxiety(1)">1</div>
                            <div class="rating-number" onclick="selectAnxiety(2)">2</div>
                            <div class="rating-number" onclick="selectAnxiety(3)">3</div>
                            <div class="rating-number" onclick="selectAnxiety(4)">4</div>
                            <div class="rating-number" onclick="selectAnxiety(5)">5</div>
                        </div>
                    </div>

                    <div style="margin: 24px 0;">
                        <p><strong>How energized did you feel? (1 = completely drained, 5 = very energized)</strong></p>
                        <div class="rating-scale" id="energy-scale">
                            <div class="rating-number" onclick="selectInteractionEnergy(1)">1</div>
                            <div class="rating-number" onclick="selectInteractionEnergy(2)">2</div>
                            <div class="rating-number" onclick="selectInteractionEnergy(3)">3</div>
                            <div class="rating-number" onclick="selectInteractionEnergy(4)">4</div>
                            <div class="rating-number" onclick="selectInteractionEnergy(5)">5</div>
                        </div>
                    </div>

                    <p><strong>What happened and how did it affect you?</strong></p>
                    <textarea id="interaction-notes" placeholder="Focus on YOUR experience: What did you notice about your emotions, energy, or reactions during this interaction?"></textarea>
                    
                    <button class="button" onclick="saveInteractionInsight()">Save Insight</button>
                </div>

                <div class="card" style="background: #f8fafc;">
                    <h4>Your Recent Insights</h4>
                    <div id="interaction-history">
                        <p style="text-align: center; color: var(--gray); padding: 20px;">Your insights will appear here as you track interactions</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Footer -->
        <div class="truth-box" style="text-align: center; margin-top: 40px;">
            <p style="color: white; font-size: 18px;"><strong>"She is clothed with strength and dignity; she can laugh at the days to come."</strong></p>
            <p style="color: white; margin-top: 8px;"><strong>- Proverbs 31:25</strong></p>
            <p style="color: white; margin-top: 16px;">You are strong, loved, and worthy of healthy relationships.</p>
        </div>
    </div>

    <script>
        // App state
        let completedInsights = 0;
        let energyChecks = [];
        let friendshipChecks = [];
        let boundaryChecks = [];
        let interactions = [];
        let currentAnxiety = 0;
        let currentInteractionEnergy = 0;

        // Encouraging verses for young women - updated with boundary verses
        const verses = [
            {text: "She is clothed with strength and dignity; she can laugh at the days to come.", ref: "Proverbs 31:25"},
            {text: "Above all else, guard your heart, for everything you do flows from it.", ref: "Proverbs 4:23"},
            {text: "Am I now trying to win the approval of human beings, or of God?", ref: "Galatians 1:10"},
            {text: "Walk with the wise and become wise, for a companion of fools suffers harm.", ref: "Proverbs 13:20"},
            {text: "Be as shrewd as snakes and as innocent as doves.", ref: "Matthew 10:16"},
            {text: "My sheep listen to my voice; I know them, and they follow me.", ref: "John 10:27"},
            {text: "It is for freedom that Christ has set us free. Stand firm, then, and do not let yourselves be burdened again by a yoke of slavery.", ref: "Galatians 5:1"},
            {text: "You were bought at a price; do not become slaves of human beings.", ref: "1 Corinthians 7:23"}
        ];

        // Practice scenarios
        const scenarios = {
            "peer-pressure": {
                title: "Friend Pressuring You",
                situation: "Your friend keeps pushing you to do something that makes you uncomfortable, saying things like 'Come on, everyone's doing it' or 'I thought you were my friend.'",
                biblicalPrinciple: "Galatians 1:10 - 'Am I now trying to win the approval of human beings, or of God?'",
                healthyResponse: "A healthy response acknowledges the friendship while standing firm in your values. You might say: 'I care about our friendship, but this doesn't feel right for me.' Remember, a true friend will respect your boundaries."
            },
            "drama-involvement": {
                title: "Picking Sides in Drama",
                situation: "Your friend is in conflict with someone else and wants you to take their side, share private information, or participate in talking about the other person.",
                biblicalPrinciple: "Proverbs 27:14 - 'If anyone loudly blesses their neighbor early in the morning, it will be taken as a curse.' (Sometimes what looks like friendship isn't healthy)",
                healthyResponse: "You can support your friend without participating in drama. Try: 'I care about you, but I don't feel comfortable talking about [person]. How can I support you in a positive way?' True friendship doesn't require you to participate in harmful behavior."
            },
            "constant-venting": {
                title: "One-Sided Emotional Dumping",
                situation: "A friend constantly shares their problems and emotions but never asks about you or listens when you try to share. You feel like an emotional support service.",
                biblicalPrinciple: "Proverbs 25:17 - 'Seldom set foot in your neighbor's house—too much of you, and they will hate you.' (Even good relationships need boundaries)",
                healthyResponse: "Healthy friendships are mutual. You might say: 'I care about what you're going through. I also need our friendship to have space for both of us.' It's okay to limit emotionally draining conversations."
            },
            "guilt-trip": {
                title: "Guilt Trips for Having Your Own Life",
                situation: "When you have other plans or spend time with other people, your friend makes comments like 'I guess I'm not important to you anymore' or 'You've changed.'",
                biblicalPrinciple: "1 Corinthians 7:23 - 'You were bought at a price; do not become slaves of human beings.'",
                healthyResponse: "You're not responsible for managing someone else's insecurities. A caring but firm response: 'I value our friendship and also need space for other relationships and activities. That's healthy for both of us.'"
            },
            "boundary-pushback": {
                title: "Friend Gets Upset at Boundaries",
                situation: "When you try to set a boundary (like needing space, saying no, or asking for something), your friend gets angry, withdraws, or tries to make you feel guilty.",
                biblicalPrinciple: "Galatians 5:1 - 'It is for freedom that Christ has set us free. Stand firm, then, and do not let yourselves be burdened again by a yoke of slavery.'",
                healthyResponse: "Boundaries reveal the health of relationships. Stay calm and consistent: 'I understand you're upset, but this boundary is important for our friendship to be healthy.' A true friend will eventually respect your limits."
            },
            "approval-seeking": {
                title: "Needing Everyone's Approval",
                situation: "You find yourself constantly worried about what others think, changing your opinions or behavior to fit in, or feeling anxious when someone seems upset with you.",
                biblicalPrinciple: "1 Thessalonians 2:4 - 'We are not trying to please people but God, who tests our hearts.'",
                healthyResponse: "Remember whose approval truly matters. Practice saying: 'I can't control what others think of me, but I can stay true to my values.' Focus on being authentic rather than perfect in others' eyes."
            }
        };

        // Load data
        function loadData() {
            try {
                completedInsights = parseInt(localStorage.getItem('squadsense_insights') || '0');
                energyChecks = JSON.parse(localStorage.getItem('squadsense_energy') || '[]');
                friendshipChecks = JSON.parse(localStorage.getItem('squadsense_awareness') || '[]');
                boundaryChecks = JSON.parse(localStorage.getItem('squadsense_boundaries') || '[]');
                interactions = JSON.parse(localStorage.getItem('squadsense_interactions') || '[]');
            } catch (e) {
                console.log('Could not load data');
            }
        }

        // Save data
        function saveData() {
            try {
                localStorage.setItem('squadsense_insights', completedInsights.toString());
                localStorage.setItem('squadsense_energy', JSON.stringify(energyChecks));
                localStorage.setItem('squadsense_awareness', JSON.stringify(friendshipChecks));
                localStorage.setItem('squadsense_boundaries', JSON.stringify(boundaryChecks));
                localStorage.setItem('squadsense_interactions', JSON.stringify(interactions));
            } catch (e) {
                console.log('Could not save data');
            }
        }

        // Initialize app
        function init() {
            loadData();
            setDailyVerse();
            updateProgress();
            displayInteractionHistory();
        }

        function setDailyVerse() {
            const today = new Date().toDateString();
            let savedDate = '';
            let dailyVerse = verses[0];
            
            try {
                savedDate = localStorage.getItem('squadsense_verseDate') || '';
                dailyVerse = JSON.parse(localStorage.getItem('squadsense_verse') || JSON.stringify(verses[0]));
            } catch (e) {
                dailyVerse = verses[0];
            }
            
            if (savedDate !== today) {
                dailyVerse = verses[Math.floor(Math.random() * verses.length)];
                try {
                    localStorage.setItem('squadsense_verse', JSON.stringify(dailyVerse));
                    localStorage.setItem('squadsense_verseDate', today);
                } catch (e) {
                    console.log('Could not save verse');
                }
            }
            
            document.getElementById('verse-text').textContent = '"' + dailyVerse.text + '"';
            document.getElementById('verse-ref').textContent = '- ' + dailyVerse.ref;
        }

        function newVerse() {
            const randomVerse = verses[Math.floor(Math.random() * verses.length)];
            document.getElementById('verse-text').textContent = '"' + randomVerse.text + '"';
            document.getElementById('verse-ref').textContent = '- ' + randomVerse.ref;
            
            try {
                localStorage.setItem('squadsense_verse', JSON.stringify(randomVerse));
            } catch (e) {
                console.log('Could not save verse');
            }
        }

        function showSection(sectionName) {
            // Hide all sections
            const sections = ['dashboard', 'energy', 'friendship', 'boundaries', 'practice', 'tracker'];
            sections.forEach(section => {
                const element = document.getElementById(section);
                if (element) element.classList.add('hidden');
            });
            
            // Show selected section
            const targetSection = document.getElementById(sectionName);
            if (targetSection) {
                targetSection.classList.remove('hidden');
                window.scrollTo(0, 0);
                
                if (sectionName === 'tracker') {
                    displayInteractionHistory();
                }
            }
        }

        function loadScenario() {
            const selector = document.getElementById('scenario-selector');
            const scenarioKey = selector.value;
            const contentDiv = document.getElementById('scenario-content');
            const responseDiv = document.getElementById('practice-response');
            const feedbackDiv = document.getElementById('feedback-content');
            
            if (!scenarioKey) {
                contentDiv.innerHTML = '';
                responseDiv.style.display = 'none';
                feedbackDiv.innerHTML = '';
                return;
            }
            
            const scenario = scenarios[scenarioKey];
            contentDiv.innerHTML = `
                <div style="background: #f8fafc; padding: 20px; border-radius: 12px; border-left: 4px solid var(--primary);">
                    <h4>${scenario.title}</h4>
                    <p style="margin: 12px 0;"><strong>Situation:</strong> ${scenario.situation}</p>
                    <p style="margin: 12px 0; color: var(--primary); font-weight: 600;"><strong>Biblical Wisdom:</strong> ${scenario.biblicalPrinciple}</p>
                </div>
            `;
            
            responseDiv.style.display = 'block';
            feedbackDiv.innerHTML = '';
            document.getElementById('practice-answer').value = '';
        }

        function getPracticeFeedback() {
            const selector = document.getElementById('scenario-selector');
            const scenarioKey = selector.value;
            const userResponse = document.getElementById('practice-answer').value.trim();
            const feedbackDiv = document.getElementById('feedback-content');
            
            if (!userResponse) {
                alert('Please write your response first! 😊');
                return;
            }
            
            const scenario = scenarios[scenarioKey];
            feedbackDiv.innerHTML = `
                <div style="background: linear-gradient(135deg, #d1fae5 0%, #a7f3d0 100%); padding: 20px; border-radius: 12px; border-left: 4px solid var(--success);">
                    <h4>Biblical Feedback</h4>
                    <p style="margin: 12px 0;"><strong>Healthy Approach:</strong> ${scenario.healthyResponse}</p>
                    <p style="margin: 12px 0; font-style: italic;">Great job thinking through this scenario! Remember, healthy boundaries honor both yourself and others. God calls us to wisdom, not people-pleasing.</p>
                </div>
            `;
            
            // Save the practice
            completedInsights++;
            saveData();
            updateProgress();
            
            alert('Feedback provided! You\'re building wisdom for real-life situations! 🎭');
        }

        function selectEnergy(level) {
            // Clear previous selections in energy section
            document.querySelectorAll('#energy .rating-number').forEach(num => {
                num.classList.remove('selected');
            });
            // Select current
            event.target.classList.add('selected');
        }

        function selectAnxiety(level) {
            currentAnxiety = level;
            document.querySelectorAll('#anxiety-scale .rating-number').forEach(num => {
                num.classList.remove('selected');
            });
            event.target.classList.add('selected');
        }

        function selectInteractionEnergy(level) {
            currentInteractionEnergy = level;
            document.querySelectorAll('#energy-scale .rating-number').forEach(num => {
                num.classList.remove('selected');
            });
            event.target.classList.add('selected');
        }

        function saveEnergyCheck() {
            const reflection = document.getElementById('energy-reflection').value.trim();
            const selectedEnergy = document.querySelector('#energy .rating-number.selected');
            
            if (reflection && selectedEnergy) {
                const entry = {
                    date: new Date().toLocaleDateString(),
                    level: selectedEnergy.textContent,
                    reflection: reflection
                };
                energyChecks.push(entry);
                completedInsights++;
                saveData();
                updateProgress();
                document.getElementById('energy-reflection').value = '';
                selectedEnergy.classList.remove('selected');
                alert('Energy check saved! You\'re building great self-awareness! ⚡');
            } else {
                alert('Please rate your energy level and share what\'s affecting it! 😊');
            }
        }

        function saveFriendshipCheck() {
            const reflection = document.getElementById('friendship-reflection').value.trim();
            
            if (reflection) {
                const entry = {
                    date: new Date().toLocaleDateString(),
                    reflection: reflection
                };
                friendshipChecks.push(entry);
                completedInsights++;
                saveData();
                updateProgress();
                document.getElementById('friendship-reflection').value = '';
                alert('Friendship insights saved! You\'re developing wisdom about relationships! 💭');
            } else {
                alert('Please share your thoughts about friendship patterns! 💫');
            }
        }

        function saveBoundaryCheck() {
            const reflection = document.getElementById('boundary-reflection').value.trim();
            
            if (reflection) {
                const entry = {
                    date: new Date().toLocaleDateString(),
                    reflection: reflection
                };
                boundaryChecks.push(entry);
                completedInsights++;
                saveData();
                updateProgress();
                document.getElementById('boundary-reflection').value = '';
                alert('Boundary insight saved! You\'re learning to protect your heart wisely! 🛡️');
            } else {
                alert('Please explore what boundary might be helpful! 🌟');
            }
        }

        function saveInteractionInsight() {
            const notes = document.getElementById('interaction-notes').value.trim();
            
            if (currentAnxiety && currentInteractionEnergy && notes) {
                const entry = {
                    date: new Date().toLocaleDateString(),
                    time: new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'}),
                    anxiety: currentAnxiety,
                    energy: currentInteractionEnergy,
                    notes: notes
                };
                interactions.push(entry);
                completedInsights++;
                saveData();
                updateProgress();
                
                // Clear form
                document.getElementById('interaction-notes').value = '';
                document.querySelectorAll('.rating-number.selected').forEach(num => {
                    num.classList.remove('selected');
                });
                currentAnxiety = 0;
                currentInteractionEnergy = 0;
                
                displayInteractionHistory();
                alert('Interaction insight saved! You\'re tracking patterns like a pro! 📱');
            } else {
                alert('Please rate your anxiety, energy, and share your experience! 🌟');
            }
        }

        function displayInteractionHistory() {
            const container = document.getElementById('interaction-history');
            if (!container) return;
            
            if (interactions.length === 0) {
                container.innerHTML = '<p style="text-align: center; color: var(--gray); padding: 20px;">Your insights will appear here as you track interactions</p>';
                return;
            }
            
            const recentInteractions = interactions.slice(-5).reverse(); // Show last 5, newest first
            
            container.innerHTML = recentInteractions.map(interaction => {
                const anxietyColor = interaction.anxiety <= 2 ? '#10b981' : interaction.anxiety <= 3 ? '#f59e0b' : '#ef4444';
                const energyColor = interaction.energy <= 2 ? '#ef4444' : interaction.energy <= 3 ? '#f59e0b' : '#10b981';
                
                return `
                    <div class="interaction-entry">
                        <div class="interaction-header">
                            <span><strong>${interaction.date}</strong> at ${interaction.time}</span>
                        </div>
                        <div style="display: flex; gap: 20px; margin-bottom: 12px;">
                            <span style="color: ${anxietyColor}; font-weight: 600;">Anxiety: ${interaction.anxiety}/5</span>
                            <span style="color: ${energyColor}; font-weight: 600;">Energy: ${interaction.energy}/5</span>
                        </div>
                        <p style="margin: 0; font-style: italic; color: var(--gray);">"${interaction.notes}"</p>
                    </div>
                `;
            }).join('');
        }

        function updateProgress() {
            const progressFill = document.getElementById('progress-fill');
            const progressText = document.getElementById('progress-text');
            
            const percentage = Math.min((completedInsights / 10) * 100, 100);
            
            if (progressFill) progressFill.style.width = percentage + '%';
            if (progressText) progressText.textContent = completedInsights + '/10 insights recorded';
            
            // Celebration for milestones
            if (completedInsights === 3) {
                setTimeout(() => alert('🌟 Amazing! You\'re building incredible self-awareness!'), 500);
            } else if (completedInsights === 7) {
                setTimeout(() => alert('✨ Fantastic progress! You\'re developing real wisdom about relationships!'), 500);
            } else if (completedInsights >= 10) {
                setTimeout(() => alert('🏆 Incredible! You\'ve completed 10+ insights! You\'re becoming a master of healthy boundaries!'), 500);
            }
        }

        // Initialize when page loads
        document.addEventListener('DOMContentLoaded', init);
        
        if (document.readyState === 'loading') {
            document.addEventListener('DOMContentLoaded', init);
        } else {
            init();
        }
    </script>
</body>
</html>
