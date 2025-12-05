---
layout: post
title: "DNS"
description: "Submodule 4 of Hints Mini-Quest"
permalink: /digital-famine/microblog/dns/
parent: "AI Usage"
team: "FlaskLovers"
submodule: 2
categories: [CSP, Submodule, Microblogging]
tags: [microblogging, submodule, unzippers]
author: "Adhav Selvan"
date: 2025-12-01
breadcrumb: true
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AP CSP: URL & DNS Explorer</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap');
        body { font-family: 'Inter', sans-serif; }
        .server-box { transition: all 0.5s ease; }
        .packet { transition: all 1s ease-in-out; }
        
        /* Game Animations */
        @keyframes spin-slow {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        .animate-spin-slow {
            animation: spin-slow 3s linear infinite;
        }
        .server-light {
            box-shadow: 0 0 10px #22c55e;
            animation: blink 1s infinite;
        }
        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }
        
        /* Tooltip Arrow */
        .tooltip-arrow::after {
            content: " ";
            position: absolute;
            bottom: 100%;  /* At the top of the tooltip */
            left: 50%;
            margin-left: -5px;
            border-width: 5px;
            border-style: solid;
            border-color: transparent transparent #1e293b transparent;
        }
    </style>
</head>
<body class="bg-slate-900 text-slate-100 min-h-screen flex flex-col">

    <!-- Header -->
    <header class="bg-slate-800 border-b border-slate-700 p-4 shadow-lg sticky top-0 z-50">
        <div class="max-w-5xl mx-auto flex justify-between items-center">
            <h1 class="text-2xl font-bold text-blue-400 flex items-center gap-2">
                <i data-lucide="globe" class="w-6 h-6"></i>
                AP CSP: Big Idea 4
            </h1>
            <div class="text-sm text-slate-400">Topic: URL Anatomy & DNS Hierarchy</div>
        </div>
    </header>

    <main class="flex-grow p-6 max-w-5xl mx-auto w-full space-y-12">

        <!-- LECTURE INTRO -->
        <article class="prose prose-invert max-w-none">
            <h2 class="text-3xl font-light text-white border-b border-slate-700 pb-2">The Address Problem: Abstraction in Action</h2>
            <p class="text-lg text-slate-300 leading-relaxed">
                The internet is fundamentally a system of wires and signals connecting billions of devices. To send data from one device to another, we need a precise address. In the digital world, this is an <strong>IP Address</strong>.
            </p>
            <div class="grid md:grid-cols-2 gap-6 my-6">
                <div class="bg-slate-800 p-4 rounded border border-slate-700">
                    <h4 class="font-bold text-blue-400 mb-2">IPv4 (Old Standard)</h4>
                    <p class="text-sm text-slate-400">Uses 32 bits (e.g., <code>93.184.216.34</code>). This allows for about 4 billion unique addresses, which we have already exhausted.</p>
                </div>
                <div class="bg-slate-800 p-4 rounded border border-slate-700">
                    <h4 class="font-bold text-purple-400 mb-2">IPv6 (New Standard)</h4>
                    <p class="text-sm text-slate-400">Uses 128 bits (e.g., <code>2001:db8:85a3::8a2e:370:7334</code>). This provides 340 undecillion addresses—enough for every grain of sand on Earth to have an IP.</p>
                </div>
            </div>
            <p class="text-lg text-slate-300 leading-relaxed">
                Humans are terrible at memorizing these numbers. Imagine if you had to type <code>172.217.164.174</code> every time you wanted to Google something. 
                To solve this, Computer Scientists created an <strong>Abstraction</strong>. We use human-readable names (URLs), and the system translates them into machine-readable numbers behind the scenes. This layer of abstraction hides the complexity of IP routing from the user.
            </p>
        </article>

        <!-- SECTION 1: ANATOMY OF A URL -->
        <section id="url-anatomy" class="bg-slate-800 rounded-xl p-6 shadow-xl border border-slate-700">
            <h2 class="text-xl font-semibold mb-4 text-emerald-400 flex items-center gap-2">
                <i data-lucide="search" class="w-5 h-5"></i>
                Part 1: Anatomy of a URL
            </h2>
            <p class="mb-6 text-slate-300">
                A URL (Uniform Resource Locator) is just a structured request. Hover over the parts of the URL below to see what they actually do.
            </p>

            <div class="flex flex-wrap justify-center items-center text-2xl md:text-4xl font-mono bg-slate-900 p-8 rounded-lg border border-slate-600 select-none">
                <span class="group relative cursor-help hover:bg-red-900/50 rounded px-1 transition-colors" data-part="protocol">
                    https://
                    <div class="absolute hidden group-hover:block bottom-full mb-2 left-1/2 -translate-x-1/2 w-48 bg-red-600 text-white text-xs p-2 rounded shadow-lg text-center font-sans pointer-events-none z-10">
                        <strong>Protocol</strong><br>The set of rules for communication. 's' stands for Secure.
                    </div>
                </span>
                
                <span class="group relative cursor-help hover:bg-orange-900/50 rounded px-1 transition-colors" data-part="subdomain">
                    www.
                    <div class="absolute hidden group-hover:block bottom-full mb-2 left-1/2 -translate-x-1/2 w-48 bg-orange-600 text-white text-xs p-2 rounded shadow-lg text-center font-sans pointer-events-none z-10">
                        <strong>Subdomain</strong><br>A subset of the main domain. Could be 'docs', 'mail', or 'drive'.
                    </div>
                </span>

                <span class="group relative cursor-help hover:bg-green-900/50 rounded px-1 transition-colors" data-part="domain">
                    example
                    <div class="absolute hidden group-hover:block bottom-full mb-2 left-1/2 -translate-x-1/2 w-48 bg-green-600 text-white text-xs p-2 rounded shadow-lg text-center font-sans pointer-events-none z-10">
                        <strong>Second-Level Domain</strong><br>The specific name of the organization or site.
                    </div>
                </span>

                <span class="group relative cursor-help hover:bg-blue-900/50 rounded px-1 transition-colors" data-part="tld">
                    .com
                    <div class="absolute hidden group-hover:block bottom-full mb-2 left-1/2 -translate-x-1/2 w-48 bg-blue-600 text-white text-xs p-2 rounded shadow-lg text-center font-sans pointer-events-none z-10">
                        <strong>Top-Level Domain (TLD)</strong><br>The highest level of hierarchy. Examples: .org, .edu, .gov.
                    </div>
                </span>

                <span class="group relative cursor-help hover:bg-purple-900/50 rounded px-1 transition-colors" data-part="path">
                    /index.html
                    <div class="absolute hidden group-hover:block bottom-full mb-2 left-1/2 -translate-x-1/2 w-48 bg-purple-600 text-white text-xs p-2 rounded shadow-lg text-center font-sans pointer-events-none z-10">
                        <strong>Path</strong><br>The specific file or resource you are requesting on the server.
                    </div>
                </span>
            </div>
            <div class="mt-4 text-center text-sm text-slate-500">
                (Interactive: Hover over the colored segments)
            </div>
        </section>

        <!-- LECTURE BRIDGE 1 -->
        <article class="prose prose-invert max-w-none">
            <h2 class="text-3xl font-light text-white border-b border-slate-700 pb-2">How DNS Works: The Hierarchy of Trust</h2>
            <div class="bg-blue-900/20 border-l-4 border-blue-500 p-4 my-4">
                <p class="font-bold text-blue-200 m-0">Definition: Domain Name System (DNS)</p>
                <p class="text-blue-100 m-0 text-sm">The decentralized, hierarchical service that translates URLs to IP addresses.</p>
            </div>
            <p class="text-lg text-slate-300 leading-relaxed">
                When you type a URL, your computer (the client) initiates a "DNS Query." Crucially, <strong>no single server knows every address on the internet</strong>. Storing billions of records on one machine would create a massive bottleneck and a single point of failure.
            </p>
            <p class="text-lg text-slate-300 leading-relaxed">
                Instead, the system is designed to be <strong>Hierarchical and Distributed</strong>. It functions like a massive, global decision tree:
            </p>
            <ul class="list-none pl-0 text-slate-300 space-y-4 my-6">
                <li class="flex items-start gap-3">
                    <span class="bg-red-900/50 text-red-200 px-2 py-1 rounded text-sm font-mono border border-red-500 shrink-0">1. Root</span>
                    <span>The <strong>Root Servers</strong> sit at the top. They don't know where <code>nike.com</code> is, but they know exactly which server manages all <code>.com</code> addresses.</span>
                </li>
                <li class="flex items-start gap-3">
                    <span class="bg-blue-900/50 text-blue-200 px-2 py-1 rounded text-sm font-mono border border-blue-500 shrink-0">2. TLD</span>
                    <span>The <strong>Top-Level Domain (TLD) Servers</strong> manage specific extensions like .com, .org, or .gov. The .com server knows who owns the specific domain "nike," but not the specific page IPs.</span>
                </li>
                <li class="flex items-start gap-3">
                    <span class="bg-green-900/50 text-green-200 px-2 py-1 rounded text-sm font-mono border border-green-500 shrink-0">3. Auth</span>
                    <span>The <strong>Authoritative Name Server</strong> is the final stop. It is usually maintained by the domain owner (or their hosting provider) and holds the actual "A Record"—the precise IP address you need.</span>
                </li>
            </ul>
        </article>

        <!-- SECTION 2: THE DNS LOOKUP SIMULATION -->
        <section id="dns-sim" class="bg-slate-800 rounded-xl p-6 shadow-xl border border-slate-700 relative overflow-hidden">
            <h2 class="text-xl font-semibold mb-2 text-blue-400 flex items-center gap-2">
                <i data-lucide="network" class="w-5 h-5"></i>
                Part 2: The DNS Lookup Journey
            </h2>
            <p class="mb-6 text-slate-300">
                Watch the "Packet" travel through the hierarchy to find the IP address for <code>store.nike.com</code>.
            </p>

            <div class="flex flex-col md:flex-row gap-4 items-center mb-8">
                <input type="text" value="store.nike.com" disabled class="bg-slate-900 border border-slate-600 px-4 py-2 rounded text-slate-400 w-full md:w-auto font-mono">
                <button onclick="startSimulation()" id="sim-btn" class="bg-blue-600 hover:bg-blue-500 text-white px-6 py-2 rounded font-bold transition-colors w-full md:w-auto flex items-center justify-center gap-2">
                    <i data-lucide="play" class="w-4 h-4"></i> Start DNS Lookup
                </button>
                <button onclick="resetSimulation()" class="bg-slate-700 hover:bg-slate-600 text-white px-4 py-2 rounded font-bold transition-colors w-full md:w-auto">
                    Reset
                </button>
            </div>

            <!-- Visualization Stage -->
            <div class="relative bg-slate-900 rounded-lg p-4 h-[450px] md:h-[300px] border border-slate-700 w-full">
                
                <!-- Status Bar -->
                <div id="status-bar" class="absolute top-2 left-2 right-2 bg-slate-800/80 p-2 rounded text-center text-sm font-mono text-yellow-400 h-16 flex items-center justify-center border border-slate-600 z-20">
                    Ready to resolve hostname...
                </div>

                <!-- Computer (User) -->
                <div class="absolute bottom-4 left-4 md:top-1/2 md:-translate-y-1/2 md:left-4 z-10 flex flex-col items-center">
                    <div class="w-16 h-16 bg-slate-700 rounded-full flex items-center justify-center border-2 border-slate-500 server-box" id="node-user">
                        <i data-lucide="laptop" class="w-8 h-8"></i>
                    </div>
                    <span class="text-xs mt-2 font-bold">You</span>
                </div>

                <!-- Recursive Resolver (ISP) -->
                <div class="absolute bottom-24 left-1/2 -translate-x-1/2 md:top-1/2 md:-translate-y-1/2 md:left-[25%] z-10 flex flex-col items-center">
                    <div class="w-16 h-16 bg-indigo-900 rounded-lg flex items-center justify-center border-2 border-indigo-500 server-box opacity-50" id="node-resolver">
                        <i data-lucide="server" class="w-8 h-8 text-indigo-300"></i>
                    </div>
                    <span class="text-xs mt-2 font-bold text-center">ISP Resolver<br>(The Librarian)</span>
                </div>

                <!-- Hierarchy Column -->
                <div class="absolute top-4 right-4 md:right-10 md:top-8 flex flex-col gap-6 items-end">
                    
                    <!-- Root Server -->
                    <div class="flex items-center gap-2">
                        <span class="text-xs text-slate-400 text-right w-32 hidden md:block">Root Server<br>(Knows who handles .com)</span>
                        <div class="w-12 h-12 bg-red-900 rounded flex items-center justify-center border-2 border-red-500 server-box opacity-50" id="node-root">
                            <span class="font-bold text-red-200">.</span>
                        </div>
                    </div>

                    <!-- TLD Server -->
                    <div class="flex items-center gap-2">
                        <span class="text-xs text-slate-400 text-right w-32 hidden md:block">TLD Server<br>(Knows who handles nike)</span>
                        <div class="w-12 h-12 bg-blue-900 rounded flex items-center justify-center border-2 border-blue-500 server-box opacity-50" id="node-tld">
                            <span class="font-bold text-blue-200">.com</span>
                        </div>
                    </div>

                    <!-- Authoritative Server -->
                    <div class="flex items-center gap-2">
                        <span class="text-xs text-slate-400 text-right w-32 hidden md:block">Authoritative Server<br>(Knows the actual IP)</span>
                        <div class="w-12 h-12 bg-green-900 rounded flex items-center justify-center border-2 border-green-500 server-box opacity-50" id="node-auth">
                            <span class="font-bold text-green-200">nike</span>
                        </div>
                    </div>

                </div>

                <!-- Packet (Animated Dot) -->
                <div id="packet" class="absolute w-4 h-4 bg-yellow-400 rounded-full shadow-[0_0_10px_rgba(250,204,21,0.8)] hidden z-50"></div>

            </div>
            
            <div class="mt-4 p-4 bg-slate-700/50 rounded border-l-4 border-yellow-500">
                <h3 class="font-bold text-yellow-400 text-sm uppercase">Key Concept: Scalability</h3>
                <p class="text-sm text-slate-300 mt-1">
                    Because DNS is split into layers (Root -> TLD -> Authoritative), we can add millions of new .com websites without crashing the Root server. This makes the internet <strong>Scalable</strong>.
                </p>
            </div>
        </section>

        <!-- GAME SECTION -->
        <section id="deployment-game" class="bg-slate-800 rounded-xl p-6 shadow-xl border border-slate-700">
            <h2 class="text-xl font-semibold mb-2 text-pink-400 flex items-center gap-2">
                <i data-lucide="gamepad-2" class="w-5 h-5"></i>
                Part 3: The Deployment Game
            </h2>
            <p class="mb-6 text-slate-300">
                You are a Network Engineer. Type the correct parts of the URL to configure your server.
            </p>

            <div class="grid lg:grid-cols-2 gap-8">
                <!-- Left: Configuration -->
                <div class="space-y-6">
                    <div class="bg-slate-900 p-5 rounded-lg border border-slate-600">
                        <h3 class="font-bold text-slate-200 mb-4 flex items-center gap-2">
                            <i data-lucide="settings" class="w-4 h-4"></i> 1. Configure URL
                        </h3>
                        <div class="space-y-4">
                            <!-- Protocol -->
                            <div class="relative">
                                <label class="block text-xs text-slate-400 mb-1">Protocol</label>
                                <div class="relative">
                                    <input type="text" id="game-protocol" 
                                           class="w-full bg-slate-800 border border-slate-600 rounded px-3 py-2 pr-10 focus:outline-none focus:border-blue-500 transition-colors"
                                           oninput="validateInput('protocol', this.value)">
                                    <div id="icon-protocol" class="absolute right-3 top-2.5"></div>
                                </div>
                                <p id="err-protocol" class="text-xs text-red-400 mt-1 hidden">Error: Invalid Protocol</p>
                            </div>
                            
                            <div class="flex gap-2">
                                <!-- Subdomain -->
                                <div class="w-1/3 relative">
                                    <label class="block text-xs text-slate-400 mb-1">Subdomain</label>
                                    <div class="relative">
                                        <input type="text" id="game-sub" 
                                               class="w-full bg-slate-800 border border-slate-600 rounded px-3 py-2 pr-8 focus:outline-none focus:border-blue-500 transition-colors"
                                               oninput="validateInput('sub', this.value)">
                                        <div id="icon-sub" class="absolute right-2 top-2.5"></div>
                                    </div>
                                    <p id="err-sub" class="text-[10px] text-red-400 mt-1 hidden">Invalid Sub</p>
                                </div>

                                <!-- Domain Name (Free text, no validation against list) -->
                                <div class="flex-1">
                                    <label class="block text-xs text-slate-400 mb-1">Domain Name</label>
                                    <input type="text" id="game-domain" class="w-full bg-slate-800 border border-slate-600 rounded px-3 py-2 text-white" maxlength="15">
                                </div>

                                <!-- TLD -->
                                <div class="w-1/3 relative">
                                    <label class="block text-xs text-slate-400 mb-1">TLD</label>
                                    <div class="relative">
                                        <input type="text" id="game-tld" 
                                               class="w-full bg-slate-800 border border-slate-600 rounded px-3 py-2 pr-8 focus:outline-none focus:border-blue-500 transition-colors"
                                               oninput="validateInput('tld', this.value)">
                                        <div id="icon-tld" class="absolute right-2 top-2.5"></div>
                                    </div>
                                    <p id="err-tld" class="text-[10px] text-red-400 mt-1 hidden">Invalid TLD</p>
                                </div>
                            </div>

                            <button onclick="deployServer()" id="deploy-btn" class="w-full bg-pink-600 hover:bg-pink-500 text-white font-bold py-3 rounded transition-colors flex items-center justify-center gap-2">
                                <i data-lucide="rocket" class="w-4 h-4"></i> Deploy Server
                            </button>
                            
                            <div id="deploy-error" class="bg-red-900/50 border border-red-500 text-red-200 p-2 rounded text-xs text-center hidden">
                                Configuration Error: Please correct the highlighted fields.
                            </div>

                            <!-- HINTS SECTION -->
                            <div class="mt-4 flex justify-center">
                                <div class="group relative inline-block">
                                    <span class="cursor-help text-xs font-bold text-slate-500 uppercase tracking-widest hover:text-blue-400 transition-colors border-b border-dashed border-slate-600 hover:border-blue-400 pb-1 flex items-center gap-1">
                                        <i data-lucide="help-circle" class="w-3 h-3"></i> Need Hints?
                                    </span>
                                    
                                    <!-- Tooltip -->
                                    <div class="absolute bottom-full left-1/2 -translate-x-1/2 mb-3 hidden group-hover:block w-64 bg-slate-800 border border-slate-600 shadow-2xl rounded p-4 z-50 tooltip-arrow">
                                        <h4 class="text-xs font-bold text-blue-300 uppercase mb-2 border-b border-slate-700 pb-1">Valid Options</h4>
                                        <div class="grid grid-cols-2 gap-2 text-xs">
                                            <div>
                                                <span class="text-slate-500 block text-[10px]">Protocols</span>
                                                <code class="text-green-400">https://</code><br>
                                                <code class="text-yellow-400">http://</code>
                                            </div>
                                            <div>
                                                <span class="text-slate-500 block text-[10px]">TLDs</span>
                                                <code class="text-purple-300">.com</code>, <code class="text-purple-300">.org</code><br>
                                                <code class="text-purple-300">.net</code>, <code class="text-purple-300">.io</code>
                                            </div>
                                            <div class="col-span-2 mt-1">
                                                <span class="text-slate-500 block text-[10px]">Subdomains</span>
                                                <span class="text-slate-300">www, shop, blog, app</span>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <!-- End Hints -->

                        </div>
                    </div>

                    <!-- Test Connection -->
                    <div id="test-zone" class="bg-slate-900 p-5 rounded-lg border border-slate-600 opacity-50 pointer-events-none transition-opacity">
                        <h3 class="font-bold text-slate-200 mb-4 flex items-center gap-2">
                            <i data-lucide="monitor-play" class="w-4 h-4"></i> 2. Test Connection
                        </h3>
                        <div class="flex gap-2">
                            <div class="flex-1 bg-slate-800 border border-slate-600 rounded px-3 py-2 text-slate-400 font-mono text-sm flex items-center" id="browser-bar">
                                <i data-lucide="lock" class="w-3 h-3 mr-2"></i> <span id="browser-url">about:blank</span>
                            </div>
                            <button onclick="testConnection()" class="bg-green-600 hover:bg-green-500 text-white px-4 py-2 rounded font-bold text-sm">
                                Go
                            </button>
                        </div>
                        <div id="test-log" class="mt-4 h-32 overflow-y-auto bg-black rounded p-2 font-mono text-xs text-green-400 border border-slate-700">
                            > System ready. Waiting for deployment...
                        </div>
                    </div>
                </div>

                <!-- Right: Visualizer -->
                <div class="bg-slate-900 rounded-lg border border-slate-600 p-6 flex flex-col items-center justify-center relative min-h-[400px]">
                    
                    <!-- Background Grid -->
                    <div class="absolute inset-0 opacity-10" style="background-image: radial-gradient(#64748b 1px, transparent 1px); background-size: 20px 20px;"></div>

                    <!-- DNS Cloud -->
                    <div class="mb-12 relative">
                        <div class="w-24 h-16 bg-blue-900/40 border border-blue-500 rounded-full flex items-center justify-center">
                            <span class="text-xs font-bold text-blue-300">DNS Cloud</span>
                        </div>
                        <!-- Arrows -->
                        <div id="dns-arrow-down" class="absolute top-full left-1/2 -translate-x-1/2 h-0 w-0.5 bg-yellow-400 transition-all duration-500"></div>
                    </div>

                    <!-- User Server -->
                    <div id="server-rack" class="w-32 h-40 bg-slate-800 border-2 border-slate-600 rounded flex flex-col items-center justify-end p-2 relative transition-all duration-500 opacity-30 scale-90">
                        <!-- Server Lights -->
                        <div class="flex gap-1 mb-auto mt-2 w-full px-2">
                            <div class="w-2 h-2 rounded-full bg-slate-600 server-led"></div>
                            <div class="w-2 h-2 rounded-full bg-slate-600 server-led"></div>
                            <div class="w-2 h-2 rounded-full bg-slate-600 server-led"></div>
                        </div>
                        <i data-lucide="server" class="w-16 h-16 text-slate-500 mb-2" id="server-icon"></i>
                        <div class="text-[10px] bg-black px-2 py-1 rounded text-slate-400 font-mono w-full text-center" id="server-ip">
                            Offline
                        </div>
                    </div>

                    <!-- Success Message -->
                    <div id="success-msg" class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 bg-green-500 text-white px-4 py-2 rounded shadow-lg font-bold hidden scale-0 transition-transform">
                        Site Live!
                    </div>

                </div>
            </div>
        </section>

        <!-- LECTURE CONCLUSION -->
        <article class="prose prose-invert max-w-none">
            <h2 class="text-3xl font-light text-white border-b border-slate-700 pb-2">Why this matters for AP CSP</h2>
            <div class="space-y-4">
                <p class="text-lg text-slate-300 leading-relaxed">
                    The AP Exam focuses heavily on two concepts related to DNS: <strong>Fault Tolerance</strong> and <strong>Open Protocols</strong>.
                </p>
                <div class="bg-slate-800 p-4 rounded-lg">
                    <h3 class="text-blue-400 font-bold mb-2">1. Fault Tolerance & Redundancy</h3>
                    <p class="text-slate-400 text-sm">
                        If one DNS server fails, the system doesn't break. Because the data is <strong>distributed</strong>, your resolver can simply ask a different root server or a backup TLD server. Furthermore, your computer and your ISP utilize <strong>caching</strong>. Once you know the IP for <code>google.com</code>, your computer saves it for a while (TTL - Time To Live) so it doesn't have to repeat the entire lookup process every time you click a link.
                    </p>
                </div>
                <div class="bg-slate-800 p-4 rounded-lg">
                    <h3 class="text-purple-400 font-bold mb-2">2. Open Protocols</h3>
                    <p class="text-slate-400 text-sm">
                        DNS is not owned by one company. It is an <strong>Open Protocol</strong> managed by organizations like IETF and ICANN. This openness is critical because it ensures that any device—whether it's an iPhone, an Android, or a smart fridge—can connect to the internet using the exact same "language" to find websites.
                    </p>
                </div>
            </div>
        </article>

        <!-- SECTION 4: QUIZ -->
        <section class="bg-slate-800 rounded-xl p-6 shadow-xl border border-slate-700">
             <h2 class="text-xl font-semibold mb-4 text-purple-400 flex items-center gap-2">
                <i data-lucide="clipboard-check" class="w-5 h-5"></i>
                Part 4: Quick Check
            </h2>
            <div class="grid md:grid-cols-2 gap-4">
                <div class="bg-slate-900 p-4 rounded border border-slate-600">
                    <p class="font-semibold text-sm mb-3">1. Why does the internet use DNS?</p>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500 mb-1" onclick="checkAnswer(this, false)">Because computers cannot read English.</button>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500 mb-1" onclick="checkAnswer(this, true)">To provide an abstraction mapping names to IPs.</button>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500" onclick="checkAnswer(this, false)">To make the internet more secure by hiding IPs.</button>
                </div>
                <div class="bg-slate-900 p-4 rounded border border-slate-600">
                    <p class="font-semibold text-sm mb-3">2. Which subdomain is in `docs.google.com`?</p>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500 mb-1" onclick="checkAnswer(this, false)">google</button>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500 mb-1" onclick="checkAnswer(this, false)">.com</button>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500" onclick="checkAnswer(this, true)">docs</button>
                </div>
            </div>
        </section>

    </main>

    <footer class="bg-slate-800 text-center p-4 text-xs text-slate-500 border-t border-slate-700">
        AP® is a trademark registered by the College Board, which is not affiliated with, and does not endorse, this product.
    </footer>

    <script>
        lucide.createIcons();

        // --- QUIZ LOGIC ---
        function checkAnswer(btn, isCorrect) {
            const parent = btn.parentElement;
            const siblings = parent.querySelectorAll('button');
            siblings.forEach(s => {
                s.className = "w-full text-left p-2 text-sm rounded transition-colors border border-transparent mb-1 opacity-50";
            });
            if(isCorrect) {
                btn.className = "w-full text-left p-2 text-sm bg-green-900/50 text-green-200 border border-green-500 rounded font-bold mb-1";
                btn.innerText += " ✅ Correct";
            } else {
                btn.className = "w-full text-left p-2 text-sm bg-red-900/50 text-red-200 border border-red-500 rounded mb-1";
                btn.innerText += " ❌ Try again";
            }
        }

        // --- PART 2: SIMULATION ANIMATION ---
        const packet = document.getElementById('packet');
        const statusBar = document.getElementById('status-bar');
        const simBtn = document.getElementById('sim-btn');
        let isSimRunning = false;

        function getPos(id) {
            const el = document.getElementById(id);
            const rect = el.getBoundingClientRect();
            const container = document.getElementById('dns-sim').getBoundingClientRect();
            return {
                x: rect.left - container.left + rect.width/2 - 8,
                y: rect.top - container.top + rect.height/2 - 8
            };
        }

        async function moveTo(targetId, speed = 1000) {
            const pos = getPos(targetId);
            packet.style.transition = `all ${speed}ms ease-in-out`;
            packet.style.transform = `translate(${pos.x}px, ${pos.y}px)`;
            await new Promise(r => setTimeout(r, speed));
        }

        function highlight(id, active) {
            const el = document.getElementById(id);
            if(active) {
                el.classList.remove('opacity-50', 'border-2');
                el.classList.add('opacity-100', 'border-4', 'shadow-[0_0_15px_rgba(255,255,255,0.3)]');
            } else {
                el.classList.add('opacity-50', 'border-2');
                el.classList.remove('opacity-100', 'border-4', 'shadow-[0_0_15px_rgba(255,255,255,0.3)]');
            }
        }

        function updateStatus(text) {
            statusBar.innerHTML = text;
        }

        function resetSimulation() {
            isSimRunning = false;
            packet.classList.add('hidden');
            highlight('node-user', false);
            highlight('node-resolver', false);
            highlight('node-root', false);
            highlight('node-tld', false);
            highlight('node-auth', false);
            updateStatus("Ready to resolve hostname...");
            simBtn.disabled = false;
            simBtn.classList.remove('opacity-50', 'cursor-not-allowed');
        }

        async function startSimulation() {
            if(isSimRunning) return;
            isSimRunning = true;
            simBtn.disabled = true;
            simBtn.classList.add('opacity-50', 'cursor-not-allowed');
            const startPos = getPos('node-user');
            packet.style.transform = `translate(${startPos.x}px, ${startPos.y}px)`;
            packet.classList.remove('hidden');
            updateStatus("Step 1: Computer asks ISP Resolver: 'Where is store.nike.com?'");
            highlight('node-user', true);
            await new Promise(r => setTimeout(r, 1000));
            await moveTo('node-resolver');
            highlight('node-resolver', true);
            updateStatus("Resolver checks cache... Not found. Asking Root Server.");
            await new Promise(r => setTimeout(r, 1500));
            await moveTo('node-root');
            highlight('node-root', true);
            updateStatus("Step 2: Root Server says: 'I don't know nike, but here is the .com server.'");
            await new Promise(r => setTimeout(r, 2000));
            highlight('node-root', false);
            await moveTo('node-resolver', 500);
            updateStatus("Resolver contacts the .com TLD Server...");
            await moveTo('node-tld');
            highlight('node-tld', true);
            updateStatus("Step 3: TLD Server says: 'Here is the IP for Nike's Authoritative Server.'");
            await new Promise(r => setTimeout(r, 2000));
            highlight('node-tld', false);
            await moveTo('node-resolver', 500);
            updateStatus("Resolver contacts Nike's Server...");
            await moveTo('node-auth');
            highlight('node-auth', true);
            updateStatus("Step 4: Authoritative Server says: 'store.nike.com is at 15.197.148.33'");
            await new Promise(r => setTimeout(r, 2000));
            highlight('node-auth', false);
            await moveTo('node-resolver', 500);
            updateStatus("Resolver caches the IP and sends it to your computer.");
            await moveTo('node-user');
            updateStatus("Success! Browser connects to 15.197.148.33");
            highlight('node-user', true);
            highlight('node-resolver', false);
            await new Promise(r => setTimeout(r, 2000));
            isSimRunning = false;
            simBtn.disabled = false;
            simBtn.classList.remove('opacity-50', 'cursor-not-allowed');
        }

        // --- PART 3: GAME LOGIC ---
        let deployedIP = null;
        let deployedURL = null;

        const validOptions = {
            protocol: ['https://', 'http://'],
            sub: ['www', 'shop', 'blog', 'app'],
            tld: ['.com', '.org', '.net', '.io']
        };

        const validationState = {
            protocol: false,
            sub: false,
            tld: false
        };

        function validateInput(type, value) {
            const iconId = `icon-${type}`;
            const errId = `err-${type}`;
            const iconEl = document.getElementById(iconId);
            const errEl = document.getElementById(errId);
            const inputEl = document.getElementById(`game-${type}`);

            // Basic normalization (lowercase)
            const cleanValue = value.toLowerCase().trim();

            if (validOptions[type].includes(cleanValue)) {
                // VALID
                iconEl.innerHTML = '<i data-lucide="check" class="w-4 h-4 text-green-500"></i>';
                lucide.createIcons(); // refresh new icon
                errEl.classList.add('hidden');
                inputEl.classList.remove('border-red-500');
                inputEl.classList.add('border-green-500');
                validationState[type] = true;
            } else {
                // INVALID
                if(cleanValue.length === 0) {
                     iconEl.innerHTML = '';
                     errEl.classList.add('hidden');
                     inputEl.classList.remove('border-red-500', 'border-green-500');
                } else {
                    iconEl.innerHTML = ''; // Don't show X inside input, border handles it
                    errEl.classList.remove('hidden');
                    inputEl.classList.add('border-red-500');
                    inputEl.classList.remove('border-green-500');
                }
                validationState[type] = false;
            }
            
            // Hide main error box if it was open
            document.getElementById('deploy-error').classList.add('hidden');
        }

        function logGame(msg) {
            const log = document.getElementById('test-log');
            log.innerHTML += `<div>> ${msg}</div>`;
            log.scrollTop = log.scrollHeight;
        }

        function getRandomIP() {
            return `${Math.floor(Math.random()*255)}.${Math.floor(Math.random()*255)}.${Math.floor(Math.random()*255)}.${Math.floor(Math.random()*255)}`;
        }

        async function deployServer() {
            // Check validations
            if (!validationState.protocol || !validationState.sub || !validationState.tld) {
                document.getElementById('deploy-error').classList.remove('hidden');
                return;
            }

            const domain = document.getElementById('game-domain').value;
            if(!domain) { alert("Please enter a domain name."); return; }

            const protocol = document.getElementById('game-protocol').value;
            const sub = document.getElementById('game-sub').value;
            const tld = document.getElementById('game-tld').value;
            
            deployedURL = `${protocol}${sub}.${domain}${tld}`;
            
            // Disable deploy button
            const btn = document.getElementById('deploy-btn');
            btn.disabled = true;
            btn.innerHTML = `<i data-lucide="loader" class="animate-spin w-4 h-4"></i> Deploying...`;

            // Animate Server Rack
            const rack = document.getElementById('server-rack');
            const icon = document.getElementById('server-icon');
            const ipDisplay = document.getElementById('server-ip');
            
            rack.classList.remove('opacity-30', 'scale-90');
            rack.classList.add('opacity-100', 'scale-100', 'border-green-500', 'shadow-[0_0_20px_rgba(34,197,94,0.3)]');
            icon.classList.remove('text-slate-500');
            icon.classList.add('text-green-400');
            
            // Turn on lights
            document.querySelectorAll('.server-led').forEach(led => {
                led.classList.remove('bg-slate-600');
                led.classList.add('bg-green-500', 'server-light');
            });

            logGame("Initializing server instance...");
            await new Promise(r => setTimeout(r, 800));
            
            deployedIP = getRandomIP();
            ipDisplay.innerText = deployedIP;
            ipDisplay.classList.remove('text-slate-400');
            ipDisplay.classList.add('text-green-400', 'font-bold');
            
            logGame(`Server Online at ${deployedIP}`);
            await new Promise(r => setTimeout(r, 800));

            logGame(`Registering A-Record for ${deployedURL}...`);
            const arrow = document.getElementById('dns-arrow-down');
            arrow.style.height = '40px'; // connect dns to server
            
            await new Promise(r => setTimeout(r, 1000));
            logGame("DNS Propagation Complete.");

            // Enable Test Zone
            document.getElementById('test-zone').classList.remove('opacity-50', 'pointer-events-none');
            document.getElementById('browser-bar').classList.add('bg-white', 'text-black');
            document.getElementById('browser-bar').classList.remove('bg-slate-800', 'text-slate-400');
            document.getElementById('browser-url').innerText = deployedURL;

            btn.innerHTML = `<i data-lucide="check" class="w-4 h-4"></i> Deployed`;
        }

        async function testConnection() {
            if(!deployedURL) return;
            
            logGame(`Browser requesting ${deployedURL}...`);
            
            // Visual feedback
            const browserBar = document.getElementById('browser-bar');
            browserBar.classList.add('ring-2', 'ring-blue-500');
            
            await new Promise(r => setTimeout(r, 500));
            logGame(`DNS Lookup: Resolved to ${deployedIP}`);
            
            await new Promise(r => setTimeout(r, 500));
            logGame(`Handshake with ${deployedIP}... Success.`);
            
            // Show Success Msg
            const msg = document.getElementById('success-msg');
            msg.classList.remove('hidden', 'scale-0');
            msg.classList.add('scale-100');
            
            await new Promise(r => setTimeout(r, 2000));
            browserBar.classList.remove('ring-2', 'ring-blue-500');
            msg.classList.add('hidden');
        }

    </script>
</body>
</html>