<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>Jayden's Research Homepage · 多模态与多语言大模型</title>
    <!-- 
        完全遵从原始设计: 
        - 保留所有布局 (固定侧边栏 + 主内容区)
        - 保留动态渐变动画背景、自定义光标、按钮样式等
        - “关于我”等标题字体保持不变 (inherit from body, 但保证罗马风格)
        - 各模块内部内容字体统一变为 “Times New Roman”, Times, serif (罗马体)
        - 所有正文、描述、论文作者、邮箱、新闻等均使用罗马体
    -->
    <style>
        /* ========== 基础全局: 设定罗马体为核心字体 (覆盖所有正文内容) ========= */
        body, html, .page, .page__content, p, div, li, span, .news-list, .pub-item, .pub-authors, .pub-venue, .pub-title, .edu-item, .exp-item, .honor-list, .reviewer-list, .about-text, .phd-detail, .comm-line, .email-block, .btn {
            font-family: 'Times New Roman', Times, serif !important;
        }
        
        /* 保留特殊标题依然使用罗马体，但无需额外修改 — Times New Roman 也是优雅标题字体 */
        h2, h3, h1, .section-title {
            font-family: 'Times New Roman', Times, serif !important;
            font-weight: 600;
        }
        
        /* 所有内部内容字体确保一致性，包括新闻区域单独定义过，重写覆盖 */
        div[style*="font-family"] {
            font-family: 'Times New Roman', Times, serif !important;
        }
        
        /* 原始样式完全保留，不丢失任何布局/色彩效果 */
        .page {
            width: calc(100% - 310px) !important;
            margin-left: 320px !important;
            padding-right: 20px !important;
        }
        .sidebar {
            width: 320px !important;
            position: fixed !important;
            padding-right: 20px !important;
        }
        #main {
            max-width: 1800px !important;
        }
        .page__content {
            padding-right: 0 !important;
        }
        @media (max-width: 1024px) {
            .page {
                width: 100% !important;
                margin-left: 0 !important;
            }
            .sidebar {
                position: relative !important;
                width: 100% !important;
            }
        }
        .btn--primary {
            background-color: #4dabf7;
            color: #fff;
            padding: 0.25em 0.75em;
            border-radius: 4px;
            display: inline-block;
            font-size: 0.8em;
            text-decoration: none !important;
            margin-left: 10px;
            transition: background-color 0.3s ease;
            border: none;
            font-family: 'Times New Roman', Times, serif !important;
        }
        .btn--second {
            background-color: #F2A7DA;
            color: #fff;
            padding: 0.25em 0.75em;
            border-radius: 4px;
            display: inline-block;
            font-size: 0.8em;
            text-decoration: none !important;
            margin-left: 10px;
            transition: background-color 0.3s ease;
            border: none;
            font-family: 'Times New Roman', Times, serif !important;
        }
        .btn--primary:hover {
            background-color: #339af0;
            text-decoration: none !important;
            color: #fff;
        }
        .btn--second:hover {
            background-color: #D882AD;
            text-decoration: none !important;
            color: #fff;
        }
        /* 确保所有链接无下划线，但保持可读 */
        .page__content a {
            text-decoration: none !important;
        }
        /* 动态渐变动画背景 */
        body {
            background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
            background-size: 400% 400%;
            animation: gradient 15s ease infinite;
            margin: 0;
            padding: 0;
            min-height: 100vh;
        }
        /* 自定义光标 (gif光标) */
        body, html {
            cursor: url('https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExamQ1d2ZjY2c5ZWVyaWRtaHJveTJsMWsxNnFmZzZnZ28zaXZ1amNrciZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/c39G3b12cyqmEhOxib/giphy.gif'), auto;
        }
        @keyframes gradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        .page {
            background-color: rgba(255, 255, 255, 0.92);
            backdrop-filter: blur(5px);
            border-radius: 20px;
            padding: 2rem 2rem 2.5rem 2rem;
            margin-top: 2rem;
            margin-bottom: 2rem;
            box-shadow: 0 20px 35px -12px rgba(0, 0, 0, 0.2);
        }
        /* 文章内微调边距 */
        h2 {
            font-size: 1.8rem;
            margin-top: 1.5rem;
            margin-bottom: 0.8rem;
            border-bottom: 2px solid #dee6ef;
            padding-bottom: 0.3rem;
            font-weight: 600;
            letter-spacing: 0.5px;
        }
        .about-text {
            font-size: 1.02rem;
            line-height: 1.5;
            text-align: justify;
        }
        .research-line, .phd-detail, .comm-line {
            margin-bottom: 0.5rem;
        }
        .email-block {
            margin-top: 0.8rem;
            padding-top: 0.6rem;
            border-top: 1px solid #dfe8f0;
            display: flex;
            flex-wrap: wrap;
            gap: 0.4rem;
        }
        .email-label {
            font-weight: 700;
            color: #1c5a77;
        }
        .news-item {
            display: flex;
            flex-wrap: wrap;
            margin-bottom: 0.6rem;
            font-size: 0.96rem;
            line-height: 1.45;
        }
        .news-date {
            font-weight: bold;
            min-width: 95px;
            color: #2a5f7a;
        }
        .news-content {
            flex: 1;
        }
        .red-num {
            color: #c7254e;
            font-weight: bold;
        }
        .pub-item {
            margin-bottom: 1.2rem;
            padding-left: 0.2rem;
        }
        .pub-title {
            font-size: 1rem;
            font-weight: 700;
            color: #1f5e7e;
            margin: 0.2rem 0 0.2rem;
        }
        .pub-authors {
            font-size: 0.92rem;
            color: #2c3e50;
        }
        .pub-venue {
            font-size: 0.89rem;
            color: #4a627a;
            font-style: italic;
        }
        .pub-links {
            margin-top: 0.3rem;
            display: flex;
            flex-wrap: wrap;
            gap: 0.7rem;
        }
        .edu-item {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: baseline;
            margin-bottom: 0.8rem;
            font-size: 1rem;
            border-bottom: 1px dashed #e9f0f5;
            padding-bottom: 0.4rem;
        }
        .edu-left {
            font-weight: 500;
        }
        .edu-date {
            color: #b22234;
            font-weight: 500;
        }
        .exp-item {
            margin-bottom: 0.75rem;
            font-size: 0.98rem;
        }
        .exp-title {
            font-weight: 700;
            color: #1a4d66;
        }
        .honor-list, .reviewer-list {
            margin-left: 1.2rem;
            margin-bottom: 0.8rem;
            line-height: 1.45;
        }
        .reviewer-list li {
            margin-bottom: 0.3rem;
        }
        .italic-note {
            font-size: 0.85rem;
            color: #5f7486;
            margin-top: 0.2rem;
        }
        .float-gif-area {
            float: right;
            margin-left: 20px;
            margin-bottom: 20px;
            width: 150px;
            border-radius: 12px;
        }
        .float-gif-area img {
            width: 100%;
            border-radius: 12px;
            box-shadow: 0 8px 18px rgba(0,0,0,0.1);
            display: block;
        }
        .clearfix::after {
            content: "";
            clear: both;
            display: table;
        }
        .small-footer {
            font-size: 0.75rem;
            text-align: right;
            margin-top: 1.8rem;
            color: #7e95aa;
            border-top: 1px solid #e2ecf5;
            padding-top: 0.8rem;
        }
        @media (max-width: 680px) {
            .float-gif-area {
                float: none;
                margin: 0 auto 20px auto;
                display: block;
            }
            .news-item {
                flex-direction: column;
            }
            .news-date {
                margin-bottom: 0.2rem;
            }
            .edu-item {
                flex-direction: column;
            }
            .page {
                margin-left: 20px !important;
                margin-right: 20px !important;
                width: auto !important;
            }
            .sidebar {
                position: relative !important;
            }
        }
        /* 保持所有引用链接无下划线且优雅 */
        a {
            color: #1f6d8a;
            transition: 0.2s;
        }
        a:hover {
            color: #0a4f69;
            text-decoration: underline !important;
        }
    </style>
</head>
<body>
    <!-- 仿照学术主页原始结构，使用 .page 容器渲染主要内容 (模拟 academicpages 主题) -->
    <div class="page">
        <!-- 由于原始内容中带有 title 和 author_profile 信息，这里完全保留文本内容 -->
        <div style="margin-bottom: 0.5rem;">
            <h1 style="font-size: 2rem; margin-bottom: 0.25rem;">🤣👉 Hello！this is Jayden's research homepage 👈</h1>
            <div style="font-size: 0.9rem; color: #4a627a;">PhD Candidate @ Xiamen University | Multilingual & Omni LLMs</div>
        </div>
        
        <!-- ========== 📚 About Me 区域 ========= -->
        <h2>📚 About Me</h2>
        <div class="clearfix">
            <div class="float-gif-area">
                <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExcjV0Z3J6d2Y0d3B0dGJ6d2V6Z2J6Z2V6Z2J6Z2V6Z2J6Z2V6ZyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o7qE1YN7aBOFPRw8E/giphy.gif" 
                     alt="Academic animated GIF - neural research">
            </div>
            <div class="about-text">
                <div class="research-line">
                    My research interests cover <strong>Multilingual Large Language Models</strong>, <strong>Multimodal Reasoning</strong>, <strong>Omni Large Language Models</strong>.
                </div>
                <div class="phd-detail">
                    As a PhD candidate at <strong>Xiamen University</strong> and a member of the 
                    <a href="https://xmudeeplit.github.io/" target="_blank" rel="noopener"><strong>DeepLIT</strong></a> Group, 
                    I work under the guidance of Prof. 
                    <a href="https://xmudeeplit.github.io/author/%E8%8B%8F%E5%8A%B2%E6%9D%BE/" target="_blank" rel="noopener"><strong>Jinsong Su</strong></a>.
                </div>
                <div class="comm-line">
                    😁 Feel free to reach out for academic communication.
                </div>
                <div class="email-block">
                    <span class="email-label">📧 Emails:</span>
                    <span><a href="mailto:jayden20010817@163.com">jayden20010817@163.com</a> | <a href="mailto:zhuangxingjie617@gmail.com">zhuangxingjie617@gmail.com</a></span>
                </div>
            </div>
        </div>
        
        <!-- ========== 📣 News 区域 ========= -->
        <h2>📣 News</h2>
        <div class="news-list" style="font-family: 'Times New Roman', Times, serif;">
            <div class="news-item"><span class="news-date">🎉 [04/2026]</span><span class="news-content"><span class="red-num">1</span> paper has been accepted by <strong><em>Information Fusion</em></strong>.</span></div>
            <div class="news-item"><span class="news-date">🎉 [11/2025]</span><span class="news-content">I won a <strong><em>Outstanding Graduate Student Scholarship (only 18 awardees campus-wide)</em></strong>.</span></div>
            <div class="news-item"><span class="news-date">🎉 [10/2025]</span><span class="news-content">I won a <strong><em>National Scholarship</em></strong>.</span></div>
            <div class="news-item"><span class="news-date">🎉 [07/2025]</span><span class="news-content"><span class="red-num">1</span> paper has been accepted by <strong><em>Neural Networks</em></strong>.</span></div>
            <div class="news-item"><span class="news-date">🎉 [05/2025]</span><span class="news-content"><span class="red-num">1</span> paper has been accepted by <strong><em>ACM Transactions on Multimedia Computing, Communications, and Applications (TOMM)</em></strong>.</span></div>
            <div class="news-item"><span class="news-date">🎉 [01/2025]</span><span class="news-content"><span class="red-num">1</span> paper has been accepted by <strong><em>Knowledge-Based Systems (KBS)</em></strong>.</span></div>
            <div class="news-item"><span class="news-date">🎉 [12/2024]</span><span class="news-content"><span class="red-num">1</span> paper has been accepted by <strong><em>Engineering Applications of Artificial Intelligence (EAAI)</em></strong>.</span></div>
            <div class="news-item"><span class="news-date">🎉 [07/2024]</span><span class="news-content"><span class="red-num">1</span> paper has been accepted by <strong><em>CIKM 2024</em></strong>.</span></div>
        </div>
        
        <!-- ========== 📝 Selected Publications ========= -->
        <h2>📝 Selected Publications</h2>
        
        <div class="pub-item">
            <div class="pub-title">🔥 <span style="color:#6CBCD0;"><b>MPF: A Multi-Level Perceiving Framework for Multimodal Sarcasm Detection</b></span></div>
            <div class="pub-authors"><strong>Xingjie Zhuang</strong>, Zhixin Li, Fengling Zhou, Canlong Zhang, Huifang Ma</div>
            <div class="pub-venue"><em>Information Fusion</em> (<strong>JCR Q1</strong>, <strong>CAS Zone 1</strong>)</div>
            <div class="pub-links">
                <a href="https://www.sciencedirect.com/science/article/abs/pii/S1566253526003167" class="btn btn--primary btn--small">📄 Paper</a>
                <a href="https://github.com/JayDen20010817/MPF" class="btn btn--second btn--small">💻 Code</a>
            </div>
        </div>
        
        <div class="pub-item">
            <div class="pub-title">🔥 <span style="color:#6CBCD0;"><b>Multi-Modal Sarcasm Detection via Knowledge-Aware Focused Graph Convolutional Networks</b></span></div>
            <div class="pub-authors"><strong>Xingjie Zhuang</strong>, Fengling Zhou, Zhixin Li</div>
            <div class="pub-venue"><em>ACM Transactions on Multimedia Computing, Communications, and Applications (TOMM)</em> (<strong>JCR Q1</strong>, <strong>CCF-B</strong>)</div>
            <div class="pub-links"><a href="https://dl.acm.org/doi/10.1145/3722115" class="btn btn--primary btn--small">📄 Paper</a></div>
        </div>
        
        <div class="pub-item">
            <div class="pub-title">🔥 <span style="color:#6CBCD0;"><b>DyCR-Net: A dynamic context-aware routing network for multi-modal sarcasm detection in conversation</b></span></div>
            <div class="pub-authors"><strong>Xingjie Zhuang</strong>, Zhixin Li, Fengling Zhou, Jingliang Gu, Canlong Zhang, Huifang Ma</div>
            <div class="pub-venue"><em>Knowledge-Based Systems (KBS)</em> (<strong>JCR Q1</strong>, <strong>CAS Zone 1, CCF-C</strong>)</div>
            <div class="pub-links"><a href="https://www.sciencedirect.com/science/article/abs/pii/S0950705125000772" class="btn btn--primary btn--small">📄 Paper</a></div>
        </div>
        
        <div class="pub-item">
            <div class="pub-title">🔥 <span style="color:#6CBCD0;"><b>A Cross-modal Collaborative Guiding Network for Sarcasm Explanation in Multi-modal Multi-party Dialogues</b></span></div>
            <div class="pub-authors"><strong>Xingjie Zhuang</strong>, Zhixin Li, Canlong Zhang, Huifang Ma</div>
            <div class="pub-venue"><em>Engineering Applications of Artificial Intelligence (EAAI)</em> (<strong>JCR Q1</strong>, <strong>CAS Zone 1, CCF-C</strong>)</div>
            <div class="pub-links">
                <a href="https://doi.org/10.1016/j.engappai.2024.109884" class="btn btn--primary btn--small">📄 Paper</a>
                <a href="https://github.com/JayDen20010817/CCG-Net" class="btn btn--second btn--small">💻 Code</a>
            </div>
        </div>
        
        <div class="pub-item">
            <div class="pub-title">🔥 <span style="color:#6CBCD0;"><b>MV-BART: Multi-view BART for Multi-modal Sarcasm Detection</b></span></div>
            <div class="pub-authors"><strong>Xingjie Zhuang</strong>, Fengling Zhou, Zhixin Li</div>
            <div class="pub-venue"><em>ACM International Conference on Information and Knowledge Management (CIKM 2024)</em> (<strong>CCF-B</strong>)</div>
            <div class="pub-links"><a href="https://dl.acm.org/doi/10.1145/3627673.3679570" class="btn btn--primary btn--small">📄 Paper</a></div>
        </div>
        
        <!-- ========== 🎓 Educations ========= -->
        <h2>🎓 Educations</h2>
        <div class="edu-item"><span class="edu-left"><strong>Xiamen University</strong></span><span class="edu-date">09/2026 - 07/2030</span> <strong>PhD</strong>, under the supervision of Prof. <a href="https://xmudeeplit.github.io/author/%E8%8B%8F%E5%8A%B2%E6%9D%BE/" target="_blank">Jinsong Su</a></div>
        <div class="edu-item"><span class="edu-left"><strong>Guangxi Normal University</strong></span><span class="edu-date">09/2023 - 07/2026</span> <strong>Master</strong>, under the supervision of Prof. <a href="http://www.cs.gxnu.edu.cn/2019/0302/c4860a143385/page.htm" target="_blank">Zhixin Li</a></div>
        <div class="edu-item"><span class="edu-left"><strong>Fujian Jiangxia University</strong></span><span class="edu-date">09/2019 - 07/2023</span> <strong>Bachelor</strong></div>
        
        <!-- ========== 💼 Industrial & Contest Experience ========= -->
        <h2>💼 Industrial & Contest Experience</h2>
        <div class="exp-item"><span class="exp-title">LLM Algorithm Intern</span>, <strong>Institute of Intelligent Computing Technology, Suzhou, CAS (IICT)</strong> (Mar.2025 – Sep.2025), under supervision of Prof. <a href="https://aoxaustin.github.io/" target="_blank">Xiang Ao</a></div>
        <div class="exp-item"><span class="exp-title">System Development & Data Analysis Intern</span>, <strong>Akuvox/STAR-NET</strong> (Apr.2023 – Jul.2023)</div>
        
        <!-- ========== 🏆 Honors and Awards ========= -->
        <h2>🏆 Honors and Awards</h2>
        <ul class="honor-list">
            <li>Outstanding Graduate in GXNU</li>
            <li>National Scholarship, 2025</li>
            <li>Outstanding Graduate Student Scholarship, 2025</li>
            <li>The First Prize Scholarship, 2025</li>
            <li><strong>1st Prize</strong> China Undergraduate Mathematical Contest in Modelling (CUMCM, Fujian Division), 2021</li>
        </ul>
        
        <!-- ========== ⚡ Academic Services/Reviewer ========= -->
        <h2>⚡ Academic Services/Reviewer</h2>
        <div style="margin-left: 0px;">
            <ul class="reviewer-list">
                <li>ACM International Conference on Information and Knowledge Management (CIKM)</li>
                <li>IEEE International Conference on Multimedia & Expo (ICME)</li>
                <li>IEEE International Conference on Acoustics, Speech, and Signal Processing (ICASSP)</li>
                <li>Knowledge-based Systems</li>
                <li>Knowledge and Information Systems</li>
                <li>Neurocomputing</li>
                <li>International Journal of Machine Learning and Cybernetics</li>
                <li>Multimedia Systems</li>
                <li>Journal of Intelligent Information Systems</li>
            </ul>
        </div>
        
        <!-- 访问计数器 (保留原始 flagcounter) -->
        <div style="margin-top: 2rem; text-align: center;">
            <a href="https://info.flagcounter.com/KHH5" target="_blank" rel="noopener">
                <img src="https://s01.flagcounter.com/count2/KHH5/bg_FFFFFF/txt_000000/border_CCCCCC/columns_2/maxflags_10/viewers_0/labels_0/pageviews_0/flags_0/percent_0/" alt="Free counters!" border="0">
            </a>
        </div>
        
        <div class="small-footer">
            ✦ Last update: 2026 · Multilingual & Omni LLMs ✦ 
            <span style="margin-left: 1rem;">Rome typeface for all content (Times New Roman)</span>
        </div>
    </div>
</body>
</html>
