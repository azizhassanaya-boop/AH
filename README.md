<!DOCTYPE html>
<html lang="ar" dir="rtl" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- يمكنك تغيير اسم الموقع من هنا مباشرة -->
    <title>اسم موقعك الجديد - 3D Pro Studio</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;800;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <style>
        body {
            font-family: 'Cairo', sans-serif;
            background: radial-gradient(circle at top center, #0f172a 0%, #020617 100%);
            color: #f8fafc;
            overflow-x: hidden;
        }
        /* 3D Glassmorphism & Depth Effects */
        .glass-3d {
            background: linear-gradient(135deg, rgba(30, 41, 59, 0.75) 0%, rgba(15, 23, 42, 0.85) 100%);
            backdrop-filter: blur(16px);
            border: 1px solid rgba(245, 158, 11, 0.2);
            box-shadow: 0 20px 40px -15px rgba(0, 0, 0, 0.7), 0 0 25px rgba(245, 158, 11, 0.08), inset 0 1px 1px rgba(255, 255, 255, 0.1);
            transform: perspective(1000px) translateZ(0);
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .glass-3d:hover {
            border-color: rgba(245, 158, 11, 0.4);
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.8), 0 0 35px rgba(245, 158, 11, 0.15), inset 0 1px 2px rgba(255, 255, 255, 0.2);
            transform: perspective(1000px) translateY(-2px) translateZ(4px);
        }
        .btn-3d {
            background: linear-gradient(135deg, #f59e0b 0%, #d97706 50%, #b45309 100%);
            box-shadow: 0 10px 20px -5px rgba(245, 158, 11, 0.4), inset 0 2px 3px rgba(255, 255, 255, 0.3), inset 0 -2px 3px rgba(0, 0, 0, 0.4);
            transition: all 0.2s ease;
        }
        .btn-3d:hover {
            transform: translateY(-2px);
            box-shadow: 0 15px 25px -5px rgba(245, 158, 11, 0.6), inset 0 2px 3px rgba(255, 255, 255, 0.4), inset 0 -2px 3px rgba(0, 0, 0, 0.4);
        }
        .btn-3d:active {
            transform: translateY(1px);
            box-shadow: 0 5px 10px -2px rgba(245, 158, 11, 0.3), inset 0 1px 2px rgba(0, 0, 0, 0.5);
        }
        ::-webkit-scrollbar { width: 8px; height: 8px; }
        ::-webkit-scrollbar-track { background: #020617; }
        ::-webkit-scrollbar-thumb { background: #1e293b; border-radius: 4px; border: 2px solid #020617; }
        ::-webkit-scrollbar-thumb:hover { background: #f59e0b; }
    </style>
</head>
<body class="min-h-screen selection:bg-amber-500 selection:text-slate-950">

    <!-- TOP NAVIGATION BAR (3D GLASS) -->
    <header class="glass-3d sticky top-0 z-40 px-4 sm:px-6 py-3.5 border-b border-amber-500/20">
        <div class="max-w-7xl mx-auto flex items-center justify-between gap-3 flex-wrap">
            <!-- Studio Logo & Brand 3D -->
            <div class="flex items-center gap-3.5">
                <div class="w-12 h-12 rounded-2xl bg-gradient-to-br from-amber-300 via-yellow-500 to-amber-700 p-0.5 shadow-2xl shadow-amber-500/30 flex items-center justify-center transform hover:rotate-6 transition-transform">
                    <div class="w-full h-full bg-slate-950 rounded-[14px] flex items-center justify-center">
                        <svg viewBox="0 0 100 100" class="w-8 h-8 filter drop-shadow-[0_2px_4px_rgba(245,158,11,0.5)]">
                            <defs>
                                <linearGradient id="goldGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                                    <stop offset="0%" stop-color="#fde68a" />
                                    <stop offset="50%" stop-color="#f59e0b" />
                                    <stop offset="100%" stop-color="#b45309" />
                                </linearGradient>
                            </defs>
                            <path d="M10 15 L90 15 L80 40 L76 40 L83 20 L17 20 L24 40 L20 40 Z" fill="url(#goldGrad)"/>
                            <path d="M25 25 L48 25 L48 92 L40 82 L40 55 L33 55 L33 72 L25 62 Z M33 33 L33 46 L40 46 L40 33 Z" fill="url(#goldGrad)"/>
                            <path d="M52 25 L60 25 L60 46 L67 46 L67 25 L75 25 L75 62 L67 72 L67 55 L60 55 L60 82 L52 92 Z" fill="url(#goldGrad)"/>
                        </svg>
                    </div>
                </div>
                <div>
                    <h1 class="text-base sm:text-lg font-black text-white tracking-wide flex items-center gap-2 drop-shadow-md">
                        Studio Aziz hasan
                    </h1>
                    <p class="text-[10px] font-black text-amber-400 tracking-widest uppercase">SOUND ENGINEER</p>
                </div>
            </div>

            <!-- Admin Dual-View Switcher -->
            <div id="adminDualViewBar" class="hidden items-center gap-1.5 bg-slate-950/80 p-1 rounded-2xl border border-amber-500/30 shadow-inner">
                <button onclick="switchAdminViewMode('engineer-view')" id="btnAdminViewEng" class="px-3.5 py-2 rounded-xl text-xs font-black transition-all bg-amber-500 text-slate-950 shadow-md">
                    <i class="fa-solid fa-sliders ml-1.5"></i> لوحة المهندس
                </button>
                <button onclick="switchAdminViewMode('client-view')" id="btnAdminViewClient" class="px-3.5 py-2 rounded-xl text-xs font-bold transition-all text-slate-400 hover:text-white">
                    <i class="fa-solid fa-user-shield ml-1.5"></i> معاينة العميل
                </button>
                <select id="adminClientPreviewSelect" onchange="changeActiveClient(this.value)" class="bg-slate-900 text-amber-400 text-xs font-bold px-2.5 py-1.5 rounded-xl border border-slate-700 focus:outline-none">
                </select>
            </div>

            <!-- Header Actions & Notifications -->
            <div class="flex items-center gap-3">
                <span id="currentUserBadge" class="hidden sm:inline-flex items-center gap-1.5 px-3.5 py-1.5 rounded-xl bg-amber-500/10 border border-amber-500/30 text-amber-400 text-xs font-black shadow-md"></span>

                <button onclick="toggleNotificationsModal()" class="relative p-2.5 rounded-xl glass-3d text-slate-300 hover:text-white transition-all">
                    <i class="fa-solid fa-bell text-sm text-amber-400"></i>
                    <span id="notifUnreadBadge" class="absolute -top-1 -right-1 w-4 h-4 rounded-full bg-rose-500 text-white text-[9px] font-black flex items-center justify-center hidden shadow-lg">0</span>
                </button>

                <button onclick="forceCloudSyncNow()" title="مزامنة سحابية فورية" class="hidden md:flex items-center gap-2 px-3.5 py-2 rounded-xl glass-3d text-[11px] text-slate-300 hover:border-amber-500/40 transition-all">
                    <span class="w-2.5 h-2.5 rounded-full bg-emerald-500 animate-ping"></span>
                    <span id="cloudStatusText">سحابة حية 3D</span>
                </button>

                <button onclick="openChangePasswordModal()" title="تغيير كلمة السر" class="px-3.5 py-2 rounded-xl glass-3d text-amber-400 text-xs font-black transition-all flex items-center gap-1.5 hover:scale-105">
                    <i class="fa-solid fa-key"></i>
                    <span class="hidden sm:inline">كلمة السر</span>
                </button>

                <button onclick="logoutToLoginScreen()" class="px-3.5 py-2 rounded-xl bg-rose-500/15 text-rose-400 hover:bg-rose-500 hover:text-slate-950 border border-rose-500/30 text-xs font-black transition-all flex items-center gap-1.5 shadow-md">
                    <i class="fa-solid fa-right-from-bracket"></i>
                    <span>خروج</span>
                </button>
            </div>
        </div>
    </header>

    <!-- LOGIN SCREEN MODAL (3D PRO GLASS) -->
    <div id="loginScreenModal" class="fixed inset-0 z-50 bg-slate-950/95 backdrop-blur-2xl flex items-center justify-center p-4">
        <div class="max-w-md w-full glass-3d rounded-3xl p-6 sm:p-8 relative overflow-hidden shadow-2xl">
            <div class="absolute -top-24 -left-24 w-52 h-52 bg-amber-500/15 rounded-full blur-3xl pointer-events-none"></div>
            
            <div class="text-center space-y-3 mb-6">
                <div class="w-20 h-20 mx-auto rounded-2xl bg-gradient-to-br from-amber-300 via-yellow-500 to-amber-700 p-0.5 shadow-2xl shadow-amber-500/30 flex items-center justify-center transform hover:rotate-12 transition-transform">
                    <div class="w-full h-full bg-slate-950 rounded-[14px] flex flex-col items-center justify-center">
                        <svg viewBox="0 0 100 100" class="w-12 h-12">
                            <path d="M10 15 L90 15 L80 40 L76 40 L83 20 L17 20 L24 40 L20 40 Z" fill="#f59e0b"/>
                            <path d="M25 25 L48 25 L48 92 L40 82 L40 55 L33 55 L33 72 L25 62 Z M33 33 L33 46 L40 46 L40 33 Z" fill="#f59e0b"/>
                            <path d="M52 25 L60 25 L60 46 L67 46 L67 25 L75 25 L75 62 L67 72 L67 55 L60 55 L60 82 L52 92 Z" fill="#f59e0b"/>
                        </svg>
                    </div>
                </div>
                <h2 class="text-2xl font-black text-white tracking-wide">Studio Aziz hasan</h2>
                <p class="text-[11px] font-black text-amber-400 tracking-widest uppercase">SOUND ENGINEERING</p>
                <p class="text-xs text-slate-400 pt-1">أدخل بيانات اعتماد الحساب الآمنة للدخول</p>
            </div>

            <form onsubmit="handleUserLoginSubmit(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1.5">الحساب / كود الدخول</label>
                    <input type="text" id="loginUsernameInput" required placeholder="أدخل اسم الحساب أو الكود" class="w-full px-4 py-3.5 rounded-2xl bg-slate-950/80 border border-slate-800 text-white text-sm focus:outline-none focus:border-amber-500 font-mono shadow-inner">
                </div>

                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1.5">كلمة السر المؤكدة</label>
                    <input type="password" id="loginPasswordInput" required placeholder="أدخل كلمة المرور" class="w-full px-4 py-3.5 rounded-2xl bg-slate-950/80 border border-slate-800 text-white text-sm focus:outline-none focus:border-amber-500 font-mono shadow-inner">
                </div>

                <div id="loginErrorMsg" class="hidden p-3 rounded-xl bg-rose-500/10 border border-rose-500/30 text-rose-400 text-xs text-center font-bold"></div>

                <button type="submit" class="w-full py-4 rounded-2xl btn-3d text-slate-950 font-black text-sm shadow-xl transition-all flex items-center justify-center gap-2">
                    <i class="fa-solid fa-arrow-right-to-bracket text-base"></i>
                    <span>تسجيل الدخول الآمن</span>
                </button>
            </form>
        </div>
    </div>

    <!-- MAIN APP CONTAINER -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 py-6">

        <!-- ================================================================= -->
        <!-- 1. ENGINEER / ADMIN WORKSPACE (3D PRO)                            -->
        <!-- ================================================================= -->
        <section id="adminWorkspace" class="hidden space-y-6">
            <div class="glass-3d p-3 rounded-2xl flex flex-wrap items-center justify-between gap-3">
                <div class="flex flex-wrap items-center gap-2">
                    <button onclick="switchAdminTab('dashboard')" id="adminTabBtn-dashboard" class="px-4 py-2.5 rounded-xl text-xs font-black transition-all bg-amber-500 text-slate-950 shadow-md">
                        <i class="fa-solid fa-compact-disc ml-1.5"></i> المشاريع والحلقات
                    </button>
                    <button onclick="switchAdminTab('clients')" id="adminTabBtn-clients" class="px-4 py-2.5 rounded-xl text-xs font-bold transition-all bg-slate-900/80 text-slate-300 hover:text-white border border-slate-800">
                        <i class="fa-solid fa-user-lock ml-1.5"></i> الحسابات والأمان
                    </button>
                    <button onclick="switchAdminTab('ai')" id="adminTabBtn-ai" class="px-4 py-2.5 rounded-xl text-xs font-bold transition-all bg-slate-900/80 text-slate-300 hover:text-white border border-slate-800">
                        <i class="fa-solid fa-brain ml-1.5 text-purple-400"></i> المحلل الذكي (AI)
                    </button>
                </div>

                <button id="btnCreateNewAccount" onclick="openNewClientModal()" class="px-4 py-2.5 rounded-xl bg-emerald-500/15 hover:bg-emerald-500 text-emerald-400 hover:text-slate-950 border border-emerald-500/30 text-xs font-black transition-all flex items-center gap-1.5 shadow-md">
                    <i class="fa-solid fa-user-plus"></i>
                    <span>إنشاء حساب جديد</span>
                </button>
            </div>

            <!-- Admin Summary KPI Cards (3D) -->
            <div id="adminSummaryCards" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4"></div>

            <!-- Admin Tab 1: Projects -->
            <div id="adminSubView-dashboard" class="space-y-4">
                <div id="adminProjectsList" class="space-y-5"></div>
            </div>

            <!-- Admin Tab 2: Accounts -->
            <div id="adminSubView-clients" class="hidden space-y-6">
                <div id="adminSystemAccountsSection" class="glass-3d rounded-3xl p-6 space-y-4">
                    <div class="border-b border-slate-800 pb-3">
                        <h3 class="text-sm font-black text-white flex items-center gap-2">
                            <i class="fa-solid fa-shield-halved text-amber-400"></i>
                            <span>حسابات الإدارة والمهندسين (صلاحيات الأدمن فقط)</span>
                        </h3>
                    </div>
                    <div id="adminSystemAccountsGrid" class="grid grid-cols-1 md:grid-cols-2 gap-4"></div>
                </div>

                <div class="space-y-3">
                    <h3 class="text-sm font-black text-white flex items-center gap-2">
                        <i class="fa-solid fa-users-viewfinder text-emerald-400"></i>
                        <span>حسابات العملاء المعزولة والسرية</span>
                    </h3>
                    <div id="adminClientsGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4"></div>
                </div>
            </div>

            <!-- Admin Tab 3: AI -->
            <div id="adminSubView-ai" class="hidden space-y-4">
                <div class="glass-3d rounded-3xl p-6 space-y-4 border border-purple-500/30">
                    <div class="flex items-center justify-between flex-wrap gap-3">
                        <div class="flex items-center gap-3">
                            <div class="w-12 h-12 rounded-2xl bg-purple-500/15 border border-purple-500/30 flex items-center justify-center text-purple-400 text-xl shadow-md">
                                <i class="fa-solid fa-wand-magic-sparkles"></i>
                            </div>
                            <div>
                                <h3 class="text-base font-black text-white">المحلل الذكي لسلوك العملاء والجدولة (AI Analyzer)</h3>
                                <p class="text-xs text-slate-400">متابعة الأداء الحي لتنفيذ العمليات الصوتية بدقة متناهية</p>
                            </div>
                        </div>
                        <button onclick="generateNewAISuggestion()" class="px-4 py-2.5 rounded-xl bg-purple-500 hover:bg-purple-400 text-slate-950 text-xs font-black transition-all shadow-md">
                            <i class="fa-solid fa-rotate ml-1"></i> تحليل جديد
                        </button>
                    </div>
                    <div id="aiSuggestionsContainer" class="grid grid-cols-1 md:grid-cols-2 gap-4"></div>
                </div>
            </div>
        </section>

        <!-- ================================================================= -->
        <!-- 2. ISOLATED CLIENT WORKSPACE (3D PRO)                             -->
        <!-- ================================================================= -->
        <section id="clientWorkspace" class="hidden space-y-6">
            <div id="clientFinancialHeader" class="glass-3d rounded-3xl p-6 space-y-4"></div>

            <div class="glass-3d p-2 rounded-2xl flex items-center gap-2">
                <button onclick="switchClientTab('projects-room')" id="clientTabBtn-projects-room" class="flex-1 py-3 px-4 rounded-xl text-xs sm:text-sm font-black transition-all bg-amber-500 text-slate-950 shadow-md">
                    <i class="fa-solid fa-layer-group ml-1.5"></i> مشاريعي وغرفة المراجعة
                </button>
                <button onclick="switchClientTab('new-project')" id="clientTabBtn-new-project" class="flex-1 py-3 px-4 rounded-xl text-xs sm:text-sm font-bold transition-all bg-slate-900/80 text-slate-300 hover:text-white border border-slate-800">
                    <i class="fa-solid fa-circle-plus ml-1.5"></i> طلب مشروع صوتي جديد
                </button>
            </div>

            <!-- Client Tab 1: Projects Room -->
            <div id="clientSubView-projects-room" class="space-y-4">
                <div id="clientProjectsButtonsContainer" class="space-y-4"></div>
            </div>

            <!-- Client Tab 2: New Project Form -->
            <div id="clientSubView-new-project" class="hidden">
                <form onsubmit="submitClientNewProject(event)" class="glass-3d rounded-3xl p-6 sm:p-8 space-y-6">
                    <div class="border-b border-slate-800 pb-4">
                        <h3 class="text-lg font-black text-white flex items-center gap-2">
                            <i class="fa-solid fa-sliders text-amber-400"></i>
                            <span>استمارة طلب مشروع صوتي جديد (3D Pro)</span>
                        </h3>
                        <p class="text-xs text-slate-400 mt-1">حدد مواصفات المشروع والمعايير التقنية بدقة تامة</p>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-xs font-bold text-slate-300 mb-1.5">اسم المشروع</label>
                            <input type="text" id="newProjName" required placeholder="مثال: مسلسل ما وراء الطبيعة" class="w-full px-4 py-3.5 rounded-2xl bg-slate-950/80 border border-slate-800 text-white text-sm focus:outline-none focus:border-amber-500 shadow-inner">
                        </div>
                        <div>
                            <label class="block text-xs font-bold text-slate-300 mb-1.5">حجم المشروع</label>
                            <select id="newProjSize" class="w-full px-4 py-3.5 rounded-2xl bg-slate-950/80 border border-slate-800 text-white text-sm focus:outline-none focus:border-amber-500 shadow-inner">
                                <option value="مسلسل">مسلسل (حلقات متعددة)</option>
                                <option value="فلم">فلم</option>
                                <option value="ريل">ريل (Reel)</option>
                                <option value="إعلان">إعلان</option>
                            </select>
                        </div>
                    </div>

                    <!-- Tasks -->
                    <div class="space-y-2.5">
                        <div class="flex items-center justify-between">
                            <label class="text-xs font-bold text-slate-300">المهام الصوتية المطلوبة</label>
                            <button type="button" onclick="toggleAllTasks()" class="px-3 py-1 rounded-xl bg-amber-500/15 text-amber-400 border border-amber-500/30 text-xs font-bold hover:bg-amber-500 hover:text-slate-950 transition-all">جميعها</button>
                        </div>
                        <div id="newProjTasksGrid" class="grid grid-cols-2 sm:grid-cols-5 gap-2.5">
                            <button type="button" onclick="toggleTaskItem('edit')" id="taskBtn-edit" class="p-3.5 rounded-2xl border text-xs font-black transition-all bg-amber-500/20 border-amber-500 text-amber-300 shadow-md">إيديت (Edit)</button>
                            <button type="button" onclick="toggleTaskItem('mix')" id="taskBtn-mix" class="p-3.5 rounded-2xl border text-xs font-black transition-all bg-amber-500/20 border-amber-500 text-amber-300 shadow-md">ميكس (Mix)</button>
                            <button type="button" onclick="toggleTaskItem('soundFx')" id="taskBtn-soundFx" class="p-3.5 rounded-2xl border text-xs font-bold transition-all bg-slate-950 border-slate-800 text-slate-400">ساوند إفيكت</button>
                            <button type="button" onclick="toggleTaskItem('soundDesign')" id="taskBtn-soundDesign" class="p-3.5 rounded-2xl border text-xs font-bold transition-all bg-slate-950 border-slate-800 text-slate-400">ساوند ديزاين</button>
                            <button type="button" onclick="toggleTaskItem('music')" id="taskBtn-music" class="p-3.5 rounded-2xl border text-xs font-bold transition-all bg-slate-950 border-slate-800 text-slate-400">إعداد موسيقي</button>
                        </div>
                    </div>

                    <!-- Output Format -->
                    <div class="space-y-2.5">
                        <label class="block text-xs font-bold text-slate-300">نظام الإخراج الصوتي (ستيريو أو سيراوند أو كليْهما)</label>
                        <div class="grid grid-cols-2 gap-3">
                            <button type="button" onclick="toggleOutputMode('stereo')" id="outBtn-stereo" class="p-3.5 rounded-2xl border text-xs font-black transition-all bg-amber-500/20 border-amber-500 text-amber-300 flex items-center justify-center gap-2 shadow-md">
                                <i class="fa-solid fa-headphones"></i>
                                <span>ستيريو (Stereo)</span>
                            </button>
                            <button type="button" onclick="toggleOutputMode('surround')" id="outBtn-surround" class="p-3.5 rounded-2xl border text-xs font-bold transition-all bg-slate-950 border-slate-800 text-slate-400 flex items-center justify-center gap-2">
                                <i class="fa-solid fa-cubes"></i>
                                <span>سيراوند (Surround)</span>
                            </button>
                        </div>
                    </div>

                    <!-- Technical Standards -->
                    <div class="space-y-3 bg-slate-950/80 p-5 rounded-3xl border border-slate-800 shadow-inner">
                        <label class="block text-xs font-bold text-slate-300">المعايير التقنية (اختر DIGITAL SCALE أو LOUDNESS أو كليْهما)</label>
                        
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                            <button type="button" onclick="toggleTechStandardCategory('digitalScale')" id="catBtn-digitalScale" class="p-4 rounded-2xl border border-slate-800 bg-slate-900 text-xs font-black text-slate-300 flex items-center justify-between transition-all">
                                <span class="flex items-center gap-2">
                                    <i id="checkIcon-digitalScale" class="fa-regular fa-square text-slate-500 text-base"></i>
                                    <span>DIGITAL SCALE</span>
                                </span>
                                <span id="selectedDigitalScaleLabel" class="hidden px-2.5 py-1 rounded-lg bg-amber-500 text-slate-950 font-mono text-[11px]">-6 dB</span>
                            </button>
                            <button type="button" onclick="toggleTechStandardCategory('loudness')" id="catBtn-loudness" class="p-4 rounded-2xl border border-slate-800 bg-slate-900 text-xs font-black text-slate-300 flex items-center justify-between transition-all">
                                <span class="flex items-center gap-2">
                                    <i id="checkIcon-loudness" class="fa-regular fa-square text-slate-500 text-base"></i>
                                    <span>LOUDNESS</span>
                                </span>
                                <span id="selectedLoudnessLabel" class="hidden px-2.5 py-1 rounded-lg bg-cyan-500 text-slate-950 font-mono text-[11px]">YOUTUBE</span>
                            </button>
                        </div>

                        <div id="panel-digitalScale" class="hidden pt-2 space-y-2 border-t border-slate-800">
                            <p class="text-[11px] text-amber-400 font-bold">اختر القيمة المطلوبة</p>
                            <div class="grid grid-cols-2 sm:grid-cols-4 gap-2" id="digitalScaleOptionsWrap"></div>
                        </div>

                        <div id="panel-loudness" class="hidden pt-2 space-y-2 border-t border-slate-800">
                            <p class="text-[11px] text-cyan-400 font-bold">اختر المعيار أو المنصة</p>
                            <div class="grid grid-cols-2 sm:grid-cols-3 gap-2" id="loudnessOptionsWrap"></div>
                        </div>
                    </div>

                    <!-- Deliverables -->
                    <div class="space-y-2.5">
                        <div class="flex items-center justify-between flex-wrap gap-2">
                            <label class="text-xs font-bold text-slate-300">الملفات المطلوبة للتسليم</label>
                            <button type="button" onclick="toggleCustomDeliverableInput()" class="text-xs font-bold text-amber-400 hover:underline">+ إضافة طلب خاص</button>
                        </div>
                        <div id="deliverablesButtonsWrap" class="flex flex-wrap gap-2"></div>
                        <div id="customDeliverableBox" class="hidden flex items-center gap-2 pt-2">
                            <input type="text" id="customDeliverableInput" placeholder="اسم الملف (مثال: STEMS)" class="flex-1 px-3 py-2 rounded-xl bg-slate-950 border border-slate-800 text-xs text-white">
                            <button type="button" onclick="confirmAddCustomDeliverable()" class="px-4 py-2 rounded-xl bg-amber-500 text-slate-950 text-xs font-black">إضافة</button>
                        </div>
                    </div>

                    <!-- Link & Duration -->
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 bg-slate-950/60 p-5 rounded-3xl border border-slate-800">
                        <div>
                            <label class="block text-xs font-bold text-slate-300 mb-1.5">رابط الملفات الخام (Drive)</label>
                            <input type="url" id="newProjRawLink" placeholder="https://drive.google.com/..." class="w-full px-4 py-3 rounded-2xl bg-slate-900 border border-slate-800 text-xs text-white font-mono shadow-inner">
                        </div>
                        <div>
                            <label class="block text-xs font-bold text-slate-300 mb-1.5">مدة الحلقة الأولى (بالدقائق)</label>
                            <input type="number" id="newProjDurationMin" value="5" min="1" class="w-full px-4 py-3 rounded-2xl bg-slate-900 border border-slate-800 text-xs text-white font-mono shadow-inner">
                        </div>
                        <div class="md:col-span-2">
                            <label class="block text-xs font-bold text-amber-400 mb-1.5">موعد التسليم المقترح</label>
                            <input type="datetime-local" id="newProjDeliveryDate" class="w-full px-4 py-3 rounded-2xl bg-slate-900 border border-amber-500/40 text-xs text-white font-mono shadow-inner">
                        </div>
                    </div>

                    <button type="submit" class="w-full py-4 rounded-2xl btn-3d text-slate-950 font-black text-sm shadow-xl transition-all">
                        <i class="fa-solid fa-paper-plane ml-1.5"></i> إرسال المشروع للمهندس
                    </button>
                </form>
            </div>
        </section>
    </main>

    <!-- MODALS (3D GLASS) -->
    <div id="addEpisodeModal" class="fixed inset-0 z-50 hidden bg-slate-950/85 backdrop-blur-md items-center justify-center p-4">
        <div class="max-w-md w-full glass-3d rounded-3xl p-6 space-y-4 shadow-2xl">
            <h3 class="text-base font-black text-white flex items-center justify-between border-b border-slate-800 pb-3">
                <span>إضافة حلقة جديدة بالترتيب</span>
                <button onclick="closeAddEpisodeModal()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </h3>
            <div class="space-y-3">
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">عنوان الحلقة</label>
                    <input type="text" id="modalEpTitle" placeholder="الحلقة الثانية" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white shadow-inner">
                </div>
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">المدة (دقائق)</label>
                    <input type="number" id="modalEpDuration" value="10" min="1" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white font-mono shadow-inner">
                </div>
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">رابط الملفات الخام</label>
                    <input type="url" id="modalEpRawLink" placeholder="https://..." class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white font-mono shadow-inner">
                </div>
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">موعد التسليم</label>
                    <input type="date" id="modalEpDeliveryDate" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white font-mono shadow-inner">
                </div>
            </div>
            <button onclick="confirmSaveNewEpisode()" class="w-full py-3.5 rounded-2xl btn-3d text-slate-950 font-black text-xs shadow-lg">حفظ الحلقة وإرسال إشعار</button>
        </div>
    </div>

    <div id="markerUploadModal" class="fixed inset-0 z-50 hidden bg-slate-950/85 backdrop-blur-md items-center justify-center p-4">
        <div class="max-w-md w-full glass-3d rounded-3xl p-6 space-y-4 shadow-2xl">
            <h3 class="text-base font-black text-white flex items-center justify-between border-b border-slate-800 pb-3">
                <span>إضافة صورة / ماركر تعديل</span>
                <button onclick="closeMarkerUploadModal()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </h3>
            <div class="space-y-3">
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">عنوان الماركر</label>
                    <input type="text" id="modalMarkerTitle" placeholder="خفض الموسيقى" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white shadow-inner">
                </div>
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">التوقيت الزمني</label>
                    <input type="text" id="modalMarkerTimecode" value="01:15" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white font-mono shadow-inner">
                </div>
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">ملاحظة</label>
                    <textarea id="modalMarkerNote" rows="2" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white shadow-inner"></textarea>
                </div>
            </div>
            <button onclick="saveMarkerToEpisode()" class="w-full py-3.5 rounded-2xl btn-3d text-slate-950 font-black text-xs shadow-lg">حفظ وإرفاق</button>
        </div>
    </div>

    <div id="newClientModal" class="fixed inset-0 z-50 hidden bg-slate-950/85 backdrop-blur-md items-center justify-center p-4">
        <div class="max-w-md w-full glass-3d rounded-3xl p-6 space-y-4 shadow-2xl">
            <h3 class="text-base font-black text-white flex items-center justify-between border-b border-slate-800 pb-3">
                <span>إنشاء حساب جديد</span>
                <button onclick="closeNewClientModal()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </h3>
            <div class="space-y-3">
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">نوع الحساب</label>
                    <select id="newAccountRoleType" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white font-bold shadow-inner">
                        <option value="client">حساب عميل (معزول وسري)</option>
                        <option value="engineer">حساب مهندس صوت</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">الاسم</label>
                    <input type="text" id="newClientNameInput" placeholder="اسم العميل أو الشركة" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white shadow-inner">
                </div>
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">كود الدخول / الحساب</label>
                    <input type="text" id="newClientCodeInput" placeholder="SADA-500" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white font-mono shadow-inner">
                </div>
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">كلمة السر المؤكدة</label>
                    <input type="password" id="newClientPassInput" placeholder="كلمة السر" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white font-mono shadow-inner">
                </div>
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">تأكيد كلمة السر</label>
                    <input type="password" id="newClientPassConfirmInput" placeholder="إعادة كلمة السر" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white font-mono shadow-inner">
                </div>
                <div id="newAccountErrorMsg" class="hidden p-2.5 rounded-xl bg-rose-500/10 border border-rose-500/30 text-rose-400 text-xs text-center font-bold"></div>
            </div>
            <button onclick="saveNewClientAccount()" class="w-full py-3.5 rounded-2xl bg-emerald-500 text-slate-950 font-black text-xs shadow-lg">حفظ الحساب بكلمة السر</button>
        </div>
    </div>

    <div id="changePasswordModal" class="fixed inset-0 z-50 hidden bg-slate-950/85 backdrop-blur-md items-center justify-center p-4">
        <div class="max-w-md w-full glass-3d rounded-3xl p-6 space-y-4 shadow-2xl">
            <h3 class="text-base font-black text-white flex items-center justify-between border-b border-slate-800 pb-3">
                <span>تغيير كلمة السر الخاصة بحسابك</span>
                <button onclick="closeChangePasswordModal()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </h3>
            <div class="space-y-3">
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">كلمة السر الحالية</label>
                    <input type="password" id="currentPassInput" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white font-mono shadow-inner">
                </div>
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">كلمة السر الجديدة</label>
                    <input type="password" id="newPassInput" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white font-mono shadow-inner">
                </div>
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">تأكيد كلمة السر الجديدة</label>
                    <input type="password" id="confirmNewPassInput" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white font-mono shadow-inner">
                </div>
                <div id="changePassErrorMsg" class="hidden p-2.5 rounded-xl bg-rose-500/10 border border-rose-500/30 text-rose-400 text-xs text-center font-bold"></div>
            </div>
            <button onclick="confirmChangeOwnPassword()" class="w-full py-3.5 rounded-2xl btn-3d text-slate-950 font-black text-xs shadow-lg">حفظ وتأكيد</button>
        </div>
    </div>

    <div id="adminResetPassModal" class="fixed inset-0 z-50 hidden bg-slate-950/85 backdrop-blur-md items-center justify-center p-4">
        <div class="max-w-md w-full glass-3d rounded-3xl p-6 space-y-4 shadow-2xl">
            <h3 class="text-base font-black text-white flex items-center justify-between border-b border-slate-800 pb-3">
                <span>تعيين كلمة سر جديدة</span>
                <button onclick="closeAdminResetPassModal()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </h3>
            <p id="adminResetTargetTitle" class="text-xs text-amber-400 font-bold"></p>
            <div class="space-y-3">
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">كلمة السر الجديدة</label>
                    <input type="password" id="adminResetNewPass" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white font-mono shadow-inner">
                </div>
                <div>
                    <label class="block text-xs font-bold text-slate-300 mb-1">تأكيد كلمة السر</label>
                    <input type="password" id="adminResetConfirmPass" class="w-full px-4 py-3 rounded-2xl bg-slate-950 border border-slate-800 text-xs text-white font-mono shadow-inner">
                </div>
            </div>
            <button onclick="confirmAdminResetPassword()" class="w-full py-3.5 rounded-2xl btn-3d text-slate-950 font-black text-xs shadow-lg">تحديث كلمة السر</button>
        </div>
    </div>

    <div id="notificationsModal" class="fixed inset-0 z-50 hidden bg-slate-950/85 backdrop-blur-md items-center justify-center p-4">
        <div class="max-w-md w-full glass-3d rounded-3xl p-5 space-y-4 shadow-2xl">
            <div class="flex items-center justify-between border-b border-slate-800 pb-3">
                <h3 class="text-sm font-black text-white"><i class="fa-solid fa-bell text-amber-400 ml-1.5"></i> سجل الإشعارات الفورية</h3>
                <button onclick="toggleNotificationsModal()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </div>
            <div id="notificationsListContainer" class="max-h-80 overflow-y-auto space-y-2.5"></div>
        </div>
    </div>

    <div id="toastContainer" class="fixed bottom-6 left-6 z-50 hidden px-5 py-3.5 rounded-2xl btn-3d text-slate-950 font-black text-xs shadow-2xl"></div>

    <script>
        const STORAGE_KEY = 'studio_aziz_hasan_v7_3d';

        let appState = {
            currentRole: 'admin',
            loggedAccountId: 'sys-admin',
            adminViewMode: 'engineer-view',
            activeClientId: 'client-1',
            activeAdminTab: 'dashboard',
            activeClientTab: 'projects-room',
            expandedClientProjectId: 'proj-1',
            activeClientProjectSubTab: 'episodes',
            activeEpisodeNum: 1,
            modalTargetProjectId: null,
            modalTargetEpisodeNum: 1,
            adminResetTarget: null,
            revealedPasswords: {},
            systemAccounts: [
                { id: 'sys-admin', role: 'admin', name: 'الأدمن الرئيسي', username: 'admin', password: '123456' },
                { id: 'sys-eng-1', role: 'engineer', name: 'المهندس Aziz hasan', username: 'aziz', password: '123456' }
            ],
            newProjectForm: {
                tasks: { edit: true, mix: true, soundFx: false, soundDesign: false, music: false },
                outputModes: { stereo: true, surround: false },
                enableDigitalScale: false,
                enableLoudness: false,
                digitalScale: '-6 dB',
                loudnessStandard: 'YOUTUBE',
                deliverables: ['FULL MIX', 'VOCAL', 'M&E'],
                allDeliverableOptions: ['FULL MIX', 'VOCAL', 'M&E']
            },
            clients: [
                { id: 'client-1', name: 'شركة الإبداع للإنتاج', accessCode: 'SADA-882', password: '123' },
                { id: 'client-2', name: 'استوديو الصوت الذهبي', accessCode: 'SADA-991', password: '123' }
            ],
            projects: [
                {
                    id: 'proj-1',
                    clientId: 'client-1',
                    projectName: 'مسلسل ما وراء الطبيعة',
                    projectSize: 'مسلسل',
                    tasks: { edit: true, mix: true, soundDesign: true, soundFx: true, music: false },
                    outputMode: 'Stereo + Surround',
                    digitalScale: '-6 dB',
                    loudnessStandard: 'NETFLIX',
                    deliverables: ['FULL MIX', 'VOCAL', 'M&E'],
                    status: 'قيد العمل والتنفيذ',
                    pricePerMin: 25,
                    finalMasterLink: 'https://drive.google.com/drive/folders/master-files-aziz',
                    episodes: [
                        {
                            episodeNum: 1,
                            episodeName: 'الحلقة الأولى',
                            durationMin: 40,
                            customPricePerMin: null,
                            deliveryDate: '2026-11-10',
                            externalRawLink: 'https://drive.google.com/file/d/ep1-raw',
                            markers: [
                                { title: 'موازنة المؤثرات مع الحوار', timecode: '04:15', note: 'تخفيف صوت الخلفية', uploader: 'المهندس' }
                            ]
                        }
                    ],
                    payments: [
                        { id: 'pay-1', amount: 800, date: '2026-11-01', note: 'دفعة أولى عند البدء' }
                    ]
                }
            ],
            notifications: [
                { id: 'n-1', title: 'تم قبول المشروع', message: 'قام المهندس عزيز حسن بقبول المشروع بنجاح.', time: 'منذ ساعة' }
            ],
            aiSuggestions: [
                { id: 'ai-1', title: 'تحليل أداء 3D', desc: 'تم ضبط جودة معالجة الصوتيات وتنسيق القنوات بدقة متناهية.', impact: 'كفاءة 100%' }
            ]
        };

        function saveState() {
            try { localStorage.setItem(STORAGE_KEY, JSON.stringify(appState)); } catch(e){}
        }

        function loadState() {
            try {
                const raw = localStorage.getItem(STORAGE_KEY);
                if (raw) appState = Object.assign({}, appState, JSON.parse(raw));
            } catch(e){}
        }

        function showToast(msg) {
            const t = document.getElementById('toastContainer');
            if(!t) return;
            t.textContent = msg;
            t.classList.remove('hidden');
            setTimeout(() => t.classList.add('hidden'), 3200);
        }

        function forceCloudSyncNow() {
            saveState();
            const st = document.getElementById('cloudStatusText');
            if(st) {
                st.textContent = 'جاري المزامنة...';
                setTimeout(() => { st.textContent = 'سحابة حية 3D (مُحدّث)'; }, 600);
            }
            showToast('تمت المزامنة السحابية 3D بنجاح');
        }

        function openLoginScreen() {
            const m = document.getElementById('loginScreenModal');
            if(m) { m.classList.remove('hidden'); m.classList.add('flex'); }
        }

        function closeLoginScreen() {
            const m = document.getElementById('loginScreenModal');
            if(m) { m.classList.add('hidden'); m.classList.remove('flex'); }
        }

        function logoutToLoginScreen() {
            document.getElementById('loginPasswordInput').value = '';
            document.getElementById('loginErrorMsg').classList.add('hidden');
            openLoginScreen();
        }

        function handleUserLoginSubmit(event) {
            event.preventDefault();
            const u = document.getElementById('loginUsernameInput').value.trim();
            const p = document.getElementById('loginPasswordInput').value.trim();
            const err = document.getElementById('loginErrorMsg');

            const sys = (appState.systemAccounts || []).find(acc => acc.username.toLowerCase() === u.toLowerCase() || (acc.role === 'admin' && (u === 'ادمن' || u === 'أدمن')) || (acc.role === 'engineer' && (u.toLowerCase() === 'engineer' || u === 'مهندس')));
            if(sys && p === sys.password) {
                appState.currentRole = sys.role;
                appState.loggedAccountId = sys.id;
                if(sys.role === 'admin') appState.adminViewMode = 'engineer-view';
                saveState();
                closeLoginScreen();
                renderApp();
                showToast('مرحباً بك في لوحة 3D Pro');
                return;
            }

            const cli = appState.clients.find(c => c.accessCode.toLowerCase() === u.toLowerCase());
            if(cli && p === String(cli.password)) {
                appState.currentRole = 'client';
                appState.loggedAccountId = cli.id;
                appState.activeClientId = cli.id;
                const fp = appState.projects.find(x => x.clientId === cli.id);
                appState.expandedClientProjectId = fp ? fp.id : null;
                saveState();
                closeLoginScreen();
                renderApp();
                showToast('مرحباً بك: ' + cli.name);
                return;
            }

            if(err) {
                err.textContent = 'بيانات الدخول غير صحيحة أو كلمة السر غير مؤكدة!';
                err.classList.remove('hidden');
            }
        }

        function switchAdminViewMode(m) {
            if(appState.currentRole !== 'admin') return;
            appState.adminViewMode = m;
            saveState();
            renderApp();
        }

        function changeActiveClient(id) {
            appState.activeClientId = id;
            const fp = appState.projects.find(p => p.clientId === id);
            appState.expandedClientProjectId = fp ? fp.id : null;
            appState.activeEpisodeNum = 1;
            saveState();
            renderApp();
        }

        function calculateEpisodeCost(p, ep) {
            const r = (ep.customPricePerMin !== null && ep.customPricePerMin !== undefined && ep.customPricePerMin !== '') ? Number(ep.customPricePerMin) : Number(p.pricePerMin || 0);
            return Number(ep.durationMin || 0) * r;
        }

        function calculateProjectTotalCost(p) {
            if(!p.episodes || p.episodes.length === 0) return 0;
            return p.episodes.reduce((s, ep) => s + calculateEpisodeCost(p, ep), 0);
        }

        function calculateProjectPaidAmount(p) {
            if(!p.payments || p.payments.length === 0) return 0;
            return p.payments.reduce((s, pay) => s + Number(pay.amount || 0), 0);
        }

        function renderApp() {
            const role = appState.currentRole;
            const adminWs = document.getElementById('adminWorkspace');
            const clientWs = document.getElementById('clientWorkspace');
            const dualBar = document.getElementById('adminDualViewBar');
            const badge = document.getElementById('currentUserBadge');
            const btnCreateAcc = document.getElementById('btnCreateNewAccount');
            const tabClients = document.getElementById('adminTabBtn-clients');
            const unread = document.getElementById('notifUnreadBadge');

            if(unread) {
                unread.textContent = appState.notifications.length;
                unread.classList.toggle('hidden', appState.notifications.length === 0);
            }

            if(role === 'admin') {
                dualBar.classList.remove('hidden');
                dualBar.classList.add('flex');
                if(btnCreateAcc) btnCreateAcc.classList.remove('hidden');
                if(tabClients) tabClients.classList.remove('hidden');
                if(badge) badge.innerHTML = `<i class="fa-solid fa-crown text-amber-400"></i> الأدمن`;

                const sel = document.getElementById('adminClientPreviewSelect');
                if(sel) {
                    sel.innerHTML = appState.clients.map(c => `<option value="${c.id}" ${c.id === appState.activeClientId ? 'selected' : ''}>${c.name}</option>`).join('');
                }

                const bE = document.getElementById('btnAdminViewEng');
                const bC = document.getElementById('btnAdminViewClient');
                if(appState.adminViewMode === 'client-view') {
                    bE.className = 'px-3.5 py-2 rounded-xl text-xs font-bold transition-all text-slate-400 hover:text-white';
                    bC.className = 'px-3.5 py-2 rounded-xl text-xs font-black transition-all bg-amber-500 text-slate-950 shadow-md';
                    adminWs.classList.add('hidden');
                    clientWs.classList.remove('hidden');
                    renderClientWorkspace();
                } else {
                    bE.className = 'px-3.5 py-2 rounded-xl text-xs font-black transition-all bg-amber-500 text-slate-950 shadow-md';
                    bC.className = 'px-3.5 py-2 rounded-xl text-xs font-bold transition-all text-slate-400 hover:text-white';
                    adminWs.classList.remove('hidden');
                    clientWs.classList.add('hidden');
                    renderAdminWorkspace();
                }
            } else if(role === 'engineer') {
                dualBar.classList.add('hidden');
                dualBar.classList.remove('flex');
                if(btnCreateAcc) btnCreateAcc.classList.add('hidden');
                if(tabClients) tabClients.classList.add('hidden');
                if(appState.activeAdminTab === 'clients') appState.activeAdminTab = 'dashboard';
                if(badge) badge.innerHTML = `<i class="fa-solid fa-sliders text-amber-400"></i> مهندس الصوت`;
                adminWs.classList.remove('hidden');
                clientWs.classList.add('hidden');
                renderAdminWorkspace();
            } else {
                dualBar.classList.add('hidden');
                dualBar.classList.remove('flex');
                const cli = appState.clients.find(c => c.id === appState.activeClientId) || appState.clients[0];
                if(badge && cli) badge.innerHTML = `<i class="fa-solid fa-user-lock text-amber-400"></i> ${cli.name}`;
                adminWs.classList.add('hidden');
                clientWs.classList.remove('hidden');
                renderClientWorkspace();
            }
        }

        function switchAdminTab(tab) {
            appState.activeAdminTab = tab;
            ['dashboard', 'clients', 'ai'].forEach(t => {
                const b = document.getElementById('adminTabBtn-' + t);
                const v = document.getElementById('adminSubView-' + t);
                if(b) b.className = (t === tab) ? 'px-4 py-2.5 rounded-xl text-xs font-black transition-all bg-amber-500 text-slate-950 shadow-md' : 'px-4 py-2.5 rounded-xl text-xs font-bold transition-all bg-slate-900/80 text-slate-300 hover:text-white border border-slate-800';
                if(v) v.classList.toggle('hidden', t !== tab);
            });
            renderAdminWorkspace();
        }

        function renderAdminWorkspace() {
            let totRev = 0, totPaid = 0;
            appState.projects.forEach(p => {
                totRev += calculateProjectTotalCost(p);
                totPaid += calculateProjectPaidAmount(p);
            });
            const totDue = Math.max(0, totRev - totPaid);

            const kpi = document.getElementById('adminSummaryCards');
            if(kpi) {
                kpi.innerHTML = `
                    <div class="glass-3d rounded-3xl p-5 space-y-1">
                        <span class="text-xs text-slate-400 font-bold">المشاريع النشطة</span>
                        <div class="text-2xl font-black text-white">${appState.projects.length} مشاريع</div>
                    </div>
                    <div class="glass-3d rounded-3xl p-5 space-y-1">
                        <span class="text-xs text-slate-400 font-bold">إجمالي العقود</span>
                        <div class="text-2xl font-black text-amber-400 font-mono">$${totRev.toLocaleString()}</div>
                    </div>
                    <div class="glass-3d rounded-3xl p-5 space-y-1">
                        <span class="text-xs text-slate-400 font-bold">الدفعات المستلمة</span>
                        <div class="text-2xl font-black text-emerald-400 font-mono">$${totPaid.toLocaleString()}</div>
                    </div>
                    <div class="glass-3d rounded-3xl p-5 space-y-1">
                        <span class="text-xs text-slate-400 font-bold">المتبقي</span>
                        <div class="text-2xl font-black text-rose-400 font-mono">$${totDue.toLocaleString()}</div>
                    </div>
                `;
            }

            const plist = document.getElementById('adminProjectsList');
            if(plist) {
                plist.innerHTML = appState.projects.map(p => {
                    const cli = appState.clients.find(c => c.id === p.clientId) || { name: 'عميل' };
                    const tCost = calculateProjectTotalCost(p);
                    const pPaid = calculateProjectPaidAmount(p);
                    const rem = Math.max(0, tCost - pPaid);

                    return `
                        <div class="glass-3d rounded-3xl p-6 space-y-5">
                            <div class="flex flex-wrap items-center justify-between gap-3 border-b border-slate-800 pb-4">
                                <div>
                                    <div class="flex items-center gap-2">
                                        <span class="px-3 py-1 rounded-xl bg-amber-500/20 text-amber-400 border border-amber-500/40 text-xs font-black shadow-md">${p.projectSize}</span>
                                        <h3 class="text-lg font-black text-white">${p.projectName}</h3>
                                        <span class="text-xs text-slate-400">— العميل: <strong class="text-cyan-400">${cli.name}</strong></span>
                                    </div>
                                    <div class="flex flex-wrap items-center gap-2 mt-2 text-[11px] text-slate-300">
                                        <span class="px-2.5 py-1 rounded-xl bg-slate-900 font-mono border border-slate-800">الإخراج: ${p.outputMode}</span>
                                        ${p.digitalScale ? `<span class="px-2.5 py-1 rounded-xl bg-amber-500/15 text-amber-300 border border-amber-500/30 font-mono">DIGITAL SCALE: ${p.digitalScale}</span>` : ''}
                                        ${p.loudnessStandard ? `<span class="px-2.5 py-1 rounded-xl bg-cyan-500/15 text-cyan-300 border border-cyan-500/30 font-mono">LOUDNESS: ${p.loudnessStandard}</span>` : ''}
                                    </div>
                                </div>
                                <select onchange="adminChangeProjectStatus('${p.id}', this.value)" class="px-3.5 py-2.5 rounded-2xl bg-slate-950 border border-amber-500/40 text-amber-400 text-xs font-bold shadow-inner">
                                    <option value="بانتظار الاستلام" ${p.status === 'بانتظار الاستلام' ? 'selected' : ''}>بانتظار الاستلام</option>
                                    <option value="قيد العمل والتنفيذ" ${p.status === 'قيد العمل والتنفيذ' ? 'selected' : ''}>قيد العمل والتنفيذ</option>
                                    <option value="تم قبول التسليم" ${p.status === 'تم قبول التسليم' ? 'selected' : ''}>تم قبول التسليم</option>
                                </select>
                            </div>

                            <div class="grid grid-cols-1 lg:grid-cols-2 gap-4 bg-slate-950/70 p-5 rounded-2xl border border-slate-800 shadow-inner">
                                <div class="space-y-3">
                                    <h4 class="text-xs font-black text-amber-400">التسعير والمستحقات</h4>
                                    <div class="flex flex-wrap items-center gap-3">
                                        <div>
                                            <label class="block text-[11px] text-slate-400 mb-1">سعر الدقيقة ($)</label>
                                            <input type="number" value="${p.pricePerMin || 0}" onchange="adminUpdateProjectMinuteRate('${p.id}', this.value)" class="w-28 px-3.5 py-2 rounded-xl bg-slate-900 border border-slate-700 text-white font-mono text-xs shadow-inner">
                                        </div>
                                        <div class="text-xs space-y-0.5">
                                            <div>الإجمالي: <strong class="font-mono text-amber-400">$${tCost.toLocaleString()}</strong></div>
                                            <div>المتبقي: <strong class="font-mono text-rose-400">$${rem.toLocaleString()}</strong></div>
                                        </div>
                                    </div>
                                    <div>
                                        <label class="block text-[11px] text-slate-400 mb-1">رابط الماستر النهائي</label>
                                        <input type="url" value="${p.finalMasterLink || ''}" onchange="adminUpdateFinalLink('${p.id}', this.value)" class="w-full px-3.5 py-2 rounded-xl bg-slate-900 border border-slate-700 text-white font-mono text-xs shadow-inner">
                                    </div>
                                </div>

                                <div class="space-y-2.5">
                                    <h4 class="text-xs font-black text-emerald-400">سجل الدفعات المسددة الفعلية مع التاريخ</h4>
                                    <div class="space-y-1.5 max-h-28 overflow-y-auto">
                                        ${(p.payments || []).map(pay => `
                                            <div class="flex items-center justify-between text-xs bg-slate-900 px-3.5 py-2 rounded-xl border border-slate-800">
                                                <span><strong class="text-emerald-400 font-mono">$${pay.amount}</strong> — ${pay.note} (${pay.date})</span>
                                                <button onclick="adminDeletePayment('${p.id}', '${pay.id}')" class="text-rose-400 hover:text-rose-300"><i class="fa-solid fa-trash-can"></i></button>
                                            </div>
                                        `).join('') || '<p class="text-[11px] text-slate-500">لا توجد دفعات مسجلة</p>'}
                                    </div>
                                    <div class="flex flex-wrap items-center gap-2 pt-1">
                                        <input type="number" id="payAmt-${p.id}" placeholder="المبلغ $" class="w-24 px-3 py-2 rounded-xl bg-slate-900 border border-slate-700 text-xs text-white font-mono shadow-inner">
                                        <input type="date" id="payDate-${p.id}" value="2026-11-05" class="px-3 py-2 rounded-xl bg-slate-900 border border-slate-700 text-xs text-white font-mono shadow-inner">
                                        <input type="text" id="payNote-${p.id}" placeholder="ملاحظة" class="flex-1 min-w-[90px] px-3 py-2 rounded-xl bg-slate-900 border border-slate-700 text-xs text-white shadow-inner">
                                        <button onclick="adminAddPayment('${p.id}')" class="px-3.5 py-2 rounded-xl bg-emerald-500 text-slate-950 font-black text-xs shadow-md">+ تسديد</button>
                                    </div>
                                </div>
                            </div>

                            <div class="space-y-3">
                                <div class="flex items-center justify-between">
                                    <h4 class="text-xs font-black text-white">الحلقات المرقمة (${(p.episodes || []).length})</h4>
                                    <button onclick="openAddEpisodeModal('${p.id}')" class="px-3.5 py-2 rounded-xl bg-amber-500/15 hover:bg-amber-500 text-amber-400 hover:text-slate-950 border border-amber-500/30 text-xs font-black transition-all shadow-md">
                                        + إضافة حلقة جديدة
                                    </button>
                                </div>
                                <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
                                    ${(p.episodes || []).map(ep => `
                                        <div class="bg-slate-950 border border-slate-800 rounded-2xl p-4 space-y-2.5 shadow-inner">
                                            <div class="flex items-center justify-between">
                                                <span class="px-3 py-1 rounded-xl bg-amber-500 text-slate-950 font-black text-xs shadow-md">حلقة #${ep.episodeNum} — ${ep.episodeName}</span>
                                                <button onclick="adminDeleteEpisode('${p.id}', ${ep.episodeNum})" class="text-rose-400 hover:text-rose-300 text-xs"><i class="fa-solid fa-trash"></i></button>
                                            </div>
                                            <div class="grid grid-cols-3 gap-2 text-[11px]">
                                                <div>
                                                    <label class="text-slate-400 block mb-1">المدة (د)</label>
                                                    <input type="number" value="${ep.durationMin}" onchange="adminUpdateEpisodeDuration('${p.id}', ${ep.episodeNum}, this.value)" class="w-full px-2.5 py-1.5 rounded-xl bg-slate-900 border border-slate-700 text-white font-mono shadow-inner">
                                                </div>
                                                <div>
                                                    <label class="text-slate-400 block mb-1">سعر خاص</label>
                                                    <input type="number" value="${ep.customPricePerMin || ''}" onchange="adminUpdateEpisodeCustomRate('${p.id}', ${ep.episodeNum}, this.value)" class="w-full px-2.5 py-1.5 rounded-xl bg-slate-900 border border-slate-700 text-white font-mono shadow-inner">
                                                </div>
                                                <div>
                                                    <label class="text-slate-400 block mb-1">التكلفة</label>
                                                    <div class="px-2.5 py-1.5 rounded-xl bg-slate-900 text-amber-400 font-mono font-bold shadow-inner">$${calculateEpisodeCost(p, ep).toLocaleString()}</div>
                                                </div>
                                            </div>
                                        </div>
                                    `).join('')}
                                </div>
                            </div>
                        </div>
                    `;
                }).join('');
            }

            const sysGrid = document.getElementById('adminSystemAccountsGrid');
            if(sysGrid && appState.currentRole === 'admin') {
                sysGrid.innerHTML = (appState.systemAccounts || []).map(acc => {
                    const isRev = !!appState.revealedPasswords[acc.id];
                    return `
                        <div class="bg-slate-950 border border-slate-800 rounded-2xl p-4 space-y-3 shadow-inner">
                            <div class="flex items-center justify-between">
                                <h4 class="text-sm font-black text-white">${acc.name}</h4>
                                <span class="px-3 py-1 rounded-xl bg-slate-900 text-amber-400 font-mono text-xs font-bold">${acc.username}</span>
                            </div>
                            <div class="flex items-center justify-between text-xs bg-slate-900 px-3.5 py-2.5 rounded-xl border border-slate-800">
                                <span class="text-slate-400">كلمة السر: <strong class="text-white font-mono">${isRev ? acc.password : '••••••••'}</strong></span>
                                <button onclick="toggleRevealPassword('${acc.id}')" class="text-slate-400 hover:text-amber-400"><i class="fa-solid ${isRev ? 'fa-eye-slash' : 'fa-eye'}"></i></button>
                            </div>
                            <button onclick="openAdminResetPassModal('system', '${acc.id}')" class="w-full py-2.5 rounded-xl bg-amber-500/15 text-amber-400 border border-amber-500/30 text-xs font-black shadow-md">تعديل كلمة السر</button>
                        </div>
                    `;
                }).join('');
            }

            const cliGrid = document.getElementById('adminClientsGrid');
            if(cliGrid && appState.currentRole === 'admin') {
                cliGrid.innerHTML = appState.clients.map(c => {
                    const isRev = !!appState.revealedPasswords[c.id];
                    return `
                        <div class="bg-slate-950 border border-slate-800 rounded-2xl p-4 space-y-3 shadow-inner">
                            <div class="flex items-center justify-between">
                                <h4 class="text-sm font-black text-white">${c.name}</h4>
                                <span class="px-3 py-1 rounded-xl bg-emerald-500/15 text-emerald-400 font-mono text-xs font-bold">${c.accessCode}</span>
                            </div>
                            <div class="flex items-center justify-between bg-slate-900 px-3.5 py-2.5 rounded-xl border border-slate-800 text-xs">
                                <span>كلمة السر: <strong class="text-amber-400 font-mono">${isRev ? c.password : '••••••••'}</strong></span>
                                <button onclick="toggleRevealPassword('${c.id}')" class="text-slate-400 hover:text-white"><i class="fa-solid ${isRev ? 'fa-eye-slash' : 'fa-eye'}"></i></button>
                            </div>
                            <div class="flex items-center gap-2">
                                <button onclick="copyClientAccessInvite('${c.id}')" class="flex-1 py-2.5 rounded-xl bg-slate-900 hover:bg-slate-800 text-xs font-bold text-amber-400 border border-slate-800 shadow-md">نسخ الدعوة</button>
                                <button onclick="openAdminResetPassModal('client', '${c.id}')" class="px-3 py-2.5 rounded-xl bg-amber-500/15 text-amber-400 text-xs font-black shadow-md">كلمة السر</button>
                            </div>
                        </div>
                    `;
                }).join('');
            }
        }

        function switchClientTab(tab) {
            appState.activeClientTab = tab;
            ['projects-room', 'new-project'].forEach(t => {
                const b = document.getElementById('clientTabBtn-' + t);
                const v = document.getElementById('clientSubView-' + t);
                if(b) b.className = (t === tab) ? 'flex-1 py-3 px-4 rounded-xl text-xs sm:text-sm font-black transition-all bg-amber-500 text-slate-950 shadow-md' : 'flex-1 py-3 px-4 rounded-xl text-xs sm:text-sm font-bold transition-all bg-slate-900/80 text-slate-300 hover:text-white border border-slate-800';
                if(v) v.classList.toggle('hidden', t !== tab);
            });
            if(tab === 'new-project') {
                renderTechStandardOptions();
                renderDeliverablesButtons();
            } else {
                renderClientWorkspace();
            }
        }

        function renderClientWorkspace() {
            const cli = appState.clients.find(c => c.id === appState.activeClientId) || appState.clients[0];
            const cliProjs = appState.projects.filter(p => p.clientId === cli.id);

            let totCon = 0, totPaid = 0;
            let allPays = [];
            cliProjs.forEach(p => {
                totCon += calculateProjectTotalCost(p);
                totPaid += calculateProjectPaidAmount(p);
                (p.payments || []).forEach(pay => { allPays.push({ ...pay, projectName: p.projectName }); });
            });
            const totDue = Math.max(0, totCon - totPaid);

            const fHead = document.getElementById('clientFinancialHeader');
            if(fHead) {
                fHead.innerHTML = `
                    <div class="flex flex-wrap items-center justify-between gap-4 border-b border-slate-800 pb-4">
                        <div>
                            <span class="text-[11px] font-black text-amber-400">مساحة العمل الخاصة والمعزولة</span>
                            <h2 class="text-lg font-black text-white">${cli.name}</h2>
                        </div>
                        <div class="grid grid-cols-3 gap-3 w-full sm:w-auto">
                            <div class="bg-slate-950 border border-slate-800 rounded-2xl px-4 py-2.5 text-center shadow-inner">
                                <span class="text-[10px] text-slate-400 block font-bold">إجمالي المشاريع</span>
                                <strong class="text-sm font-black text-white font-mono">$${totCon.toLocaleString()}</strong>
                            </div>
                            <div class="bg-slate-950 border border-slate-800 rounded-2xl px-4 py-2.5 text-center shadow-inner">
                                <span class="text-[10px] text-slate-400 block font-bold">الدفعات المدفوعة</span>
                                <strong class="text-sm font-black text-emerald-400 font-mono">$${totPaid.toLocaleString()}</strong>
                            </div>
                            <div class="bg-slate-950 border border-rose-500/30 rounded-2xl px-4 py-2.5 text-center shadow-inner">
                                <span class="text-[10px] text-rose-300 block font-bold">المتبقي</span>
                                <strong class="text-sm font-black text-rose-400 font-mono">$${totDue.toLocaleString()}</strong>
                            </div>
                        </div>
                    </div>

                    <div class="space-y-2">
                        <h4 class="text-xs font-black text-slate-300"><i class="fa-solid fa-receipt text-emerald-400 ml-1"></i> الدفعات التي تم دفعها مع التاريخ:</h4>
                        <div class="flex flex-wrap gap-2">
                            ${allPays.map(pay => `
                                <div class="px-3.5 py-2 rounded-2xl bg-slate-950 border border-slate-800 text-xs flex items-center gap-2.5 shadow-inner">
                                    <span class="font-mono font-black text-emerald-400">$${pay.amount}</span>
                                    <span class="text-slate-300">${pay.projectName}</span>
                                    <span class="px-2.5 py-0.5 rounded-xl bg-slate-900 text-amber-400 font-mono text-[10px] border border-slate-800">${pay.date}</span>
                                </div>
                            `).join('') || '<span class="text-xs text-slate-500">لا توجد دفعات مسجلة</span>'}
                        </div>
                    </div>
                `;
            }

            const pCont = document.getElementById('clientProjectsButtonsContainer');
            if(!pCont) return;

            if(cliProjs.length === 0) {
                pCont.innerHTML = `<div class="p-8 text-center glass-3d rounded-3xl text-sm text-slate-400">لا توجد مشاريع حالية.</div>`;
                return;
            }

            pCont.innerHTML = cliProjs.map(p => {
                const isExp = (appState.expandedClientProjectId === p.id);
                const pTotCost = calculateProjectTotalCost(p);
                const selEpNum = appState.activeEpisodeNum || 1;
                const actEp = (p.episodes || []).find(e => e.episodeNum === selEpNum) || (p.episodes || [])[0];

                return `
                    <div class="glass-3d rounded-3xl overflow-hidden transition-all">
                        <button onclick="toggleClientProjectButton('${p.id}')" class="w-full p-5 flex items-center justify-between text-right hover:bg-slate-800/40 transition-all">
                            <div class="flex items-center gap-3.5">
                                <div class="w-11 h-11 rounded-2xl bg-amber-500/15 border border-amber-500/30 flex items-center justify-center text-amber-400 font-black shadow-md">
                                    <i class="fa-solid fa-folder-open text-base"></i>
                                </div>
                                <div>
                                    <div class="flex items-center gap-2">
                                        <span class="text-base font-black text-white">${p.projectName}</span>
                                        <span class="px-2.5 py-0.5 rounded-xl bg-slate-900 text-amber-400 text-[11px] font-bold border border-slate-800">${p.projectSize}</span>
                                    </div>
                                    <div class="text-xs text-slate-400 mt-0.5">الحالة: <strong class="text-emerald-400">${p.status}</strong> | الإجمالي: <strong class="text-amber-400 font-mono">$${pTotCost.toLocaleString()}</strong></div>
                                </div>
                            </div>
                            <i class="fa-solid ${isExp ? 'fa-chevron-up text-amber-400' : 'fa-chevron-down text-slate-400'}"></i>
                        </button>

                        ${isExp ? `
                            <div class="p-5 border-t border-slate-800 bg-slate-950/60 space-y-5">
                                <div class="flex items-center gap-2">
                                    <button onclick="switchClientProjectSubTab('details')" class="px-4 py-2.5 rounded-xl text-xs font-black transition-all ${appState.activeClientProjectSubTab === 'details' ? 'bg-amber-500 text-slate-950 shadow-md' : 'bg-slate-900 text-slate-300 border border-slate-800'}">تفاصيل التنفيذ</button>
                                    <button onclick="switchClientProjectSubTab('episodes')" class="px-4 py-2.5 rounded-xl text-xs font-black transition-all ${appState.activeClientProjectSubTab === 'episodes' ? 'bg-amber-500 text-slate-950 shadow-md' : 'bg-slate-900 text-slate-300 border border-slate-800'}">الحلقات (${(p.episodes || []).length})</button>

                                    ${p.finalMasterLink ? `
                                        <a href="${p.finalMasterLink}" target="_blank" class="mr-auto px-4 py-2.5 rounded-xl bg-emerald-500 text-slate-950 text-xs font-black flex items-center gap-1.5 shadow-md">
                                            <i class="fa-solid fa-cloud-arrow-down"></i>
                                            <span>تحميل التسليم النهائي</span>
                                        </a>
                                    ` : ''}
                                </div>

                                ${appState.activeClientProjectSubTab === 'details' ? `
                                    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-3 bg-slate-900 p-4 rounded-2xl border border-slate-800 text-xs shadow-inner">
                                        <div class="p-3.5 rounded-xl bg-slate-950 border border-slate-800">
                                            <span class="text-slate-400 block mb-1">حجم المشروع</span>
                                            <strong class="text-white font-bold">${p.projectSize}</strong>
                                        </div>
                                        <div class="p-3.5 rounded-xl bg-slate-950 border border-slate-800">
                                            <span class="text-slate-400 block mb-1">نظام الإخراج</span>
                                            <strong class="text-white font-mono">${p.outputMode}</strong>
                                        </div>
                                        <div class="p-3.5 rounded-xl bg-slate-950 border border-slate-800">
                                            <span class="text-slate-400 block mb-1">المعايير التقنية</span>
                                            <strong class="text-amber-400 font-mono">${p.digitalScale || ''} ${p.loudnessStandard || ''}</strong>
                                        </div>
                                    </div>
                                ` : `
                                    <div class="space-y-4">
                                        <div class="flex flex-wrap items-center gap-2">
                                            ${(p.episodes || []).map(ep => `
                                                <button onclick="selectClientEpisodeNumber(${ep.episodeNum})" class="w-12 h-12 rounded-2xl font-mono font-black text-sm transition-all ${actEp && actEp.episodeNum === ep.episodeNum ? 'bg-amber-500 text-slate-950 shadow-md' : 'bg-slate-900 text-slate-300 border border-slate-800'}">
                                                    ${ep.episodeNum}
                                                </button>
                                            `).join('')}
                                        </div>

                                        ${actEp ? `
                                            <div class="glass-3d rounded-2xl p-4 space-y-4">
                                                <div class="flex items-center justify-between border-b border-slate-800 pb-3 text-xs">
                                                    <h4 class="text-sm font-black text-white">حلقة رقم (${actEp.episodeNum}) — ${actEp.episodeName}</h4>
                                                    <span>التكلفة: <strong class="text-amber-400 font-mono">$${calculateEpisodeCost(p, actEp).toLocaleString()}</strong></span>
                                                </div>
                                                <div class="flex items-center justify-between text-xs">
                                                    <span>رابط الملفات الخام: ${actEp.externalRawLink ? `<a href="${actEp.externalRawLink}" target="_blank" class="text-cyan-400 underline font-mono">فتح الرابط</a>` : 'لا يوجد'}</span>
                                                    <button onclick="openAddMarkerModal('${p.id}', ${actEp.episodeNum})" class="px-3.5 py-2 rounded-xl bg-amber-500/15 text-amber-400 text-xs font-bold shadow-md">+ إرفاق ماركر</button>
                                                </div>
                                                <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                                                    ${(actEp.markers || []).map(m => `
                                                        <div class="bg-slate-950 border border-slate-800 rounded-xl p-3 text-xs space-y-1 shadow-inner">
                                                            <div class="flex items-center justify-between font-bold text-amber-400">
                                                                <span>${m.title}</span>
                                                                <span class="font-mono">${m.timecode}</span>
                                                            </div>
                                                            <p class="text-slate-400">${m.note || ''}</p>
                                                        </div>
                                                    `).join('')}
                                                </div>
                                            </div>
                                        ` : ''}
                                    </div>
                                `}
                            </div>
                        ` : ''}
                    </div>
                `;
            }).join('');
        }

        function toggleClientProjectButton(id) {
            appState.expandedClientProjectId = (appState.expandedClientProjectId === id) ? null : id;
            appState.activeEpisodeNum = 1;
            renderClientWorkspace();
        }

        function switchClientProjectSubTab(st) {
            appState.activeClientProjectSubTab = st;
            renderClientWorkspace();
        }

        function selectClientEpisodeNumber(num) {
            appState.activeEpisodeNum = num;
            renderClientWorkspace();
        }

        function toggleTaskItem(k) {
            appState.newProjectForm.tasks[k] = !appState.newProjectForm.tasks[k];
            updateTaskButtonsUI();
        }

        function toggleAllTasks() {
            const all = Object.values(appState.newProjectForm.tasks).every(Boolean);
            Object.keys(appState.newProjectForm.tasks).forEach(k => { appState.newProjectForm.tasks[k] = !all; });
            updateTaskButtonsUI();
        }

        function updateTaskButtonsUI() {
            Object.entries(appState.newProjectForm.tasks).forEach(([k, v]) => {
                const b = document.getElementById('taskBtn-' + k);
                if(b) b.className = v ? 'p-3.5 rounded-2xl border text-xs font-black transition-all bg-amber-500/20 border-amber-500 text-amber-300 shadow-md' : 'p-3.5 rounded-2xl border text-xs font-bold transition-all bg-slate-950 border-slate-800 text-slate-400';
            });
        }

        function toggleOutputMode(m) {
            appState.newProjectForm.outputModes[m] = !appState.newProjectForm.outputModes[m];
            const bS = document.getElementById('outBtn-stereo');
            const bSu = document.getElementById('outBtn-surround');
            const sVal = appState.newProjectForm.outputModes.stereo;
            const suVal = appState.newProjectForm.outputModes.surround;
            if(bS) bS.className = sVal ? 'p-3.5 rounded-2xl border text-xs font-black transition-all bg-amber-500/20 border-amber-500 text-amber-300 flex items-center justify-center gap-2 shadow-md' : 'p-3.5 rounded-2xl border text-xs font-bold transition-all bg-slate-950 border-slate-800 text-slate-400 flex items-center justify-center gap-2';
            if(bSu) bSu.className = suVal ? 'p-3.5 rounded-2xl border text-xs font-black transition-all bg-amber-500/20 border-amber-500 text-amber-300 flex items-center justify-center gap-2 shadow-md' : 'p-3.5 rounded-2xl border text-xs font-bold transition-all bg-slate-950 border-slate-800 text-slate-400 flex items-center justify-center gap-2';
        }

        function toggleTechStandardCategory(cat) {
            if(cat === 'digitalScale') appState.newProjectForm.enableDigitalScale = !appState.newProjectForm.enableDigitalScale;
            if(cat === 'loudness') appState.newProjectForm.enableLoudness = !appState.newProjectForm.enableLoudness;
            renderTechStandardOptions();
        }

        function renderTechStandardOptions() {
            const ds = !!appState.newProjectForm.enableDigitalScale;
            const ld = !!appState.newProjectForm.enableLoudness;

            const pDs = document.getElementById('panel-digitalScale');
            const pLd = document.getElementById('panel-loudness');
            if(pDs) pDs.classList.toggle('hidden', !ds);
            if(pLd) pLd.classList.toggle('hidden', !ld);

            const bDs = document.getElementById('catBtn-digitalScale');
            const bLd = document.getElementById('catBtn-loudness');
            const iDs = document.getElementById('checkIcon-digitalScale');
            const iLd = document.getElementById('checkIcon-loudness');
            const lDs = document.getElementById('selectedDigitalScaleLabel');
            const lLd = document.getElementById('selectedLoudnessLabel');

            if(bDs) bDs.className = ds ? 'p-4 rounded-2xl border border-amber-500 bg-amber-500/10 text-xs font-black text-white flex items-center justify-between transition-all shadow-md' : 'p-4 rounded-2xl border border-slate-800 bg-slate-900 text-xs font-black text-slate-400 flex items-center justify-between transition-all';
            if(iDs) iDs.className = ds ? 'fa-solid fa-square-check text-amber-400 text-base' : 'fa-regular fa-square text-slate-500 text-base';
            if(lDs) { lDs.textContent = appState.newProjectForm.digitalScale; lDs.classList.toggle('hidden', !ds); }

            if(bLd) bLd.className = ld ? 'p-4 rounded-2xl border border-cyan-500 bg-cyan-500/10 text-xs font-black text-white flex items-center justify-between transition-all shadow-md' : 'p-4 rounded-2xl border border-slate-800 bg-slate-900 text-xs font-black text-slate-400 flex items-center justify-between transition-all';
            if(iLd) iLd.className = ld ? 'fa-solid fa-square-check text-cyan-400 text-base' : 'fa-regular fa-square text-slate-500 text-base';
            if(lLd) { lLd.textContent = appState.newProjectForm.loudnessStandard; lLd.classList.toggle('hidden', !ld); }

            const dsOpt = ['0 dB', '-1 dB', '-6 dB', '-10 dB'];
            const dsW = document.getElementById('digitalScaleOptionsWrap');
            if(dsW) {
                dsW.innerHTML = dsOpt.map(v => `<button type="button" onclick="selectDigitalScale('${v}')" class="py-2.5 px-3 rounded-xl border font-mono text-xs font-black transition-all ${appState.newProjectForm.digitalScale === v ? 'bg-amber-500 text-slate-950 border-amber-400 shadow-md' : 'bg-slate-900 text-slate-300 border-slate-800'}">${v}</button>`).join('');
            }

            const ldOpt = ['ITU-R BS.1770.4', 'EBU R128', 'NETFLIX', 'SPOTIFY', 'YOUTUBE', 'AMAZON'];
            const ldW = document.getElementById('loudnessOptionsWrap');
            if(ldW) {
                ldW.innerHTML = ldOpt.map(v => `<button type="button" onclick="selectLoudnessStandard('${v}')" class="py-2.5 px-3 rounded-xl border font-mono text-xs font-black transition-all ${appState.newProjectForm.loudnessStandard === v ? 'bg-cyan-500 text-slate-950 border-cyan-400 shadow-md' : 'bg-slate-900 text-slate-300 border-slate-800'}">${v}</button>`).join('');
            }
        }

        function selectDigitalScale(v) {
            appState.newProjectForm.enableDigitalScale = true;
            appState.newProjectForm.digitalScale = v;
            renderTechStandardOptions();
        }

        function selectLoudnessStandard(v) {
            appState.newProjectForm.enableLoudness = true;
            appState.newProjectForm.loudnessStandard = v;
            renderTechStandardOptions();
        }

        function renderDeliverablesButtons() {
            const w = document.getElementById('deliverablesButtonsWrap');
            if(!w) return;
            w.innerHTML = appState.newProjectForm.allDeliverableOptions.map(item => {
                const act = appState.newProjectForm.deliverables.includes(item);
                return `<button type="button" onclick="toggleDeliverableItem('${item}')" class="px-4 py-2 rounded-xl border font-mono text-xs font-black transition-all ${act ? 'bg-emerald-500/20 border-emerald-500 text-emerald-300 shadow-md' : 'bg-slate-950 border-slate-800 text-slate-400'}">${item}</button>`;
            }).join('');
        }

        function toggleDeliverableItem(item) {
            const idx = appState.newProjectForm.deliverables.indexOf(item);
            if(idx > -1) appState.newProjectForm.deliverables.splice(idx, 1);
            else appState.newProjectForm.deliverables.push(item);
            renderDeliverablesButtons();
        }

        function toggleCustomDeliverableInput() {
            document.getElementById('customDeliverableBox').classList.toggle('hidden');
        }

        function confirmAddCustomDeliverable() {
            const inp = document.getElementById('customDeliverableInput');
            const v = inp.value.trim().toUpperCase();
            if(!v) return;
            if(!appState.newProjectForm.allDeliverableOptions.includes(v)) appState.newProjectForm.allDeliverableOptions.push(v);
            if(!appState.newProjectForm.deliverables.includes(v)) appState.newProjectForm.deliverables.push(v);
            inp.value = '';
            document.getElementById('customDeliverableBox').classList.add('hidden');
            renderDeliverablesButtons();
        }

        function submitClientNewProject(event) {
            event.preventDefault();
            if(!appState.newProjectForm.enableDigitalScale && !appState.newProjectForm.enableLoudness) {
                showToast('يرجى اختيار معيار تقني واحد على الأقل');
                return;
            }
            const name = document.getElementById('newProjName').value.trim();
            const size = document.getElementById('newProjSize').value;
            const raw = document.getElementById('newProjRawLink').value.trim();
            const dur = Number(document.getElementById('newProjDurationMin').value || 5);
            const deliv = document.getElementById('newProjDeliveryDate').value;

            const oArr = [];
            if(appState.newProjectForm.outputModes.stereo) oArr.push('Stereo');
            if(appState.newProjectForm.outputModes.surround) oArr.push('Surround');
            const outStr = oArr.length > 0 ? oArr.join(' + ') : 'Stereo';

            const np = {
                id: 'proj-' + Date.now(),
                clientId: appState.activeClientId,
                projectName: name,
                projectSize: size,
                tasks: { ...appState.newProjectForm.tasks },
                outputMode: outStr,
                digitalScale: appState.newProjectForm.enableDigitalScale ? appState.newProjectForm.digitalScale : null,
                loudnessStandard: appState.newProjectForm.enableLoudness ? appState.newProjectForm.loudnessStandard : null,
                deliverables: [...appState.newProjectForm.deliverables],
                status: 'بانتظار الاستلام',
                pricePerMin: 0,
                finalMasterLink: '',
                episodes: [
                    { episodeNum: 1, episodeName: 'الحلقة 1', durationMin: dur, customPricePerMin: null, deliveryDate: deliv ? deliv.slice(0, 10) : '2026-11-10', externalRawLink: raw, markers: [] }
                ],
                payments: []
            };

            appState.projects.unshift(np);
            appState.expandedClientProjectId = np.id;
            saveState();
            switchClientTab('projects-room');
            showToast('تم إرسال المشروع بنجاح');
        }

        function openAddEpisodeModal(pId) {
            appState.modalTargetProjectId = pId;
            const m = document.getElementById('addEpisodeModal');
            if(m) { m.classList.remove('hidden'); m.classList.add('flex'); }
        }

        function closeAddEpisodeModal() {
            const m = document.getElementById('addEpisodeModal');
            if(m) { m.classList.add('hidden'); m.classList.remove('flex'); }
        }

        function confirmSaveNewEpisode() {
            const p = appState.projects.find(x => x.id === appState.modalTargetProjectId);
            if(!p) return;
            const next = (p.episodes || []).length + 1;
            p.episodes.push({
                episodeNum: next,
                episodeName: document.getElementById('modalEpTitle').value.trim() || ('الحلقة ' + next),
                durationMin: Number(document.getElementById('modalEpDuration').value || 10),
                customPricePerMin: null,
                deliveryDate: document.getElementById('modalEpDeliveryDate').value || '2026-11-15',
                externalRawLink: document.getElementById('modalEpRawLink').value.trim(),
                markers: []
            });
            appState.activeEpisodeNum = next;
            saveState();
            closeAddEpisodeModal();
            renderApp();
            showToast('تمت إضافة الحلقة');
        }

        function openAddMarkerModal(pId, epNum) {
            appState.modalTargetProjectId = pId;
            appState.modalTargetEpisodeNum = epNum;
            const m = document.getElementById('markerUploadModal');
            if(m) { m.classList.remove('hidden'); m.classList.add('flex'); }
        }

        function closeMarkerUploadModal() {
            const m = document.getElementById('markerUploadModal');
            if(m) { m.classList.add('hidden'); m.classList.remove('flex'); }
        }

        function saveMarkerToEpisode() {
            const p = appState.projects.find(x => x.id === appState.modalTargetProjectId);
            if(!p) return;
            const ep = (p.episodes || []).find(e => e.episodeNum === appState.modalTargetEpisodeNum);
            if(!ep) return;

            ep.markers.push({
                title: document.getElementById('modalMarkerTitle').value.trim() || 'ماركر',
                timecode: document.getElementById('modalMarkerTimecode').value.trim() || '01:00',
                note: document.getElementById('modalMarkerNote').value.trim(),
                uploader: appState.currentRole === 'client' ? 'العميل' : 'المهندس'
            });
            saveState();
            closeMarkerUploadModal();
            renderApp();
            showToast('تمت إضافة الماركر');
        }

        function adminChangeProjectStatus(pId, st) {
            const p = appState.projects.find(x => x.id === pId);
            if(!p) return;
            p.status = st;
            saveState();
            renderApp();
            showToast('تم تحديث الحالة');
        }

        function adminUpdateProjectMinuteRate(pId, r) {
            const p = appState.projects.find(x => x.id === pId);
            if(!p) return;
            p.pricePerMin = Number(r || 0);
            saveState();
            renderApp();
        }

        function adminUpdateFinalLink(pId, l) {
            const p = appState.projects.find(x => x.id === pId);
            if(!p) return;
            p.finalMasterLink = l.trim();
            saveState();
            renderApp();
        }

        function adminAddPayment(pId) {
            const p = appState.projects.find(x => x.id === pId);
            if(!p) return;
            const amt = Number(document.getElementById('payAmt-' + pId).value || 0);
            const date = document.getElementById('payDate-' + pId).value || '2026-11-05';
            const note = document.getElementById('payNote-' + pId).value.trim() || 'دفعة';
            if(amt <= 0) return;
            p.payments.push({ id: 'pay-' + Date.now(), amount: amt, date, note });
            saveState();
            renderApp();
            showToast('تم تسجيل الدفعة');
        }

        function adminDeletePayment(pId, payId) {
            const p = appState.projects.find(x => x.id === pId);
            if(!p) return;
            p.payments = p.payments.filter(x => x.id !== payId);
            saveState();
            renderApp();
        }

        function adminUpdateEpisodeDuration(pId, epNum, d) {
            const p = appState.projects.find(x => x.id === pId);
            if(!p) return;
            const ep = p.episodes.find(e => e.episodeNum === epNum);
            if(ep) ep.durationMin = Number(d || 1);
            saveState();
            renderApp();
        }

        function adminUpdateEpisodeCustomRate(pId, epNum, r) {
            const p = appState.projects.find(x => x.id === pId);
            if(!p) return;
            const ep = p.episodes.find(e => e.episodeNum === epNum);
            if(ep) ep.customPricePerMin = r === '' ? null : Number(r);
            saveState();
            renderApp();
        }

        function adminDeleteEpisode(pId, epNum) {
            const p = appState.projects.find(x => x.id === pId);
            if(!p) return;
            p.episodes = p.episodes.filter(e => e.episodeNum !== epNum);
            p.episodes.forEach((e, i) => { e.episodeNum = i + 1; });
            saveState();
            renderApp();
        }

        function toggleRevealPassword(accId) {
            appState.revealedPasswords[accId] = !appState.revealedPasswords[accId];
            renderAdminWorkspace();
        }

        function openNewClientModal() {
            const m = document.getElementById('newClientModal');
            if(m) { m.classList.remove('hidden'); m.classList.add('flex'); }
        }

        function closeNewClientModal() {
            const m = document.getElementById('newClientModal');
            if(m) { m.classList.add('hidden'); m.classList.remove('flex'); }
        }

        function saveNewClientAccount() {
            const role = document.getElementById('newAccountRoleType').value;
            const name = document.getElementById('newClientNameInput').value.trim();
            const code = document.getElementById('newClientCodeInput').value.trim();
            const pass = document.getElementById('newClientPassInput').value.trim();
            const conf = document.getElementById('newClientPassConfirmInput').value.trim();
            const err = document.getElementById('newAccountErrorMsg');

            if(!name || !code || !pass) {
                if(err) { err.textContent = 'املأ الحقول المطلوبة!'; err.classList.remove('hidden'); }
                return;
            }
            if(pass !== conf) {
                if(err) { err.textContent = 'كلمة السر غير متطابقة!'; err.classList.remove('hidden'); }
                return;
            }

            if(role === 'engineer') {
                appState.systemAccounts.push({ id: 'sys-eng-' + Date.now(), role: 'engineer', name, username: code, password: pass });
            } else {
                appState.clients.push({ id: 'client-' + Date.now(), name, accessCode: code.toUpperCase(), password: pass });
            }
            saveState();
            closeNewClientModal();
            renderApp();
            showToast('تم إنشاء الحساب بنجاح');
        }

        function openChangePasswordModal() {
            const m = document.getElementById('changePasswordModal');
            if(m) { m.classList.remove('hidden'); m.classList.add('flex'); }
        }

        function closeChangePasswordModal() {
            const m = document.getElementById('changePasswordModal');
            if(m) { m.classList.add('hidden'); m.classList.remove('flex'); }
        }

        function confirmChangeOwnPassword() {
            const cur = document.getElementById('currentPassInput').value.trim();
            const neu = document.getElementById('newPassInput').value.trim();
            const cnf = document.getElementById('confirmNewPassInput').value.trim();
            const err = document.getElementById('changePassErrorMsg');

            if(neu !== cnf) {
                if(err) { err.textContent = 'كلمة السر الجديدة غير متطابقة!'; err.classList.remove('hidden'); }
                return;
            }

            if(appState.currentRole === 'admin' || appState.currentRole === 'engineer') {
                const sys = (appState.systemAccounts || []).find(a => a.id === appState.loggedAccountId);
                if(sys && sys.password === cur) sys.password = neu;
            } else {
                const cli = appState.clients.find(c => c.id === appState.activeClientId);
                if(cli && String(cli.password) === cur) cli.password = neu;
            }
            saveState();
            closeChangePasswordModal();
            showToast('تم تغيير كلمة السر بنجاح');
        }

        function openAdminResetPassModal(type, id) {
            appState.adminResetTarget = { type, id };
            const m = document.getElementById('adminResetPassModal');
            if(m) { m.classList.remove('hidden'); m.classList.add('flex'); }
        }

        function closeAdminResetPassModal() {
            const m = document.getElementById('adminResetPassModal');
            if(m) { m.classList.add('hidden'); m.classList.remove('flex'); }
        }

        function confirmAdminResetPassword() {
            const neu = document.getElementById('adminResetNewPass').value.trim();
            const cnf = document.getElementById('adminResetConfirmPass').value.trim();
            if(neu !== cnf) return;
            const { type, id } = appState.adminResetTarget;
            if(type === 'system') {
                const acc = (appState.systemAccounts || []).find(a => a.id === id);
                if(acc) acc.password = neu;
            } else {
                const cli = appState.clients.find(c => c.id === id);
                if(cli) cli.password = neu;
            }
            saveState();
            closeAdminResetPassModal();
            showToast('تم تحديث كلمة السر');
        }

        function copyClientAccessInvite(id) {
            const c = appState.clients.find(x => x.id === id);
            if(!c) return;
            const text = `بيانات دخولك إلى Studio Aziz hasan:\nالحساب: ${c.accessCode}\nكلمة السر: ${c.password}`;
            const ta = document.createElement('textarea');
            ta.value = text;
            document.body.appendChild(ta);
            ta.select();
            document.execCommand('copy');
            document.body.removeChild(ta);
            showToast('تم نسخ دعوة الدخول');
        }

        function generateNewAISuggestion() {
            appState.aiSuggestions.unshift({ id: 'ai-' + Date.now(), title: 'تحليل 3D جديد', desc: 'تم تحديث التوصيات الذكية للاستوديو.', impact: 'كفاءة عالية' });
            saveState();
            renderAdminWorkspace();
            showToast('تم تحديث التحليل الذكي');
        }

        function toggleNotificationsModal() {
            const m = document.getElementById('notificationsModal');
            if(!m) return;
            const isH = m.classList.contains('hidden');
            m.classList.toggle('hidden', !isH);
            m.classList.toggle('flex', isH);
            const list = document.getElementById('notificationsListContainer');
            if(list) {
                list.innerHTML = appState.notifications.map(n => `
                    <div class="p-3.5 rounded-2xl bg-slate-950 border border-slate-800 space-y-1 shadow-inner">
                        <div class="flex items-center justify-between"><strong class="text-xs text-amber-400">${n.title}</strong><span class="text-[10px] text-slate-500">${n.time}</span></div>
                        <p class="text-xs text-slate-300">${n.message}</p>
                    </div>
                `).join('');
            }
        }

        window.onload = function() {
            loadState();
            renderTechStandardOptions();
            renderDeliverablesButtons();
            openLoginScreen();
            renderApp();
        };
    </script>
</body>
</html>
