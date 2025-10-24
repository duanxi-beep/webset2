<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>E海导航：网络道德图鉴与价值明灯</title>
    <style>
        /* 全局样式 */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Microsoft YaHei', 'Segoe UI', sans-serif;
        }
        
        :root {
            --primary-blue: #1a6bc4;
            --light-blue: #4a90e2;
            --dark-blue: #0d47a1;
            --white: #ffffff;
            --warning-red: #e53935;
            --hope-green: #43a047;
            --warm-yellow: #ffb300;
            --gray: #f5f5f5;
            --dark-gray: #424242;
        }
        
        body {
            color: #333;
            line-height: 1.6;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        section {
            padding: 80px 0;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        
        h1, h2, h3 {
            color: var(--dark-blue);
            margin-bottom: 20px;
        }
        
        /* 导航栏样式 */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            background-color: rgba(255, 255, 255, 0.95);
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            z-index: 1000;
            transition: all 0.3s ease;
        }
        
        nav.scrolled {
            background-color: var(--white);
            padding: 5px 0;
        }
        
        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 20px;
        }
        
        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--primary-blue);
        }
        
        .nav-links {
            display: flex;
            list-style: none;
        }
        
        .nav-links li {
            margin-left: 30px;
        }
        
        .nav-links a {
            text-decoration: none;
            color: var(--dark-blue);
            font-weight: 500;
            transition: color 0.3s;
        }
        
        .nav-links a:hover {
            color: var(--light-blue);
        }
        
        /* 首页/引航区样式 */
        #hero {
            background: linear-gradient(135deg, var(--primary-blue) 0%, var(--dark-blue) 100%);
            color: var(--white);
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .hero-content {
            z-index: 2;
            position: relative;
        }
        
        #hero h1 {
            font-size: 3rem;
            margin-bottom: 20px;
            color: var(--white);
        }
        
        #hero p {
            font-size: 1.5rem;
            margin-bottom: 30px;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .compass {
            width: 200px;
            height: 200px;
            margin: 40px auto;
            position: relative;
        }
        
        .compass-circle {
            width: 100%;
            height: 100%;
            border: 3px solid var(--white);
            border-radius: 50%;
            position: relative;
            animation: rotate 20s linear infinite;
        }
        
        .compass-needle {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 4px;
            height: 80px;
            background-color: var(--warning-red);
            border-radius: 2px;
        }
        
        .compass-needle::after {
            content: '';
            position: absolute;
            top: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 0;
            height: 0;
            border-left: 8px solid transparent;
            border-right: 8px solid transparent;
            border-bottom: 10px solid var(--warning-red);
        }
        
        .moral-keywords {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 30px;
        }
        
        .keyword {
            background-color: rgba(255, 255, 255, 0.2);
            padding: 10px 20px;
            border-radius: 30px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .keyword:hover {
            background-color: rgba(255, 255, 255, 0.3);
            transform: translateY(-3px);
        }
        
        /* 现象图鉴区样式 */
        #phenomena {
            background-color: var(--gray);
        }
        
        .card-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 30px;
            margin-top: 40px;
        }
        
        .card {
            background-color: var(--white);
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            width: 300px;
            overflow: hidden;
            transition: transform 0.3s, box-shadow 0.3s;
            cursor: pointer;
        }
        
        .card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
        }
        
        .card-icon {
            height: 150px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
            color: var(--warning-red);
        }
        
        .card-content {
            padding: 20px;
        }
        
        .card h3 {
            margin-bottom: 10px;
            color: var(--dark-blue);
        }
        
        .detail-panel {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            z-index: 2000;
            justify-content: center;
            align-items: center;
        }
        
        .detail-content {
            background-color: var(--white);
            width: 90%;
            max-width: 800px;
            max-height: 90%;
            overflow-y: auto;
            border-radius: 10px;
            padding: 30px;
            position: relative;
        }
        
        .close-btn {
            position: absolute;
            top: 15px;
            right: 15px;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--dark-gray);
        }
        
        /* 价值明灯区样式 */
        #values {
            background: linear-gradient(135deg, var(--hope-green) 0%, var(--light-blue) 100%);
            color: var(--white);
        }
        
        #values h2, #values h3 {
            color: var(--white);
        }
        
        .value-card {
            background-color: rgba(255, 255, 255, 0.9);
            color: var(--dark-gray);
            border-radius: 10px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        /* 理论灯塔区样式 */
        #theory {
            background-color: var(--white);
        }
        
        .theory-item {
            margin-bottom: 30px;
            border-left: 4px solid var(--primary-blue);
            padding-left: 20px;
        }
        
        /* 互动航海日志区样式 */
        #interaction {
            background-color: var(--gray);
        }
        
        .reflection-wall {
            background-color: var(--white);
            border-radius: 10px;
            padding: 30px;
            margin-bottom: 30px;
            min-height: 200px;
            max-height: 300px;
            overflow-y: auto;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .reflection-input {
            display: flex;
            margin-bottom: 20px;
        }
        
        .reflection-input textarea {
            flex: 1;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 5px;
            resize: vertical;
            min-height: 100px;
        }
        
        .reflection-input button {
            margin-left: 10px;
            padding: 0 20px;
            background-color: var(--primary-blue);
            color: var(--white);
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .reflection-input button:hover {
            background-color: var(--dark-blue);
        }
        
        .pledge-section {
            text-align: center;
            margin-top: 50px;
        }
        
        .pledge-btn {
            background-color: var(--hope-green);
            color: var(--white);
            border: none;
            padding: 15px 30px;
            font-size: 1.2rem;
            border-radius: 30px;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .pledge-btn:hover {
            background-color: #388e3c;
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.25);
        }
        
        .stars-container {
            display: flex;
            justify-content: center;
            margin-top: 30px;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .star {
            font-size: 2rem;
            color: #ddd;
            transition: color 0.5s;
        }
        
        .star.lit {
            color: var(--warm-yellow);
        }
        
        /* 动画 */
        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0px); }
        }
        
        .floating {
            animation: float 5s ease-in-out infinite;
        }
        
        /* 响应式设计 */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }
            
            #hero h1 {
                font-size: 2rem;
            }
            
            #hero p {
                font-size: 1.2rem;
            }
            
            .compass {
                width: 150px;
                height: 150px;
            }
            
            .card {
                width: 100%;
                max-width: 300px;
            }
        }
    </style>
</head>
<body>
    <!-- 导航栏 -->
    <nav id="navbar">
        <div class="nav-container">
            <div class="logo">E海导航</div>
            <ul class="nav-links">
                <li><a href="#hero">首页</a></li>
                <li><a href="#phenomena">暗礁探测</a></li>
                <li><a href="#values">明灯指引</a></li>
                <li><a href="#theory">知识灯塔</a></li>
                <li><a href="#interaction">航海日志</a></li>
            </ul>
        </div>
    </nav>

    <!-- 首页/引航区 -->
    <section id="hero">
        <div class="container">
            <div class="hero-content">
                <h1>E海导航：网络道德图鉴与价值明灯</h1>
                <p>穿梭数据浪潮，守护内心灯塔</p>
                
                <div class="compass">
                    <div class="compass-circle floating">
                        <div class="compass-needle"></div>
                    </div>
                </div>
                
                <p>在匿名的海洋里，我们如何选择成为怎样的水手？</p>
                
                <div class="moral-keywords">
                    <div class="keyword" data-target="privacy">隐私</div>
                    <div class="keyword" data-target="violence">暴力</div>
                    <div class="keyword" data-target="integrity">诚信</div>
                    <div class="keyword" data-target="respect">尊重</div>
                    <div class="keyword" data-target="responsibility">责任</div>
                </div>
            </div>
        </div>
    </section>

    <!-- 现象图鉴区 -->
    <section id="phenomena">
        <div class="container">
            <h2>第一章：暗礁探测 - 网络道德现象图鉴</h2>
            <p>识别网络海洋中的道德暗礁，避免触碰危险</p>
            
            <div class="card-container">
                <div class="card" data-detail="violence">
                    <div class="card-icon">💬</div>
                    <div class="card-content">
                        <h3>网络暴力的漩涡</h3>
                        <p>匿名环境下的言语攻击、人身威胁和群体欺凌现象</p>
                    </div>
                </div>
                
                <div class="card" data-detail="privacy">
                    <div class="card-icon">🔑</div>
                    <div class="card-content">
                        <h3>隐私泄露的暗流</h3>
                        <p>个人信息被非法收集、使用和传播的风险</p>
                    </div>
                </div>
                
                <div class="card" data-detail="misinformation">
                    <div class="card-icon">❓</div>
                    <div class="card-content">
                        <h3>虚假信息的迷雾</h3>
                        <p>谣言、假新闻和不实信息在网络中快速传播</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 价值明灯区 -->
    <section id="values">
        <div class="container">
            <h2>第二章：明灯指引 - 我们的价值坚守</h2>
            <p>在数据海洋中点亮道德明灯，指引正确航向</p>
            
            <div class="value-card">
                <h3>尊重之光，穿透暴力漩涡</h3>
                <p>在网络交流中保持尊重，不参与或传播网络暴力，对他人保持善意和理解。</p>
                <p><strong>行动指南：</strong>发表评论前思考三秒，不使用攻击性语言，举报网络欺凌行为。</p>
                <p><strong>正能量案例：</strong>疫情期间，许多网友自发组织线上互助小组，传递温暖与支持。</p>
            </div>
            
            <div class="value-card">
                <h3>诚信之塔，驱散信息迷雾</h3>
                <p>传播真实信息，不制造或散布谣言，对不确定的信息保持审慎态度。</p>
                <p><strong>行动指南：</strong>转发前核实信息来源，标注不确定内容，纠正已发现的错误信息。</p>
                <p><strong>正能量案例：</strong>多家媒体和平台联合推出"辟谣平台"，有效遏制假新闻传播。</p>
            </div>
            
            <div class="value-card">
                <h3>责任之盾，守护隐私暗流</h3>
                <p>保护自己和他人的隐私，不非法收集或泄露个人信息。</p>
                <p><strong>行动指南：</strong>设置强密码，谨慎授权应用权限，不随意公开他人信息。</p>
                <p><strong>相关法规：</strong>《中华人民共和国个人信息保护法》于2021年11月1日正式施行。</p>
            </div>
        </div>
    </section>

    <!-- 理论灯塔区 -->
    <section id="theory">
        <div class="container">
            <h2>第三章：知识灯塔 - 理论照进现实</h2>
            <p>用理论知识解析网络道德现象，为价值坚守提供理论支撑</p>
            
            <div class="theory-item">
                <h3>沉默的螺旋理论</h3>
                <p>解释了为何在网络环境中，少数意见持有者可能因害怕孤立而选择沉默，从而导致多数意见看似更加强大。这凸显了尊重多样性、鼓励不同声音的重要性。</p>
            </div>
            
            <div class="theory-item">
                <h3>康德的绝对命令</h3>
                <p>强调行为应当遵循可普遍化的道德法则。在网络空间中，这意味着我们的行为应当能够成为所有人都遵循的准则，从而维护网络环境的秩序与和谐。</p>
            </div>
            
            <div class="theory-item">
                <h3>功利主义</h3>
                <p>主张行为应当追求最大多数人的最大幸福。在网络信息传播中，这意味着我们应当考虑信息传播可能带来的社会影响，避免传播可能造成广泛伤害的内容。</p>
            </div>
            
            <div class="theory-item">
                <h3>群体极化</h3>
                <p>指群体讨论往往会使成员的观点趋向极端。这解释了网络 echo chamber（回音室）现象，提醒我们应当主动接触多元观点，避免陷入信息茧房。</p>
            </div>
        </div>
    </section>

    <!-- 互动航海日志区 -->
    <section id="interaction">
        <div class="container">
            <h2>我的航海日志</h2>
            <p>记录您的网络道德思考与承诺</p>
            
            <div class="reflection-wall" id="reflectionWall">
                <p>欢迎在此分享您的网络道德思考！</p>
            </div>
            
            <div class="reflection-input">
                <textarea id="reflectionInput" placeholder="我遇到过哪些网络道德困境？我将如何坚守价值？"></textarea>
                <button id="submitReflection">提交</button>
            </div>
            
            <div class="pledge-section">
                <h3>网络行为守则承诺</h3>
                <p>我承诺在网络空间中：</p>
                <ul style="list-style: none; margin: 20px 0;">
                    <li>✓ 不传播谣言和虚假信息</li>
                    <li>✓ 不参与网络暴力和人身攻击</li>
                    <li>✓ 尊重他人隐私和个人信息</li>
                    <li>✓ 积极传播正能量和真实信息</li>
                </ul>
                
                <button class="pledge-btn" id="pledgeBtn">我承诺</button>
                
                <div class="stars-container" id="starsContainer">
                    <!-- 星星将通过JavaScript动态添加 -->
                </div>
            </div>
        </div>
    </section>

    <!-- 现象详情浮层 -->
    <div class="detail-panel" id="detailPanel">
        <div class="detail-content" id="detailContent">
            <span class="close-btn" id="closeDetail">×</span>
            <div id="detailBody">
                <!-- 详情内容将通过JavaScript动态加载 -->
            </div>
        </div>
    </div>

    <script>
        // 导航栏滚动效果
        window.addEventListener('scroll', function() {
            const navbar = document.getElementById('navbar');
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });
        
        // 平滑滚动到锚点
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                }
            });
        });
        
        // 道德关键词点击事件
        document.querySelectorAll('.keyword').forEach(keyword => {
            keyword.addEventListener('click', function() {
                const target = this.getAttribute('data-target');
                scrollToPhenomenaCard(target);
            });
        });
        
        // 滚动到对应的现象卡片
        function scrollToPhenomenaCard(target) {
            const phenomenaSection = document.getElementById('phenomena');
            window.scrollTo({
                top: phenomenaSection.offsetTop - 80,
                behavior: 'smooth'
            });
            
            // 高亮对应的卡片（简单实现）
            setTimeout(() => {
                const card = document.querySelector(`.card[data-detail="${target}"]`);
                if (card) {
                    card.style.boxShadow = '0 0 0 3px ' + getComputedStyle(document.documentElement).getPropertyValue('--warning-red');
                    setTimeout(() => {
                        card.style.boxShadow = '';
                    }, 2000);
                }
            }, 800);
        }
        
        // 现象卡片点击显示详情
        const detailPanel = document.getElementById('detailPanel');
        const detailBody = document.getElementById('detailBody');
        const closeDetailBtn = document.getElementById('closeDetail');
        
        document.querySelectorAll('.card').forEach(card => {
            card.addEventListener('click', function() {
                const detailType = this.getAttribute('data-detail');
                showDetail(detailType);
            });
        });
        
        // 显示详情浮层
        function showDetail(type) {
            let title = '';
            let content = '';
            
            switch(type) {
                case 'violence':
                    title = '网络暴力的漩涡';
                    content = `
                        <h2>${title}</h2>
                        <p><strong>现象描述：</strong>在网络匿名环境下，个体或群体通过言语攻击、人身威胁、散布谣言等方式对他人实施伤害。这种现象在社交媒体、论坛和游戏社区中尤为常见。</p>
                        <p><strong>典型案例：</strong>某明星因角色表现不符合部分观众期待，遭受大规模网络攻击，导致心理健康受损退出社交媒体。</p>
                        <p><strong>成因分析：</strong>匿名性降低行为约束、群体效应放大攻击行为、平台监管不足、网络素养教育缺失。</p>
                        <p><strong>社会影响：</strong>受害者心理健康受损、网络环境恶化、言论自由受限、社会信任度下降。</p>
                        <button class="theory-link" data-theory="spiral">相关理论：沉默的螺旋</button>
                    `;
                    break;
                case 'privacy':
                    title = '隐私泄露的暗流';
                    content = `
                        <h2>${title}</h2>
                        <p><strong>现象描述：</strong>个人数据被非法收集、使用和传播，包括身份信息、位置数据、消费习惯等。大数据时代，隐私泄露风险显著增加。</p>
                        <p><strong>典型案例：</strong>某大型社交平台数据泄露事件，影响全球数千万用户，个人信息被用于精准政治广告投放。</p>
                        <p><strong>成因分析：</strong>数据经济价值驱动、技术防护不足、用户意识薄弱、法律法规执行不到位。</p>
                        <p><strong>社会影响：</strong>个人权益受损、诈骗案件增加、社会信任危机、数字经济发展受阻。</p>
                        <button class="theory-link" data-theory="kant">相关理论：康德的绝对命令</button>
                    `;
                    break;
                case 'misinformation':
                    title = '虚假信息的迷雾';
                    content = `
                        <h2>${title}</h2>
                        <p><strong>现象描述：</strong>谣言、假新闻和不实信息通过社交网络快速传播，影响公众判断和决策，尤其在公共卫生事件和紧急情况下危害更大。</p>
                        <p><strong>典型案例：</strong>疫情期间，关于病毒来源、预防措施的虚假信息大量传播，导致恐慌性购买和错误防护行为。</p>
                        <p><strong>成因分析：</strong>信息验证成本高、算法推荐强化偏见、情绪化内容易传播、专业媒体权威下降。</p>
                        <p><strong>社会影响：</strong>公众认知扭曲、社会决策失误、群体对立加剧、应急管理困难。</p>
                        <button class="theory-link" data-theory="polarization">相关理论：群体极化</button>
                    `;
                    break;
            }
            
            detailBody.innerHTML = content;
            detailPanel.style.display = 'flex';
            
            // 添加理论链接事件
            document.querySelectorAll('.theory-link').forEach(link => {
                link.addEventListener('click', function() {
                    const theory = this.getAttribute('data-theory');
                    detailPanel.style.display = 'none';
                    
                    // 滚动到理论部分
                    const theorySection = document.getElementById('theory');
                    window.scrollTo({
                        top: theorySection.offsetTop - 80,
                        behavior: 'smooth'
                    });
                });
            });
        }
        
        // 关闭详情浮层
        closeDetailBtn.addEventListener('click', function() {
            detailPanel.style.display = 'none';
        });
        
        // 点击浮层外部关闭
        detailPanel.addEventListener('click', function(e) {
            if (e.target === detailPanel) {
                detailPanel.style.display = 'none';
            }
        });
        
        // 反思墙功能
        const reflectionWall = document.getElementById('reflectionWall');
        const reflectionInput = document.getElementById('reflectionInput');
        const submitReflection = document.getElementById('submitReflection');
        
        submitReflection.addEventListener('click', function() {
            const text = reflectionInput.value.trim();
            if (text) {
                const reflectionElement = document.createElement('div');
                reflectionElement.className = 'reflection-item';
                reflectionElement.innerHTML = `
                    <p>"${text}"</p>
                    <small>${new Date().toLocaleDateString()}</small>
                    <hr>
                `;
                
                // 如果第一条是欢迎消息，替换它
                if (reflectionWall.children.length === 1 && reflectionWall.children[0].tagName === 'P') {
                    reflectionWall.innerHTML = '';
                }
                
                reflectionWall.appendChild(reflectionElement);
                reflectionInput.value = '';
                
                // 滚动到底部
                reflectionWall.scrollTop = reflectionWall.scrollHeight;
            }
        });
        
        // 承诺按钮功能
        const pledgeBtn = document.getElementById('pledgeBtn');
        const starsContainer = document.getElementById('starsContainer');
        
        pledgeBtn.addEventListener('click', function() {
            // 禁用按钮防止重复点击
            pledgeBtn.disabled = true;
            pledgeBtn.textContent = '已承诺';
            
            // 创建星星动画
            starsContainer.innerHTML = '';
            const starCount = 5;
            
            for (let i = 0; i < starCount; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                star.textContent = '★';
                starsContainer.appendChild(star);
                
                // 延迟点亮星星
                setTimeout(() => {
                    star.classList.add('lit');
                }, i * 300);
            }
            
            // 添加感谢消息
            setTimeout(() => {
                const thanksMsg = document.createElement('p');
                thanksMsg.textContent = '感谢您的承诺！让我们一起建设更美好的网络空间。';
                thanksMsg.style.marginTop = '20px';
                thanksMsg.style.fontWeight = 'bold';
                starsContainer.appendChild(thanksMsg);
            }, starCount * 300 + 500);
        });
        
        // 初始化星星容器
        function initStars() {
            starsContainer.innerHTML = '';
            for (let i = 0; i < 5; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                star.textContent = '★';
                starsContainer.appendChild(star);
            }
        }
        
        // 页面加载完成后初始化
        window.addEventListener('load', function() {
            initStars();
        });
    </script>
</body>
</html>

