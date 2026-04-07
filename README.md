<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chanidu Madalagama - Interactive Resume</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- Chosen Palette: Warm Neutrals & Crisp Accents (Slate-50 bg, White panels, Blue-600 accents for a clean, professional, light aesthetic) -->
    <!-- Application Structure Plan: Interactive Career Dashboard. The structure departs from a linear resume by using a dashboard layout. It features a hero profile, a visual skill matrix (Radar Chart) for quick competency assessment, an interactive experience panel that reveals details on click to reduce cognitive load, and a grid-based project portfolio for easy scannability. This prioritizes user engagement and interactive exploration of the candidate's value. -->
    <!-- Visualization & Content Choices: 1. Skills -> Goal: Compare/Inform -> Viz: Chart.js Radar Chart -> Interaction: Hover tooltips -> Justification: Instantly communicates the balance of technical skills without reading lists. NO SVG used. 2. Experience -> Goal: Organize/Inform -> Viz: Interactive side-by-side layout -> Interaction: Click company to view details -> Justification: Prevents text-walling, allows focused reading. NO SVG used. 3. Projects -> Goal: Organize -> Viz: CSS Grid of cards -> Justification: Standard, scannable pattern for portfolios. NO SVG used. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #f8fafc; color: #1e293b; }
        .chart-container { position: relative; width: 100%; max-width: 500px; margin-left: auto; margin-right: auto; height: 350px; max-height: 400px; }
        @media (min-width: 768px) { .chart-container { height: 400px; } }
        .interactive-item { transition: all 0.2s ease-in-out; cursor: pointer; }
        .interactive-item:hover { transform: translateX(5px); border-color: #2563eb; background-color: #eff6ff; }
        .interactive-item.active { border-left-width: 4px; border-color: #2563eb; background-color: #eff6ff; font-weight: 600; }
        .project-card { transition: box-shadow 0.3s ease, transform 0.3s ease; }
        .project-card:hover { box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1); transform: translateY(-3px); }
    </style>
</head>
<body class="antialiased">

    <div class="max-w-6xl mx-auto px-4 py-8 sm:px-6 lg:px-8 space-y-12">

        <header class="bg-white rounded-2xl shadow-sm border border-slate-200 p-8 flex flex-col md:flex-row justify-between items-start md:items-center gap-6">
            <div class="space-y-2">
                <h1 class="text-4xl font-extrabold text-slate-900 tracking-tight">Chanidu Madalagama</h1>
                <h2 class="text-xl font-medium text-blue-600">Software Engineer - Flutter Specialist</h2>
                <div class="flex flex-wrap gap-4 text-sm text-slate-500 mt-2">
                    <span class="flex items-center gap-1">📍 Padukka, Colombo</span>
                    <span class="flex items-center gap-1">📧 chanidumadalagama@gmail.com</span>
                    <span class="flex items-center gap-1">📱 0770459266</span>
                </div>
            </div>
            <div class="bg-slate-50 p-4 rounded-xl border border-slate-100 max-w-sm">
                <p class="text-sm leading-relaxed text-slate-700">
                    Expert in optimizing cross-platform applications for performance, while leading code reviews and unit testing. Proven ability to translate complex designs into user-friendly interfaces.
                </p>
            </div>
        </header>

        <section class="space-y-4">
            <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-8">
                <h3 class="text-2xl font-bold text-slate-800 mb-4 border-b pb-2">Dashboard Overview</h3>
                <p class="text-slate-600 leading-relaxed max-w-4xl">
                    Welcome to the interactive professional portfolio of Chanidu Madalagama. This application synthesizes comprehensive career history, technical proficiencies, and project deliveries into an explorable format. Interact with the panels below to understand Chanidu's impact in Flutter mobile development, software architecture, and team leadership.
                </p>
            </div>
        </section>

        <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
            
            <section class="lg:col-span-1 bg-white rounded-2xl shadow-sm border border-slate-200 p-8">
                <h3 class="text-xl font-bold text-slate-800 mb-2 border-b pb-2">Technical Competency</h3>
                <p class="text-sm text-slate-500 mb-6">
                    This radar chart visualizes core technical strengths extracted from professional experience. It highlights a focus on architecture, performance, and UI execution. Hover over the points for detailed metrics.
                </p>
                <div class="chart-container">
                    <canvas id="skillsChart"></canvas>
                </div>
                <div class="mt-6 flex flex-wrap gap-2">
                    <span class="px-3 py-1 bg-blue-50 text-blue-700 text-xs font-semibold rounded-full border border-blue-100">Flutter & Dart</span>
                    <span class="px-3 py-1 bg-blue-50 text-blue-700 text-xs font-semibold rounded-full border border-blue-100">Firebase</span>
                    <span class="px-3 py-1 bg-blue-50 text-blue-700 text-xs font-semibold rounded-full border border-blue-100">RESTful APIs</span>
                    <span class="px-3 py-1 bg-blue-50 text-blue-700 text-xs font-semibold rounded-full border border-blue-100">Git/GitHub</span>
                    <span class="px-3 py-1 bg-slate-100 text-slate-700 text-xs font-semibold rounded-full border border-slate-200">Agile</span>
                </div>
            </section>

            <section class="lg:col-span-2 bg-white rounded-2xl shadow-sm border border-slate-200 p-8 flex flex-col h-full">
                <h3 class="text-xl font-bold text-slate-800 mb-2 border-b pb-2">Professional Journey</h3>
                <p class="text-sm text-slate-500 mb-6">
                    Explore Chanidu's career progression. Select a role from the timeline list on the left to reveal specific responsibilities, technical achievements, and organizational impact in the detail panel on the right.
                </p>
                
                <div class="flex flex-col md:flex-row gap-6 flex-grow">
                    <div class="w-full md:w-1/3 space-y-2 border-r border-slate-100 pr-4">
                        <div class="interactive-item active p-3 rounded-lg border border-transparent" data-target="elegant">
                            <div class="font-bold text-slate-800 text-sm">Elegant Media</div>
                            <div class="text-xs text-slate-500">2024 - Present</div>
                        </div>
                        <div class="interactive-item p-3 rounded-lg border border-transparent" data-target="archmage">
                            <div class="font-bold text-slate-800 text-sm">Archmage Solutions</div>
                            <div class="text-xs text-slate-500">2022 - 2023</div>
                        </div>
                    </div>
                    
                    <div class="w-full md:w-2/3 pl-2" id="experience-details">
                        
                    </div>
                </div>
            </section>
        </div>

        <section class="bg-white rounded-2xl shadow-sm border border-slate-200 p-8">
            <h3 class="text-xl font-bold text-slate-800 mb-2 border-b pb-2">Project Portfolio</h3>
            <p class="text-sm text-slate-500 mb-6">
                A comprehensive portfolio of development initiatives. These cards highlight expertise across various domains including mobile architecture, e-commerce, real-time communication, and enterprise POS systems.
            </p>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6" id="projects-container">
               
            </div>
        </section>

        <section class="bg-white rounded-2xl shadow-sm border border-slate-200 p-8">
            <h3 class="text-xl font-bold text-slate-800 mb-2 border-b pb-2">Academic Background</h3>
            <p class="text-sm text-slate-500 mb-6">
                Continuous learning and formal education supporting software engineering expertise.
            </p>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div class="flex items-start gap-3 p-4 bg-slate-50 rounded-xl border border-slate-100">
                    <div class="text-2xl">🎓</div>
                    <div>
                        <h4 class="font-bold text-slate-800 text-sm">Executive MSc in Digital Marketing</h4>
                        <p class="text-xs text-slate-600">Cambridge College</p>
                        <p class="text-xs text-blue-600 font-medium mt-1">Graduating October 2025</p>
                    </div>
                </div>
                <div class="flex items-start gap-3 p-4 bg-slate-50 rounded-xl border border-slate-100">
                    <div class="text-2xl">🎓</div>
                    <div>
                        <h4 class="font-bold text-slate-800 text-sm">BEng (Hons) in Software Engineering</h4>
                        <p class="text-xs text-slate-600">London Metropolitan University (UK)</p>
                        <p class="text-xs text-blue-600 font-medium mt-1">Currently Enrolled</p>
                    </div>
                </div>
                <div class="flex items-start gap-3 p-4 bg-slate-50 rounded-xl border border-slate-100">
                    <div class="text-2xl">🎓</div>
                    <div>
                        <h4 class="font-bold text-slate-800 text-sm">Bachelor of Software Engineering Honours</h4>
                        <p class="text-xs text-slate-600">Open University of Sri Lanka</p>
                        <p class="text-xs text-blue-600 font-medium mt-1">Currently Enrolled</p>
                    </div>
                </div>
                <div class="flex items-start gap-3 p-4 bg-slate-50 rounded-xl border border-slate-100">
                    <div class="text-2xl">🎓</div>
                    <div>
                        <h4 class="font-bold text-slate-800 text-sm">HND, Electrical and Electronics Engineering</h4>
                        <p class="text-xs text-slate-600">Technical College Ratmalana</p>
                        <p class="text-xs text-blue-600 font-medium mt-1">Graduated 2019</p>
                    </div>
                </div>
            </div>
        </section>

    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {

            const expData = {
                elegant: {
                    title: "Associate Software Engineer - Flutter",
                    company: "Elegant Media Sri Lanka",
                    period: "01/2024 - Present",
                    summary: "Responsible for the full development lifecycle of high-volume, cross-platform iOS and Android applications, ensuring exceptional speed and responsiveness.",
                    points: [
                        "Develop new user-facing features and integrate complex RESTful APIs/third-party libraries using Flutter and Dart.",
                        "Lead technical quality by conducting code reviews and writing unit/widget tests.",
                        "Optimize applications for performance and troubleshoot/debug issues.",
                        "Successfully implemented performance optimizations, resulting in measurable improvements.",
                        "Consistently translated complex designs into pixel-perfect, user-friendly interfaces."
                    ]
                },
                archmage: {
                    title: "Flutter Developer",
                    company: "Archmage Solutions (Pvt) Ltd",
                    period: "01/2022 - 12/2023",
                    summary: "Developed defined mobile app features and user stories, converting detailed UI/UX designs into functional Flutter widgets under guidance.",
                    points: [
                        "Translated detailed UI/UX design specifications into functional, visually accurate Flutter widgets.",
                        "Wrote clean, readable, and maintainable code, contributing to unit and widget tests.",
                        "Utilized Git/GitHub for version control and actively participated in Agile ceremonies.",
                        "Assisted in consuming and integrating basic RESTful APIs.",
                        "Identified, reproduced, and fixed minor bugs reported during the QA phase."
                    ]
                }
            };

            const detailsContainer = document.getElementById('experience-details');
            const expItems = document.querySelectorAll('.interactive-item');

            function renderExperience(key) {
                const data = expData[key];
                let html = `
                    <h4 class="text-lg font-bold text-blue-700">${data.title}</h4>
                    <p class="text-sm font-semibold text-slate-800">${data.company}</p>
                    <p class="text-xs text-slate-500 mb-4 border-b pb-2">${data.period}</p>
                    <p class="text-sm text-slate-700 mb-4 bg-slate-50 p-3 rounded-lg border border-slate-100">${data.summary}</p>
                    <ul class="space-y-2">
                `;
                data.points.forEach(pt => {
                    html += `<li class="text-sm text-slate-600 flex items-start"><span class="mr-2 text-blue-500">▪</span><span>${pt}</span></li>`;
                });
                html += `</ul>`;
                detailsContainer.innerHTML = html;
            }

            renderExperience('elegant');

            expItems.forEach(item => {
                item.addEventListener('click', (e) => {
                    expItems.forEach(i => i.classList.remove('active'));
                    e.currentTarget.classList.add('active');
                    const target = e.currentTarget.getAttribute('data-target');
                    renderExperience(target);
                });
            });

            const ctx = document.getElementById('skillsChart').getContext('2d');
            new Chart(ctx, {
                type: 'radar',
                data: {
                    labels: [
                        'Flutter & Dart Core',
                        'UI/UX Translation',
                        'API Integration',
                        'Performance Tuning',
                        'Unit & Widget Testing',
                        'Architecture & State'
                    ],
                    datasets: [{
                        label: 'Competency Level',
                        data: [95, 90, 85, 85, 80, 85],
                        backgroundColor: 'rgba(37, 99, 235, 0.2)',
                        borderColor: 'rgba(37, 99, 235, 1)',
                        pointBackgroundColor: 'rgba(37, 99, 235, 1)',
                        pointBorderColor: '#fff',
                        pointHoverBackgroundColor: '#fff',
                        pointHoverBorderColor: 'rgba(37, 99, 235, 1)'
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        r: {
                            angleLines: { color: 'rgba(0,0,0,0.05)' },
                            grid: { color: 'rgba(0,0,0,0.05)' },
                            pointLabels: {
                                font: { size: 11, family: "'Segoe UI', sans-serif" },
                                color: '#475569'
                            },
                            ticks: { display: false, min: 0, max: 100 }
                        }
                    },
                    plugins: {
                        legend: { display: false },
                        tooltip: {
                            backgroundColor: 'rgba(15, 23, 42, 0.9)',
                            padding: 10,
                            callbacks: {
                                label: function(context) {
                                    return ' Proficiency: ' + context.raw + '/100';
                                }
                            }
                        }
                    }
                }
            });

            const projectsData = [
                { name: "Danal Mathus", domain: "Handyman App", desc: "Multi-role job management platform with real-time job posting, secure Firebase Chat, and push notifications." },
                { name: "Agape Social", domain: "Social Platform", desc: "Full-stack social platform featuring scalable content feeds, private group chat, and Stripe/IAP donation integration." },
                { name: "We EV", domain: "Electric Vehicle", desc: "EV owner app with dynamic map integration for charging locations, custom e-commerce, and subscription management." },
                { name: "Savoy Cinema POS", domain: "Enterprise Software", desc: "NFC-based POS application for ticket scanning utilizing hybrid Cloud and Embedded SQL for real-time processing." },
                { name: "Taktik Book", domain: "Booking Platform", desc: "High-volume movie ticket booking platform integrating real-time seat availability and intuitive APIs." },
                { name: "LinkSafe", domain: "Mission-Critical App", desc: "Enhanced runtime form validation logic based on backend configuration and optimized data persistence with MySQL." },
                { name: "OBUDDY App", domain: "Campus Network", desc: "Secure, community-driven campus platform focusing on scalable architecture for peer-to-peer communication." },
                { name: "MoterSurte", domain: "Social Commerce", desc: "Platform for car enthusiasts to showcase projects, merging social networking with a vehicle marketplace." },
                { name: "National Film Corp", domain: "Companion App", desc: "High-performance app featuring effortless API calls, QR code scanning, and integrated web-backend booking." }
            ];

            const projectsContainer = document.getElementById('projects-container');
            let projHTML = '';
            projectsData.forEach(proj => {
                projHTML += `
                    <div class="project-card bg-white p-5 rounded-xl border border-slate-200 flex flex-col h-full">
                        <div class="text-xs font-bold text-blue-600 mb-1 uppercase tracking-wider">${proj.domain}</div>
                        <h4 class="text-lg font-extrabold text-slate-800 mb-2">${proj.name}</h4>
                        <p class="text-sm text-slate-600 flex-grow">${proj.desc}</p>
                    </div>
                `;
            });
            projectsContainer.innerHTML = projHTML;

        });
    </script>
</body>
</html>
