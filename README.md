# Vanna-Rithz

<!DOCTYPE html>
<html lang="en" class="h-full bg-[#07090e]">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CYBERNETIC // GitHub Profile Generator 2030</title>
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Google Fonts: Orbitron, Fira Code, & Inter -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500;700&family=Inter:wght@300;400;600;800&family=Orbitron:wght@500;700;900&display=swap" rel="stylesheet">
  <!-- FontAwesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            cyber: {
              black: '#07090e',
              dark: '#0e121b',
              panel: '#131825',
              cyan: '#00f0ff',
              neon: '#00ff66',
              purple: '#b026ff',
              magenta: '#ff0055',
              yellow: '#ffe600',
              border: '#1f2a3e'
            }
          },
          fontFamily: {
            orbitron: ['Orbitron', 'sans-serif'],
            mono: ['Fira Code', 'monospace'],
            sans: ['Inter', 'sans-serif']
          },
          animation: {
            'pulse-glow': 'pulseGlow 2s infinite alternate',
            'grid-move': 'gridMove 20s linear infinite',
            'glitch': 'glitch 1s infinite'
          },
          keyframes: {
            pulseGlow: {
              '0%': { boxShadow: '0 0 5px rgba(0,240,255,0.3), inset 0 0 5px rgba(0,240,255,0.2)' },
              '100%': { boxShadow: '0 0 20px rgba(0,240,255,0.8), inset 0 0 15px rgba(0,240,255,0.5)' }
            },
            gridMove: {
              '0%': { transform: 'translateY(0)' },
              '100%': { transform: 'translateY(40px)' }
            }
          }
        }
      }
    }
  </script>
  <style>
    /* Custom Sci-Fi Aesthetics & Scanlines */
    .bg-grid-pattern {
      background-size: 40px 40px;
      background-image: 
        linear-gradient(to right, rgba(0, 240, 255, 0.05) 1px, transparent 1px),
        linear-gradient(to bottom, rgba(0, 240, 255, 0.05) 1px, transparent 1px);
    }
    
    .scanlines {
      background: linear-gradient(
        to bottom,
        rgba(255,255,255,0),
        rgba(255,255,255,0) 50%,
        rgba(0, 0, 0, 0.3) 50%,
        rgba(0, 0, 0, 0.3)
      );
      background-size: 100% 4px;
    }

    .glass-panel {
      background: rgba(14, 18, 27, 0.75);
      backdrop-filter: blur(12px);
      border: 1px solid rgba(0, 240, 255, 0.2);
    }

    .cyber-glow-cyan {
      box-shadow: 0 0 15px rgba(0, 240, 255, 0.3);
    }

    .cyber-glow-magenta {
      box-shadow: 0 0 15px rgba(255, 0, 85, 0.3);
    }

    /* Clip Path Hexagons & Cyber Cut Corners */
    .clip-corner-br {
      clip-path: polygon(0 0, 100% 0, 100% calc(100% - 15px), calc(100% - 15px) 100%, 0 100%);
    }

    .clip-corner-tl {
      clip-path: polygon(15px 0, 100% 0, 100% 100%, 0 100%, 0 15px);
    }

    /* Custom Scrollbar */
    ::-webkit-scrollbar {
      width: 6px;
      height: 6px;
    }
    ::-webkit-scrollbar-track {
      background: #07090e;
    }
    ::-webkit-scrollbar-thumb {
      background: #1f2a3e;
      border-radius: 3px;
      border: 1px solid #00f0ff;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: #00f0ff;
    }
  </style>
</head>
<body class="h-full text-slate-200 font-sans bg-cyber-black overflow-x-hidden relative">

  <!-- Background Animated Sci-Fi Canvas & Grid -->
  <div class="fixed inset-0 bg-grid-pattern pointer-events-none z-0"></div>
  <canvas id="particleCanvas" class="fixed inset-0 pointer-events-none z-0 opacity-40"></canvas>
  <div class="fixed inset-0 scanlines pointer-events-none z-50 opacity-25"></div>

  <!-- Main Container -->
  <div class="relative z-10 flex flex-col h-screen">

    <!-- Top Navigation / System Header -->
    <header class="border-b border-cyber-border bg-cyber-dark/80 backdrop-blur px-6 py-3 flex items-center justify-between">
      <div class="flex items-center gap-3">
        <div class="w-8 h-8 rounded bg-cyber-cyan/10 border border-cyber-cyan flex items-center justify-center text-cyber-cyan font-orbitron font-bold">
          <i class="fa-solid fa-microchip"></i>
        </div>
        <div>
          <h1 class="font-orbitron text-lg font-bold tracking-wider text-white flex items-center gap-2">
            CYBERNETIC // <span class="text-cyber-cyan">README 2030</span>
            <span class="text-[10px] px-2 py-0.5 rounded bg-cyber-cyan/10 text-cyber-cyan border border-cyber-cyan/30">v3.0.8</span>
          </h1>
          <p class="text-xs text-slate-400 font-mono">SYSTEM_STATUS: ONLINE // NEURAL_LINK: ACTIVE</p>
        </div>
      </div>

      <!-- Action Toggle Buttons -->
      <div class="flex items-center gap-3">
        <button id="toggleCodeBtn" onclick="toggleViewMode('code')" class="px-4 py-2 text-xs font-mono rounded border border-cyber-border bg-cyber-panel hover:border-cyber-cyan transition-all flex items-center gap-2">
          <i class="fa-solid fa-code text-cyber-cyan"></i> RAW_MARKDOWN
        </button>
        <button id="togglePreviewBtn" onclick="toggleViewMode('preview')" class="px-4 py-2 text-xs font-mono rounded border border-cyber-cyan bg-cyber-cyan/10 text-cyber-cyan hover:bg-cyber-cyan/20 transition-all flex items-center gap-2">
          <i class="fa-solid fa-eye"></i> LIVE_PREVIEW
        </button>
        <button onclick="copyGeneratedCode()" class="px-4 py-2 text-xs font-mono font-bold rounded bg-gradient-to-r from-cyber-cyan to-cyber-purple text-black hover:opacity-90 transition-all flex items-center gap-2 shadow-lg shadow-cyber-cyan/20">
          <i class="fa-solid fa-copy"></i> COPY_CODE
        </button>
      </div>
    </header>

    <!-- Main Workspace Layout -->
    <div class="flex-1 flex overflow-hidden">
      
      <!-- LEFT SIDEBAR: Live Matrix Controller (Editor Controls) -->
      <aside class="w-full md:w-96 border-r border-cyber-border bg-cyber-dark/90 flex flex-col h-full overflow-y-auto p-5 gap-6 clip-corner-br">
        
        <div>
          <h2 class="font-orbitron text-sm font-bold text-cyber-cyan tracking-wider uppercase mb-1 flex items-center gap-2">
            <i class="fa-solid fa-sliders"></i> NEURAL PARAMETERS
          </h2>
          <p class="text-xs text-slate-400">Configure your 2030 Identity Matrix.</p>
        </div>

        <!-- Section: Primary Identity -->
        <div class="space-y-4">
          <label class="block text-xs font-mono text-slate-300 uppercase">Core Identity</label>
          
          <div>
            <span class="text-[11px] text-slate-400 font-mono">SYSTEM USERNAME</span>
            <input type="text" id="inputUsername" value="VANNA_DEV" oninput="updateProfile()" class="w-full mt-1 bg-cyber-panel border border-cyber-border focus:border-cyber-cyan text-sm rounded px-3 py-2 font-mono text-cyan-300 focus:outline-none transition">
          </div>

          <div>
            <span class="text-[11px] text-slate-400 font-mono">PRIMARY TITLE</span>
            <input type="text" id="inputTitle" value="FULL-STACK CYBERNETIC ENGINEER" oninput="updateProfile()" class="w-full mt-1 bg-cyber-panel border border-cyber-border focus:border-cyber-cyan text-sm rounded px-3 py-2 font-mono text-cyan-300 focus:outline-none transition">
          </div>

          <div>
            <span class="text-[11px] text-slate-400 font-mono">CURRENT LOCATION / REALM</span>
            <input type="text" id="inputLocation" value="NEO-TOKYO // NODE_09" oninput="updateProfile()" class="w-full mt-1 bg-cyber-panel border border-cyber-border focus:border-cyber-cyan text-sm rounded px-3 py-2 font-mono text-cyan-300 focus:outline-none transition">
          </div>
        </div>

        <hr class="border-cyber-border">

        <!-- Section: Terminal Logs (About Me) -->
        <div class="space-y-3">
          <label class="block text-xs font-mono text-slate-300 uppercase">Terminal Protocol ("About Me")</label>

          <div>
            <span class="text-[11px] text-slate-400 font-mono">🔭 Currently Building</span>
            <input type="text" id="inputBuilding" value="Autonomous AI Web Services & Neural API Mesh" oninput="updateProfile()" class="w-full mt-1 bg-cyber-panel border border-cyber-border focus:border-cyber-cyan text-xs rounded px-3 py-2 font-mono text-slate-200 focus:outline-none transition">
          </div>

          <div>
            <span class="text-[11px] text-slate-400 font-mono">👯 Looking to Collaborate</span>
            <input type="text" id="inputCollab" value="Quantum-Resistant Open-Source Protocols" oninput="updateProfile()" class="w-full mt-1 bg-cyber-panel border border-cyber-border focus:border-cyber-cyan text-xs rounded px-3 py-2 font-mono text-slate-200 focus:outline-none transition">
          </div>

          <div>
            <span class="text-[11px] text-slate-400 font-mono">🤝 Seeking Synergy With</span>
            <input type="text" id="inputHelp" value="Distributed MySQL & C++ Low-Latency Systems" oninput="updateProfile()" class="w-full mt-1 bg-cyber-panel border border-cyber-border focus:border-cyber-cyan text-xs rounded px-3 py-2 font-mono text-slate-200 focus:outline-none transition">
          </div>

          <div>
            <span class="text-[11px] text-slate-400 font-mono">🌱 Learning Protocol</span>
            <input type="text" id="inputLearning" value="Bio-Algorithmic Neural Networks in Python" oninput="updateProfile()" class="w-full mt-1 bg-cyber-panel border border-cyber-border focus:border-cyber-cyan text-xs rounded px-3 py-2 font-mono text-slate-200 focus:outline-none transition">
          </div>

          <div>
            <span class="text-[11px] text-slate-400 font-mono">💬 Inquiry Matrix</span>
            <input type="text" id="inputAsk" value="Full-Stack (PHP/JS/C#/Java) & Cyber Security" oninput="updateProfile()" class="w-full mt-1 bg-cyber-panel border border-cyber-border focus:border-cyber-cyan text-xs rounded px-3 py-2 font-mono text-slate-200 focus:outline-none transition">
          </div>

          <div>
            <span class="text-[11px] text-slate-400 font-mono">⚡ Fun Fact 2030</span>
            <input type="text" id="inputFunFact" value="In 2030, debugging is just asking the compiler why it has an attitude." oninput="updateProfile()" class="w-full mt-1 bg-cyber-panel border border-cyber-border focus:border-cyber-cyan text-xs rounded px-3 py-2 font-mono text-slate-200 focus:outline-none transition">
          </div>
        </div>

        <hr class="border-cyber-border">

        <!-- Tech Stack Selector -->
        <div>
          <label class="block text-xs font-mono text-slate-300 uppercase mb-3">Tech Matrix Selection</label>
          <div id="techStackCheckboxes" class="grid grid-cols-2 gap-2 text-xs font-mono">
            <!-- Dynamically populated checkboxes -->
          </div>
        </div>

        <div class="pt-4 mt-auto">
          <div class="p-3 rounded bg-cyber-cyan/5 border border-cyber-cyan/20 text-center">
            <p class="text-[11px] text-cyber-cyan font-mono"><i class="fa-solid fa-bolt mr-1"></i> Changes auto-render in real time</p>
          </div>
        </div>

      </aside>

      <!-- RIGHT PANEL: Live Interactive Preview & Markdown Exporter -->
      <main class="flex-1 flex flex-col h-full bg-cyber-black relative overflow-hidden">
        
        <!-- Tab Bar -->
        <div class="bg-cyber-panel/60 border-b border-cyber-border px-6 py-2 flex justify-between items-center text-xs font-mono">
          <div class="flex gap-4">
            <span class="text-cyber-cyan flex items-center gap-1.5"><i class="fa-solid fa-terminal"></i> PROFILE_RENDERER.exe</span>
            <span class="text-slate-500">|</span>
            <span class="text-slate-400">MODE: <span id="currentModeLabel" class="text-cyber-neon">VISUAL PREVIEW</span></span>
          </div>
          <div class="text-slate-500 text-[11px]">TARGET: README.md (GITHUB_2030_STD)</div>
        </div>

        <!-- Render Window -->
        <div class="flex-1 overflow-y-auto p-4 md:p-8 space-y-6">
          
          <!-- VISUAL PREVIEW CONTAINER -->
          <div id="visualPreviewContainer" class="max-w-4xl mx-auto glass-panel rounded-xl p-6 md:p-8 border border-cyber-cyan/30 shadow-2xl relative clip-corner-tl">
            
            <!-- Cyber Graphic Top Accents -->
            <div class="absolute top-0 left-12 right-12 h-[2px] bg-gradient-to-r from-transparent via-cyber-cyan to-transparent"></div>
            <div class="absolute top-2 right-4 text-[10px] font-mono text-cyber-cyan/60 tracking-widest uppercase">ID: 0x99A_2030</div>

            <!-- Banner Header -->
            <div class="relative overflow-hidden rounded-lg bg-gradient-to-r from-cyber-dark via-cyber-panel to-cyber-dark border border-cyber-cyan/40 p-6 md:p-8 mb-8 text-center shadow-lg">
              <div class="absolute -top-10 -left-10 w-32 h-32 bg-cyber-cyan/10 rounded-full blur-2xl"></div>
              <div class="absolute -bottom-10 -right-10 w-32 h-32 bg-cyber-purple/20 rounded-full blur-2xl"></div>
              
              <!-- Status Badge -->
              <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-cyber-neon/10 border border-cyber-neon/40 text-cyber-neon text-xs font-mono mb-4">
                <span class="w-2 h-2 rounded-full bg-cyber-neon animate-ping"></span>
                <span>SYSTEM ONLINE // 2030 NEURAL ENGINE ACTIVE</span>
              </div>

              <!-- Main Name Title -->
              <h1 id="previewName" class="font-orbitron text-2xl md:text-4xl font-black tracking-widest text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 via-teal-200 to-purple-400 mb-2">
                VANNA // SYSTEM_DEVELOPER
              </h1>
              <p id="previewTitle" class="font-mono text-sm md:text-base text-cyber-cyan tracking-wider uppercase mb-4">
                FULL-STACK CYBERNETIC ENGINEER
              </p>
              
              <div class="flex flex-wrap justify-center gap-4 text-xs font-mono text-slate-400">
                <span class="flex items-center gap-1.5"><i class="fa-solid fa-location-dot text-cyber-magenta"></i> <span id="previewLocation">NEO-TOKYO // NODE_09</span></span>
                <span>•</span>
                <span class="flex items-center gap-1.5"><i class="fa-solid fa-network-wired text-cyber-cyan"></i> MESH: ACTIVE</span>
                <span>•</span>
                <span class="flex items-center gap-1.5"><i class="fa-solid fa-shield-halved text-cyber-neon"></i> QUANTUM-ENCRYPTED</span>
              </div>
            </div>

            <!-- Terminal / About Me Section -->
            <div class="mb-8 rounded-lg bg-cyber-black/80 border border-cyber-cyan/30 p-5 font-mono text-xs leading-relaxed shadow-inner">
              <div class="flex items-center justify-between border-b border-cyber-border/80 pb-2 mb-4 text-slate-400">
                <div class="flex items-center gap-2">
                  <span class="w-3 h-3 rounded-full bg-red-500/80 inline-block"></span>
                  <span class="w-3 h-3 rounded-full bg-yellow-500/80 inline-block"></span>
                  <span class="w-3 h-3 rounded-full bg-green-500/80 inline-block"></span>
                  <span class="ml-2 text-[11px] text-cyber-cyan">~/bio_kernel_2030.sh</span>
                </div>
                <span class="text-[10px] text-slate-500">UTF-8 // BASH</span>
              </div>

              <div class="space-y-3">
                <div class="flex items-start gap-2">
                  <span class="text-cyber-cyan">🔭</span>
                  <span class="text-slate-400 font-bold min-w-[150px]">Currently Building:</span>
                  <span id="previewBuilding" class="text-cyan-200"></span>
                </div>
                <div class="flex items-start gap-2">
                  <span class="text-cyber-purple">👯</span>
                  <span class="text-slate-400 font-bold min-w-[150px]">Collaborating On:</span>
                  <span id="previewCollab" class="text-purple-200"></span>
                </div>
                <div class="flex items-start gap-2">
                  <span class="text-cyber-magenta">🤝</span>
                  <span class="text-slate-400 font-bold min-w-[150px]">Seeking Help With:</span>
                  <span id="previewHelp" class="text-pink-200"></span>
                </div>
                <div class="flex items-start gap-2">
                  <span class="text-cyber-neon">🌱</span>
                  <span class="text-slate-400 font-bold min-w-[150px]">Learning Protocol:</span>
                  <span id="previewLearning" class="text-emerald-200"></span>
                </div>
                <div class="flex items-start gap-2">
                  <span class="text-cyber-yellow">💬</span>
                  <span class="text-slate-400 font-bold min-w-[150px]">Ask Me About:</span>
                  <span id="previewAsk" class="text-yellow-100"></span>
                </div>
                <div class="flex items-start gap-2 pt-2 border-t border-cyber-border/40">
                  <span class="text-red-400">⚡</span>
                  <span class="text-slate-400 font-bold min-w-[150px]">Fun Fact (2030):</span>
                  <span id="previewFunFact" class="text-slate-300 italic"></span>
                </div>
              </div>
            </div>

            <!-- Tech Stack Matrix Display -->
            <div class="mb-8">
              <h2 class="font-orbitron text-sm font-bold text-cyber-cyan mb-4 flex items-center gap-2 uppercase tracking-widest">
                <i class="fa-solid fa-layer-group"></i> TECH_STACK_MATRIX_2030
              </h2>
              <div id="previewTechGrid" class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-3">
                <!-- Tech Stack Badges dynamically generated -->
              </div>
            </div>

            <!-- Futuristic Stats Widgets (Cyberpunk Style Simulation) -->
            <div class="mb-8 grid grid-cols-1 md:grid-cols-2 gap-4">
              <!-- Matrix Commit Activity -->
              <div class="bg-cyber-dark/80 border border-cyber-border p-4 rounded-lg">
                <div class="flex justify-between items-center mb-3">
                  <span class="font-mono text-xs text-cyber-cyan font-bold"><i class="fa-solid fa-chart-line mr-1"></i> NEURAL STREAK SCORE</span>
                  <span class="text-[10px] font-mono text-cyber-neon">99.8% ACCURACY</span>
                </div>
                <div class="space-y-2">
                  <div class="flex justify-between text-[11px] font-mono text-slate-400">
                    <span>Commit Neural Pulse</span>
                    <span class="text-white">1,420 Commits/yr</span>
                  </div>
                  <div class="w-full bg-cyber-panel h-2 rounded-full overflow-hidden border border-cyber-border">
                    <div class="bg-gradient-to-r from-cyber-cyan via-cyber-purple to-cyber-magenta h-full w-[88%] animate-pulse"></div>
                  </div>
                  <div class="flex justify-between text-[10px] font-mono text-slate-500 pt-1">
                    <span>Current Streak: 342 Days</span>
                    <span>Max Rank: S+ GRANDMASTER</span>
                  </div>
                </div>
              </div>

              <!-- Language Distribution -->
              <div class="bg-cyber-dark/80 border border-cyber-border p-4 rounded-lg">
                <div class="flex justify-between items-center mb-3">
                  <span class="font-mono text-xs text-cyber-purple font-bold"><i class="fa-solid fa-code-branch mr-1"></i> CORE SYNTAX RATIO</span>
                  <span class="text-[10px] font-mono text-slate-400">2030 TELEMETRY</span>
                </div>
                <div class="flex h-3 rounded-full overflow-hidden border border-cyber-border mb-3">
                  <div style="width: 25%" class="bg-yellow-400" title="JS/HTML/CSS"></div>
                  <div style="width: 20%" class="bg-blue-500" title="C++/C#"></div>
                  <div style="width: 20%" class="bg-green-500" title="Python"></div>
                  <div style="width: 15%" class="bg-purple-500" title="PHP"></div>
                  <div style="width: 10%" class="bg-red-500" title="Java"></div>
                  <div style="width: 10%" class="bg-cyan-500" title="MySQL"></div>
                </div>
                <div class="grid grid-cols-3 gap-1 text-[10px] font-mono text-slate-400">
                  <span class="flex items-center gap-1"><span class="w-2 h-2 rounded-full bg-yellow-400"></span> Web (JS/HTML/CSS)</span>
                  <span class="flex items-center gap-1"><span class="w-2 h-2 rounded-full bg-blue-500"></span> C++/C#</span>
                  <span class="flex items-center gap-1"><span class="w-2 h-2 rounded-full bg-green-500"></span> Python</span>
                  <span class="flex items-center gap-1"><span class="w-2 h-2 rounded-full bg-purple-500"></span> PHP</span>
                  <span class="flex items-center gap-1"><span class="w-2 h-2 rounded-full bg-red-500"></span> Java</span>
                  <span class="flex items-center gap-1"><span class="w-2 h-2 rounded-full bg-cyan-500"></span> MySQL</span>
                </div>
              </div>
            </div>

            <!-- Sci-Fi Footer Badge -->
            <div class="text-center pt-4 border-t border-cyber-border/50">
              <p class="font-mono text-xs text-slate-500 flex items-center justify-center gap-2">
                <span>⚡ GENERATED VIA CYBERNETIC PROFILE PROTOCOL 2030</span>
                <span>•</span>
                <span class="text-cyber-cyan">OPEN SOURCE</span>
              </p>
            </div>

          </div>

          <!-- RAW CODE CONTAINER (Hidden by default) -->
          <div id="rawCodeContainer" class="max-w-4xl mx-auto glass-panel rounded-xl p-6 hidden">
            <div class="flex justify-between items-center mb-4">
              <span class="font-mono text-xs text-cyber-cyan"><i class="fa-solid fa-file-code mr-1"></i> MARKDOWN / HTML COMPATIBLE SOURCE CODE:</span>
              <button onclick="copyGeneratedCode()" class="text-xs font-mono text-cyber-neon hover:underline">
                <i class="fa-solid fa-copy"></i> Copy to Clipboard
              </button>
            </div>
            <textarea id="markdownOutput" readonly class="w-full h-[600px] bg-cyber-black border border-cyber-border rounded-lg p-4 font-mono text-xs text-emerald-400 focus:outline-none resize-none"></textarea>
          </div>

        </div>
      </main>

    </div>
  </div>

  <!-- Notification Toast -->
  <div id="toast" class="fixed bottom-6 right-6 px-4 py-3 rounded-lg bg-cyber-dark border border-cyber-cyan text-cyber-cyan font-mono text-xs shadow-xl transform translate-y-20 opacity-0 transition-all duration-300 pointer-events-none flex items-center gap-2">
    <i class="fa-solid fa-circle-check text-cyber-neon"></i>
    <span id="toastMsg">Code copied to clipboard!</span>
  </div>

  <!-- Logic Script -->
  <script>
    // Complete Technology Dataset with 2030 Futuristic Descriptions & Styling
    const TECH_STACK = [
      { id: 'html', name: 'HTML5 / Web Components', icon: 'fa-brands fa-html5', color: '#e34c26', badgeBg: 'from-orange-950 to-red-900' },
      { id: 'css', name: 'CSS3 / Cyber Styling', icon: 'fa-brands fa-css3-alt', color: '#264de4', badgeBg: 'from-blue-950 to-indigo-900' },
      { id: 'js', name: 'JavaScript ES2030', icon: 'fa-brands fa-square-js', color: '#f7df1e', badgeBg: 'from-yellow-950 to-amber-900' },
      { id: 'php', name: 'PHP 8.x / Modern Backends', icon: 'fa-brands fa-php', color: '#777bb4', badgeBg: 'from-indigo-950 to-purple-900' },
      { id: 'cpp', name: 'C++ Systems Architecture', icon: 'fa-solid fa-code', color: '#00599c', badgeBg: 'from-blue-950 to-cyan-950' },
      { id: 'csharp', name: 'C# / .NET Enterprise Mesh', icon: 'fa-solid fa-cubes', color: '#239120', badgeBg: 'from-green-950 to-emerald-900' },
      { id: 'java', name: 'Java Virtual Machine Protocols', icon: 'fa-brands fa-java', color: '#5382a1', badgeBg: 'from-sky-950 to-blue-950' },
      { id: 'mysql', name: 'MySQL Relational Data Core', icon: 'fa-solid fa-database', color: '#00758f', badgeBg: 'from-cyan-950 to-teal-950' },
      { id: 'python', name: 'Python AI & Quantum Scripting', icon: 'fa-brands fa-python', color: '#3776ab', badgeBg: 'from-slate-900 to-blue-950' }
    ];

    // Selected tech state (All enabled by default)
    let selectedTech = TECH_STACK.map(t => t.id);

    // Initialize UI on load
    window.onload = function() {
      initTechCheckboxes();
      updateProfile();
      initParticles();
    };

    // Render technology checkboxes in controller panel
    function initTechCheckboxes() {
      const container = document.getElementById('techStackCheckboxes');
      container.innerHTML = TECH_STACK.map(tech => `
        <label class="flex items-center gap-2 p-2 rounded bg-cyber-panel border border-cyber-border hover:border-cyber-cyan cursor-pointer transition">
          <input type="checkbox" value="${tech.id}" checked onchange="toggleTech('${tech.id}')" class="accent-cyber-cyan">
          <span class="truncate text-slate-300"><i class="${tech.icon} mr-1" style="color:${tech.color}"></i> ${tech.name.split(' ')[0]}</span>
        </label>
      `).join('');
    }

    function toggleTech(id) {
      if (selectedTech.includes(id)) {
        selectedTech = selectedTech.filter(item => item !== id);
      } else {
        selectedTech.push(id);
      }
      updateProfile();
    }

    // Main Update Loop - Syncs input values to Live Preview & Raw Code
    function updateProfile() {
      const name = document.getElementById('inputUsername').value || 'VANNA_DEV';
      const title = document.getElementById('inputTitle').value || 'FULL-STACK CYBERNETIC ENGINEER';
      const location = document.getElementById('inputLocation').value || 'NEO-TOKYO';
      const building = document.getElementById('inputBuilding').value || 'Neural APIs';
      const collab = document.getElementById('inputCollab').value || 'AI Protocols';
      const help = document.getElementById('inputHelp').value || 'C++ Algorithms';
      const learning = document.getElementById('inputLearning').value || 'Quantum Computing';
      const ask = document.getElementById('inputAsk').value || 'Full Stack Architecture';
      const funFact = document.getElementById('inputFunFact').value || 'Code compiles faster with synthwave.';

      // Update Live Preview UI Elements
      document.getElementById('previewName').innerText = name;
      document.getElementById('previewTitle').innerText = title;
      document.getElementById('previewLocation').innerText = location;
      document.getElementById('previewBuilding').innerText = building;
      document.getElementById('previewCollab').innerText = collab;
      document.getElementById('previewHelp').innerText = help;
      document.getElementById('previewLearning').innerText = learning;
      document.getElementById('previewAsk').innerText = ask;
      document.getElementById('previewFunFact').innerText = funFact;

      // Update Preview Tech Grid
      const techGrid = document.getElementById('previewTechGrid');
      techGrid.innerHTML = TECH_STACK.filter(t => selectedTech.includes(t.id)).map(tech => `
        <div class="p-3 rounded-lg bg-gradient-to-br ${tech.badgeBg} border border-cyber-cyan/30 flex items-center gap-3 shadow-md hover:border-cyber-cyan transition-all transform hover:-translate-y-0.5">
          <i class="${tech.icon} text-lg" style="color: ${tech.color}"></i>
          <div>
            <div class="font-mono text-xs font-bold text-white">${tech.name.split(' ')[0]}</div>
            <div class="font-mono text-[9px] text-slate-400">READY // 2030</div>
          </div>
        </div>
      `).join('');

      // Generate Raw Markdown Output
      generateMarkdown({ name, title, location, building, collab, help, learning, ask, funFact });
    }

    // Generate Markdown/HTML code for GitHub profile README
    function generateMarkdown(data) {
      const techBadgesMarkdown = TECH_STACK.filter(t => selectedTech.includes(t.id)).map(t => {
        return `<img src="https://img.shields.io/badge/${encodeURIComponent(t.name.split(' ')[0])}-00f0ff?style=for-the-badge&logo=${t.id === 'cpp' ? 'cplusplus' : t.id === 'csharp' ? 'csharp' : t.id}&logoColor=black" alt="${t.name}">`;
      }).join(' ');

      const markdown = `<div align="center">

# ⚡ ${data.name} ⚡
### **${data.title}**

\`LOCATION: ${data.location}\` • \`STATUS: NEURAL LINK ACTIVE\` • \`YEAR: 2030\`

---

<!-- CYBERPUNK 2030 HUD BANNER -->
<img src="https://readme-typing-svg.demolab.com?font=Orbitron&weight=700&size=22&duration=3000&pause=1000&color=00F0FF&center=true&vCenter=true&width=600&height=50&lines=${encodeURIComponent(data.name)};${encodeURIComponent(data.title)};SYSTEM_STATUS_ONLINE_2030" alt="Cyberpunk Typing Title" />

---

</div>

### 🧬 TERMINAL_LOGS // ABOUT ME

\`\`\`bash
# Initialize Cybernetic Core Protocol v3.0
$ systemctl status developer --identity="${data.name}"

  🔭 CURRENTLY_BUILDING  : "${data.building}"
  👯 LOOKING_TO_COLLAB   : "${data.collab}"
  🤝 SEEKING_SYNERGY     : "${data.help}"
  🌱 CURRENTLY_LEARNING  : "${data.learning}"
  💬 INQUIRY_MATRIX      : "${data.ask}"
  ⚡ FUN_FACT_2030       : "${data.funFact}"
\`\`\`

---

### 🛡️ TECH_STACK_MATRIX (2030 REVISION)

<div align="center">

${techBadgesMarkdown}

</div>

---

### 📊 CYBERNETIC METRICS & STREAK MATRIX

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=${data.name.toLowerCase().replace(/[^a-z0-9]/g, '')}&show_icons=true&theme=cyberpunk&hide_border=false" alt="GitHub Stats" width="48%" />
<img src="https://github-readme-streak-stats.herokuapp.com/?user=${data.name.toLowerCase().replace(/[^a-z0-9]/g, '')}&theme=cyberpunk&hide_border=false" alt="GitHub Streak" width="48%" />

</div>

---

<div align="center">
  <sub>⚡ Generated with 2030 Cybernetic README Protocol | Built for High-Performance Developers</sub>
</div>
`;

      document.getElementById('markdownOutput').value = markdown;
    }

    // Toggle between Live Preview and Raw Code modes
    function toggleViewMode(mode) {
      const preview = document.getElementById('visualPreviewContainer');
      const rawCode = document.getElementById('rawCodeContainer');
      const label = document.getElementById('currentModeLabel');

      if (mode === 'code') {
        preview.classList.add('hidden');
        rawCode.classList.remove('hidden');
        label.innerText = 'RAW MARKDOWN SOURCE';
        label.className = 'text-cyber-magenta';
      } else {
        preview.classList.remove('hidden');
        rawCode.classList.add('hidden');
        label.innerText = 'VISUAL PREVIEW';
        label.className = 'text-cyber-neon';
      }
    }

    // Copy Raw Code to Clipboard
    function copyGeneratedCode() {
      const codeTextarea = document.getElementById('markdownOutput');
      codeTextarea.select();
      document.execCommand('copy');
      
      showToast('Markdown code copied to clipboard!');
    }

    function showToast(msg) {
      const toast = document.getElementById('toast');
      document.getElementById('toastMsg').innerText = msg;
      toast.classList.remove('translate-y-20', 'opacity-0');
      
      setTimeout(() => {
        toast.classList.add('translate-y-20', 'opacity-0');
      }, 3000);
    }

    // Canvas Sci-Fi Particle System
    function initParticles() {
      const canvas = document.getElementById('particleCanvas');
      const ctx = canvas.getContext('2d');
      
      function resize() {
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
      }
      resize();
      window.addEventListener('resize', resize);

      const particles = [];
      const particleCount = 40;

      for (let i = 0; i < particleCount; i++) {
        particles.push({
          x: Math.random() * canvas.width,
          y: Math.random() * canvas.height,
          size: Math.random() * 2 + 0.5,
          speedY: -(Math.random() * 0.8 + 0.2),
          speedX: (Math.random() - 0.5) * 0.4,
          opacity: Math.random() * 0.5 + 0.2,
          color: Math.random() > 0.5 ? '#00f0ff' : '#b026ff'
        });
      }

      function animate() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);

        particles.forEach(p => {
          p.y += p.speedY;
          p.x += p.speedX;

          if (p.y < 0) {
            p.y = canvas.height;
            p.x = Math.random() * canvas.width;
          }

          ctx.fillStyle = p.color;
          ctx.globalAlpha = p.opacity;
          ctx.beginPath();
          ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
          ctx.fill();
        });

        requestAnimationFrame(animate);
      }

      animate();
    }
  </script>
</body>
</html>
