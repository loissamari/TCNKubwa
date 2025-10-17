<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TCN Kubwa Strategy Hub</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .header {
            text-align: center;
            color: white;
            margin-bottom: 40px;
            padding: 40px 20px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            font-weight: 700;
        }

        .header p {
            font-size: 1.2em;
            opacity: 0.9;
        }

        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }

        .card {
            background: white;
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, #667eea, #764ba2);
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.3);
        }

        .card-icon {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 28px;
            margin-bottom: 20px;
        }

        .card h2 {
            color: #2d3748;
            font-size: 1.5em;
            margin-bottom: 12px;
        }

        .card p {
            color: #718096;
            line-height: 1.6;
            margin-bottom: 20px;
        }

        .card-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding-top: 15px;
            border-top: 1px solid #e2e8f0;
        }

        .card-meta span {
            font-size: 0.85em;
            color: #a0aec0;
        }

        .btn {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 10px 20px;
            border-radius: 8px;
            text-decoration: none;
            font-weight: 600;
            transition: opacity 0.3s ease;
            display: inline-block;
        }

        .btn:hover {
            opacity: 0.9;
        }

        .phase-badge {
            display: inline-block;
            background: #edf2f7;
            color: #4a5568;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.85em;
            font-weight: 600;
            margin-bottom: 10px;
        }

        .footer {
            text-align: center;
            color: white;
            padding: 30px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            margin-top: 40px;
        }

        @media (max-width: 768px) {
            .header h1 {
                font-size: 1.8em;
            }
            
            .cards-grid {
                grid-template-columns: 1fr;
            }
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 1000;
            padding: 20px;
            overflow-y: auto;
        }

        .modal.active {
            display: block;
        }

        .modal-content {
            background: white;
            max-width: 900px;
            margin: 50px auto;
            padding: 40px;
            border-radius: 15px;
            position: relative;
        }

        .close-modal {
            position: absolute;
            top: 20px;
            right: 30px;
            font-size: 30px;
            cursor: pointer;
            color: #718096;
            transition: color 0.3s;
            background: none;
            border: none;
        }

        .close-modal:hover {
            color: #2d3748;
        }

        .modal-content h2 {
            color: #2d3748;
            margin-bottom: 20px;
            font-size: 2em;
        }

        .modal-content h3 {
            color: #4a5568;
            margin-top: 30px;
            margin-bottom: 15px;
            font-size: 1.4em;
        }

        .modal-content ul {
            margin-left: 20px;
            margin-bottom: 20px;
        }

        .modal-content li {
            margin-bottom: 10px;
            color: #4a5568;
            line-height: 1.6;
        }

        .modal-content p {
            color: #4a5568;
            line-height: 1.8;
            margin-bottom: 15px;
        }

        .modal-content strong {
            color: #2d3748;
        }

        .checklist-item {
            background: #f7fafc;
            padding: 12px;
            margin-bottom: 8px;
            border-radius: 8px;
            border-left: 3px solid #667eea;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🏛️ TCN Kubwa Strategy Hub</h1>
            <p>Your Complete Brand & Social Media Roadmap</p>
        </div>

        <div class="cards-grid">
            <div class="card" onclick="openModal('modal1')">
                <div class="card-icon">📋</div>
                <span class="phase-badge">OVERVIEW</span>
                <h2>Executive Summary</h2>
                <p>Current state analysis, target audience, and strategic approach overview.</p>
                <div class="card-meta">
                    <span>⏱️ 5 min read</span>
                    <span class="btn">View →</span>
                </div>
            </div>

            <div class="card" onclick="openModal('modal2')">
                <div class="card-icon">🏗️</div>
                <span class="phase-badge">PHASE 1</span>
                <h2>Foundation (Weeks 1-2)</h2>
                <p>Dual brand architecture, account setup, and brand identity quick wins.</p>
                <div class="card-meta">
                    <span>⏱️ 8 min read</span>
                    <span class="btn">View →</span>
                </div>
            </div>

            <div class="card" onclick="openModal('modal3')">
                <div class="card-icon">📝</div>
                <span class="phase-badge">PHASE 2</span>
                <h2>Content Strategy (90 Days)</h2>
                <p>Content pillars for both @tcnkubwa and @pstdreze with detailed breakdowns.</p>
                <div class="card-meta">
                    <span>⏱️ 12 min read</span>
                    <span class="btn">View →</span>
                </div>
            </div>

            <div class="card" onclick="openModal('modal4')">
                <div class="card-icon">📱</div>
                <span class="phase-badge">PHASE 3</span>
                <h2>Instagram Execution</h2>
                <p>Complete posting schedules, content creation framework, and optimization tactics.</p>
                <div class="card-meta">
                    <span>⏱️ 10 min read</span>
                    <span class="btn">View →</span>
                </div>
            </div>

            <div class="card" onclick="openModal('modal5')">
                <div class="card-icon">💬</div>
                <span class="phase-badge">PHASE 4</span>
                <h2>WhatsApp Integration</h2>
                <p>Broadcast channels, community groups, and Instagram-WhatsApp funnel strategy.</p>
                <div class="card-meta">
                    <span>⏱️ 15 min read</span>
                    <span class="btn">View →</span>
                </div>
            </div>

            <div class="card" onclick="openModal('modal6')">
                <div class="card-icon">📈</div>
                <span class="phase-badge">PHASE 5</span>
                <h2>Growth & Measurement</h2>
                <p>KPIs, growth tactics, metrics tracking, and success factors.</p>
                <div class="card-meta">
                    <span>⏱️ 10 min read</span>
                    <span class="btn">View →</span>
                </div>
            </div>

            <div class="card" onclick="openModal('modal7')">
                <div class="card-icon">✅</div>
                <span class="phase-badge">ACTION PLAN</span>
                <h2>Immediate Checklist</h2>
                <p>Week-by-week action items to get started immediately.</p>
                <div class="card-meta">
                    <span>⏱️ 7 min read</span>
                    <span class="btn">View →</span>
                </div>
            </div>

            <div class="card" onclick="openModal('modal8')">
                <div class="card-icon">🛠️</div>
                <span class="phase-badge">RESOURCES</span>
                <h2>Tools & Resources</h2>
                <p>Essential tools, team structure, and equipment needed for execution.</p>
                <div class="card-meta">
                    <span>⏱️ 5 min read</span>
                    <span class="btn">View →</span>
                </div>
            </div>
        </div>

        <div class="footer">
            <p><strong>Strategy prepared for:</strong> The Covenant Nation (TCN) Kubwa Branch</p>
            <p><strong>Resident Pastor:</strong> Pst Dr Eze</p>
            <p style="margin-top: 20px; opacity: 0.8;">Let's build something amazing! 🚀✨</p>
        </div>
    </div>

    <div id="modal1" class="modal">
        <div class="modal-content">
            <button class="close-modal" onclick="closeModal('modal1')">&times;</button>
            <h2>📋 Executive Summary</h2>
            
            <h3>Current State</h3>
            <ul>
                <li><strong>Church:</strong> The Covenant Nation (TCN) Kubwa Branch</li>
                <li><strong>Resident Pastor:</strong> Pst Dr Eze</li>
                <li><strong>Target Audience:</strong> Young professionals, singles, young families (21-45 years)</li>
                <li><strong>Instagram Followers:</strong> Less than 200</li>
                <li><strong>Engagement:</strong> Currently poor</li>
            </ul>

            <h3>Core Positioning</h3>
            <p><strong>"Community-oriented growth in the Word of God"</strong></p>
            <p>TCN Kubwa is positioned as a warm, inviting space for all ages with particular strength in serving the 21-45 demographic. The church provides solid biblical teaching, career and family building support, and genuine community atmosphere.</p>

            <h3>Primary Challenges</h3>
            <ul>
                <li>Low brand awareness in Kubwa and environs</li>
                <li>Minimal social media engagement</li>
                <li>Need to attract new members while retaining current ones</li>
                <li>Competition from other churches (though most aren't strong online)</li>
            </ul>

            <h3>Strategic Approach</h3>
            <p><strong>Dual-brand architecture with integrated Instagram + WhatsApp ecosystem</strong></p>
            <p>We'll run two interconnected brands:</p>
            <ul>
                <li><strong>@tcnkubwa</strong> - The church community brand ("we")</li>
                <li><strong>@pstdreze</strong> - Pastor's personal teaching brand ("I")</li>
            </ul>
        </div>
    </div>

    <div id="modal2" class="modal">
        <div class="modal-content">
            <button class="close-modal" onclick="closeModal('modal2')">&times;</button>
            <h2>🏗️ Phase 1: Foundation (Weeks 1-2)</h2>
            
            <h3>A. Dual Brand Architecture</h3>
            
            <p><strong>Brand 1: @tcnkubwa (Church Brand)</strong></p>
            <ul>
                <li><strong>Purpose:</strong> The community, the experience, the "we"</li>
                <li><strong>Positioning:</strong> "Your Community. Your Growth. Your Home."</li>
                <li><strong>Platforms:</strong> Instagram + WhatsApp</li>
            </ul>

            <p><strong>Brand 2: @pstdreze (Pastor's Personal Brand)</strong></p>
            <ul>
                <li><strong>Purpose:</strong> His voice, his teaching, the "I"</li>
                <li><strong>Positioning:</strong> "The Teachable Teacher"</li>
                <li><strong>Platforms:</strong> Instagram (3-4x/week) + WhatsApp (daily)</li>
            </ul>

            <h3>Week 1-2 Deliverables</h3>
            <div class="checklist-item">✓ Finalize brand positioning statements</div>
            <div class="checklist-item">✓ Set up both Instagram accounts</div>
            <div class="checklist-item">✓ Design templates</div>
            <div class="checklist-item">✓ Get pastor's buy-in</div>
        </div>
    </div>

    <div id="modal3" class="modal">
        <div class="modal-content">
            <button class="close-modal" onclick="closeModal('modal3')">&times;</button>
            <h2>📝 Phase 2: Content Strategy (90 Days)</h2>
            
            <h3>TCN KUBWA Content Pillars</h3>
            
            <p><strong>1. COMMUNITY (30%)</strong></p>
            <ul>
                <li>Service highlights with story-focused narrative</li>
                <li>Member spotlights</li>
                <li>Behind-the-scenes content</li>
            </ul>

            <p><strong>2. GROWTH (40%)</strong></p>
            <ul>
                <li>Sermon clips (30-60 seconds)</li>
                <li>Weekly devotionals</li>
                <li>Testimony Tuesdays</li>
            </ul>

            <p><strong>3. PRACTICAL LIFE (20%)</strong></p>
            <ul>
                <li>Career tips through biblical lens</li>
                <li>Marriage/relationship wisdom</li>
                <li>Financial stewardship</li>
            </ul>

            <p><strong>4. INVITATION (10%)</strong></p>
            <ul>
                <li>Service reminders</li>
                <li>Event announcements</li>
                <li>New visitor info</li>
            </ul>
        </div>
    </div>

    <div id="modal4" class="modal">
        <div class="modal-content">
            <button class="close-modal" onclick="closeModal('modal4')">&times;</button>
            <h2>📱 Phase 3: Instagram Execution</h2>
            
            <h3>TCN Kubwa Posting Schedule</h3>
            <ul>
                <li><strong>Monday:</strong> Motivation from Sunday sermon</li>
                <li><strong>Tuesday:</strong> Testimony Tuesday</li>
                <li><strong>Wednesday:</strong> Midweek service reminder</li>
                <li><strong>Thursday:</strong> Practical life content</li>
                <li><strong>Friday:</strong> Community/BTS content</li>
                <li><strong>Saturday:</strong> Sunday invitation</li>
                <li><strong>Sunday:</strong> Service highlights</li>
            </ul>

            <h3>Pst Dr Eze Schedule</h3>
            <ul>
                <li>3-4 posts per week</li>
                <li>Daily stories with BTS content</li>
                <li>Q&A sessions</li>
                <li>Teaching clips</li>
            </ul>
        </div>
    </div>

    <div id="modal5" class="modal">
        <div class="modal-content">
            <button class="close-modal" onclick="closeModal('modal5')">&times;</button>
            <h2>💬 Phase 4: WhatsApp Integration</h2>
            
            <h3>Two-Tier WhatsApp System</h3>
            
            <p><strong>TIER 1: Broadcast Channels</strong></p>
            <ul>
                <li>TCN Kubwa Official Channel</li>
                <li>Pst Dr Eze Devotional Channel</li>
            </ul>

            <p><strong>TIER 2: Community Groups</strong></p>
            <ul>
                <li>General TCN Kubwa Community</li>
                <li>Young Professionals Group</li>
                <li>Singles Group</li>
                <li>Young Families Group</li>
                <li>Leadership/Workforce Groups</li>
            </ul>

            <h3>Content Repurposing</h3>
            <p>One sermon creates:</p>
            <ul>
                <li>5-7 Instagram clips</li>
                <li>3-5 quote graphics</li>
                <li>Daily devotionals</li>
                <li>Discussion questions</li>
            </ul>
        </div>
    </div>

    <div id="modal6" class="modal">
        <div class="modal-content">
            <button class="close-modal" onclick="closeModal('modal6')">&times;</button>
            <h2>📈 Phase 5: Growth & Measurement</h2>
            
            <h3>Month 1 Goals</h3>
            <ul>
                <li>Instagram: 300+ followers @tcnkubwa</li>
                <li>Instagram: 150+ followers @pstdreze</li>
                <li>WhatsApp: 200+ broadcast subscribers</li>
                <li>Engagement rate: 5%+</li>
            </ul>

            <h3>Month 3 Goals</h3>
            <ul>
                <li>Instagram: 800+ followers @tcnkubwa</li>
                <li>Instagram: 400+ followers @pstdreze</li>
                <li>WhatsApp: 600+ broadcast subscribers</li>
                <li>Engagement rate: 10%+</li>
                <li>5+ new visitors per week from social media</li>
            </ul>

            <h3>Growth Tactics</h3>
            <ul>
                <li>Consistent daily posting</li>
                <li>2-hour comment response time</li>
                <li>Strategic hashtags (15-20 per post)</li>
                <li>Member tagging</li>
                <li>Daily stories (5-7 per day)</li>
                <li>Reels priority</li>
            </ul>
        </div>
    </div>

    <div id="modal7" class="modal">
        <div class="modal-content">
            <button class="close-modal" onclick="closeModal('modal7')">&times;</button>
            <h2>✅ Immediate Action Checklist</h2>
            
            <h3>Week 1 Tasks</h3>
            <div class="checklist-item">□ Audit and optimize @tcnkubwa account</div>
            <div class="checklist-item">□ Set up @pstdreze account</div>
            <div class="checklist-item">□ Create 5 story highlights</div>
            <div class="checklist-item">□ Design highlight covers</div>
            <div class="checklist-item">□ Create TCN Kubwa WhatsApp Broadcast</div>
            <div class="checklist-item">□ Create Pst Dr Eze WhatsApp Broadcast</div>
            <div class="checklist-item">□ Pre-write 7 days of devotionals</div>
            <div class="checklist-item">□ Plan Sunday content capture</div>

            <h3>Week 2 Tasks</h3>
            <div class="checklist-item">□ Launch Pst Dr Eze IG with 3 posts</div>
            <div class="checklist-item">□ Begin daily WhatsApp devotionals</div>
            <div class="checklist-item">□ Start TCN Kubwa posting schedule</div>
            <div class="checklist-item">□ Announce WhatsApp from pulpit</div>
            <div class="checklist-item">□ Place QR codes around church</div>
            <div class="checklist-item">□ Invite first 50 members to community group</div>
        </div>
    </div>

    <div id="modal8" class="modal">
        <div class="modal-content">
            <button class="close-modal" onclick="closeModal('modal8')">&times;</button>
            <h2>🛠️ Tools & Resources</h2>
            
            <h3>Essential Tools</h3>
            <ul>
                <li><strong>Canva Pro</strong> - Graphic design</li>
                <li><strong>CapCut/InShot</strong> - Video editing</li>
                <li><strong>Later/Buffer</strong> - Scheduling (optional)</li>
                <li><strong>Google Drive</strong> - Content storage</li>
                <li><strong>WhatsApp Business</strong> - Community management</li>
            </ul>

            <h3>Equipment Needed</h3>
            <ul>
                <li>High-quality smartphone</li>
                <li>Ring light (optional but helpful)</li>
                <li>Lapel microphone (optional)</li>
                <li>Tripod or stabilizer</li>
            </ul>

            <h3>Team Structure</h3>
            <ul>
                <li><strong>Social Media Manager</strong> - Strategy & oversight</li>
                <li><strong>Content Creator</strong> - Graphics & video</li>
                <li><strong>Photographer</strong> - Sunday capture</li>
                <li><strong>Community Manager</strong> - WhatsApp moderation</li>
            </ul>
        </div>
    </div>

    <script>
        function openModal(modalId) {
            document.getElementById(modalId).classList.add('active');
            document.body.style.overflow = 'hidden';
        }

        function closeModal(modalId) {
            document.getElementById(modalId).classList.remove('active');
            document.body.style.overflow = 'auto';
        }

        document.querySelectorAll('.modal').forEach(modal => {
            modal.addEventListener('click', function(e) {
                if (e.target === this) {
                    closeModal(this.id);
                }
            });
        });
    </script>
</body>
</html>
