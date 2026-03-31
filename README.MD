<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flow Minimal Launcher • Minimal Android Launcher</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Space+Grotesk:wght@500;600;700&display=swap');
        
        :root {
            --primary: #3DDC84;
        }
        
        * {
            transition-property: color, background-color, border-color, text-decoration-color, fill, stroke;
            transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
            transition-duration: 150ms;
        }
        
        .hero-bg {
            background: linear-gradient(135deg, #0f172a 0%, #1e2937 100%);
        }
        
        .glass {
            background: rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(20px);
        }
        
        .section-header {
            font-family: 'Space Grotesk', sans-serif;
        }
    </style>
</head>
<body class="bg-slate-950 text-white font-sans">

    <!-- NAVBAR -->
    <nav class="sticky top-0 z-50 glass border-b border-white/10">
        <div class="max-w-7xl mx-auto px-6 py-5 flex items-center justify-between">
            <!-- Logo + Title -->
            <div class="flex items-center gap-3">
                <img src="app/src/main/res/mipmap-xxxhdpi/ic_launcher.png" alt="Flow Launcher" class="w-10 h-10 rounded-2xl">
                <div>
                    <h1 class="text-2xl font-bold tracking-tighter section-header">Flow</h1>
                    <p class="text-xs text-emerald-400 -mt-1">Minimal Launcher</p>
                </div>
            </div>

            <!-- Navigation Links dengan ID -->
            <div class="hidden md:flex items-center gap-8 text-sm font-medium">
                <a onclick="smoothScrollTo('home')" class="hover:text-emerald-400 cursor-pointer">Beranda</a>
                <a onclick="smoothScrollTo('features')" class="hover:text-emerald-400 cursor-pointer">Fitur</a>
                <a onclick="smoothScrollTo('preview')" class="hover:text-emerald-400 cursor-pointer">Preview</a>
                <a onclick="smoothScrollTo('install')" class="hover:text-emerald-400 cursor-pointer">Install</a>
            </div>

            <!-- Buttons Fungsional -->
            <div class="flex items-center gap-3">
                <!-- GitHub Button -->
                <button onclick="goToGitHub()" 
                        id="github-btn"
                        class="flex items-center gap-2 px-5 py-2.5 bg-white text-slate-900 rounded-2xl font-semibold text-sm hover:scale-105 active:scale-95">
                    <i class="fa-brands fa-github"></i>
                    <span>GitHub</span>
                </button>

                <!-- Download Button (Fungsional) -->
                <button onclick="downloadAPK()" 
                        id="download-btn"
                        class="flex items-center gap-2 px-6 py-2.5 bg-emerald-500 hover:bg-emerald-600 rounded-2xl font-semibold text-sm shadow-lg shadow-emerald-500/30 hover:scale-105 active:scale-95">
                    <i class="fa-solid fa-download"></i>
                    <span>Download APK</span>
                </button>

                <!-- Mobile Menu Button -->
                <button onclick="toggleMobileMenu()" class="md:hidden text-2xl">
                    <i class="fa-solid fa-bars" id="menu-icon"></i>
                </button>
            </div>
        </div>

        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden md:hidden px-6 py-4 border-t border-white/10 bg-slate-900">
            <a onclick="smoothScrollTo('home');toggleMobileMenu()" class="block py-3 text-lg">Beranda</a>
            <a onclick="smoothScrollTo('features');toggleMobileMenu()" class="block py-3 text-lg">Fitur</a>
            <a onclick="smoothScrollTo('preview');toggleMobileMenu()" class="block py-3 text-lg">Preview</a>
            <a onclick="smoothScrollTo('install');toggleMobileMenu()" class="block py-3 text-lg">Cara Install</a>
        </div>
    </nav>

    <!-- HERO SECTION -->
    <section id="home" class="hero-bg pt-20 pb-16">
        <div class="max-w-7xl mx-auto px-6 text-center">
            <div class="flex justify-center mb-8">
                <img src="app/src/main/res/mipmap-xxxhdpi/ic_launcher.png" 
                     alt="Flow Minimal Launcher icon" 
                     class="w-28 h-28 rounded-3xl shadow-2xl shadow-emerald-500/30">
            </div>

            <h1 class="text-6xl md:text-7xl font-bold tracking-tighter section-header leading-none mb-4">
                Flow Minimal Launcher
            </h1>
            
            <p class="text-2xl text-emerald-400 font-medium mb-6">
                Your apps. Your clock. Your wallpaper.
            </p>
            
            <p class="max-w-md mx-auto text-lg text-slate-400 mb-10">
                Layar utama Android yang minimalis dan elegan.<br>
                Tanpa gangguan. Hanya yang kamu butuhkan.
            </p>

            <!-- Badges -->
            <div class="flex flex-wrap justify-center gap-3 mb-12">
                <span class="px-4 py-1.5 bg-white/10 text-white text-sm font-medium rounded-3xl flex items-center gap-1">
                    <i class="fa-brands fa-android text-emerald-400"></i>
                    Android
                </span>
                <span class="px-4 py-1.5 bg-white/10 text-white text-sm font-medium rounded-3xl">Min SDK 23</span>
                <span class="px-4 py-1.5 bg-white/10 text-white text-sm font-medium rounded-3xl">MIT License</span>
                <span class="px-4 py-1.5 bg-emerald-400 text-slate-900 text-sm font-semibold rounded-3xl">V3</span>
            </div>

            <div class="flex flex-col sm:flex-row gap-4 justify-center">
                <button onclick="downloadAPK()" 
                        class="px-10 py-4 bg-emerald-500 hover:bg-emerald-600 text-lg font-semibold rounded-3xl flex items-center justify-center gap-3 text-slate-900">
                    <i class="fa-solid fa-download"></i>
                    Download Sekarang (Gratis)
                </button>
                
                <button onclick="goToGitHub()" 
                        class="px-8 py-4 border border-white/30 hover:border-white/70 text-lg font-medium rounded-3xl flex items-center gap-3">
                    <i class="fa-brands fa-github"></i>
                    Lihat di GitHub
                </button>
            </div>

            <p class="text-xs text-slate-500 mt-8">Built with ❤️ in Indonesia • Android 6.0+</p>
        </div>
    </section>

    <!-- PREVIEW IMAGE -->
    <section id="preview" class="max-w-7xl mx-auto px-6 -mt-8">
        <div class="bg-slate-900 rounded-3xl overflow-hidden shadow-2xl border border-white/10">
            <img src="public/image/image.jpg" 
                 alt="Flow Minimal Launcher Preview" 
                 class="w-full">
        </div>
    </section>

    <!-- THREE SCREENS -->
    <div class="max-w-7xl mx-auto px-6 py-20">
        <div class="grid md:grid-cols-3 gap-8">
            <!-- Home -->
            <div class="bg-slate-900/70 rounded-3xl p-8 border border-white/10 hover:border-emerald-400/30 group">
                <div class="flex items-center gap-3 mb-6">
                    <div class="w-8 h-8 bg-emerald-400 rounded-2xl flex items-center justify-center text-slate-900 text-xl">🏠</div>
                    <h3 class="text-2xl font-semibold">Home</h3>
                </div>
                <p class="text-slate-400 mb-8">Clock • Date • Weather</p>
                <p class="text-emerald-400 text-sm font-medium">Jam • Tanggal • Cuaca</p>
                <div class="mt-12 text-5xl font-light text-slate-300 group-hover:text-emerald-400">Clean &amp; Beautiful</div>
            </div>

            <!-- Drawer -->
            <div class="bg-slate-900/70 rounded-3xl p-8 border border-white/10 hover:border-emerald-400/30 group">
                <div class="flex items-center gap-3 mb-6">
                    <div class="w-8 h-8 bg-emerald-400 rounded-2xl flex items-center justify-center text-slate-900 text-xl">📋</div>
                    <h3 class="text-2xl font-semibold">Drawer</h3>
                </div>
                <p class="text-slate-400 mb-8">Alphabetical + Live Search</p>
                <p class="text-emerald-400 text-sm font-medium">Alfabet + Pencarian Langsung</p>
                <div class="mt-12 text-5xl font-light text-slate-300 group-hover:text-emerald-400">Instant Find</div>
            </div>

            <!-- Feed -->
            <div class="bg-slate-900/70 rounded-3xl p-8 border border-white/10 hover:border-emerald-400/30 group">
                <div class="flex items-center gap-3 mb-6">
                    <div class="w-8 h-8 bg-emerald-400 rounded-2xl flex items-center justify-center text-slate-900 text-xl">📅</div>
                    <h3 class="text-2xl font-semibold">Feed</h3>
                </div>
                <p class="text-slate-400 mb-8">Tasks • Calendar • Screen Time</p>
                <p class="text-emerald-400 text-sm font-medium">Tugas • Kalender • Screen Time</p>
                <div class="mt-12 text-5xl font-light text-slate-300 group-hover:text-emerald-400">Stay Productive</div>
            </div>
        </div>
    </div>

    <!-- FEATURES -->
    <section id="features" class="bg-slate-900 py-20">
        <div class="max-w-7xl mx-auto px-6">
            <h2 class="text-5xl font-bold text-center section-header mb-16">Fitur Utama</h2>
            
            <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                <div class="flex gap-6">
                    <i class="fa-solid fa-clock text-4xl text-emerald-400 mt-1"></i>
                    <div>
                        <h4 class="text-xl font-semibold mb-2">Clock, Date &amp; Weather</h4>
                        <p class="text-slate-400">Tampilan sekilas yang indah dengan tipografi premium.</p>
                    </div>
                </div>
                <div class="flex gap-6">
                    <i class="fa-solid fa-thumbtack text-4xl text-emerald-400 mt-1"></i>
                    <div>
                        <h4 class="text-xl font-semibold mb-2">Pinned &amp; Most Used Apps</h4>
                        <p class="text-slate-400">Akses cepat ke aplikasi favoritmu di layar utama.</p>
                    </div>
                </div>
                <div class="flex gap-6">
                    <i class="fa-solid fa-magnifying-glass text-4xl text-emerald-400 mt-1"></i>
                    <div>
                        <h4 class="text-xl font-semibold mb-2">Live Search Drawer</h4>
                        <p class="text-slate-400">Cari aplikasi dengan pencarian langsung yang super cepat.</p>
                    </div>
                </div>
                <div class="flex gap-6">
                    <i class="fa-solid fa-calendar text-4xl text-emerald-400 mt-1"></i>
                    <div>
                        <h4 class="text-xl font-semibold mb-2">Calendar &amp; Tasks Feed</h4>
                        <p class="text-slate-400">Event kalender, daftar tugas, dan screen time insight.</p>
                    </div>
                </div>
                <div class="flex gap-6">
                    <i class="fa-solid fa-image text-4xl text-emerald-400 mt-1"></i>
                    <div>
                        <h4 class="text-xl font-semibold mb-2">Transparent Background</h4>
                        <p class="text-slate-400">Dukungan penuh untuk live wallpaper dan transparansi.</p>
                    </div>
                </div>
                <div class="flex gap-6">
                    <i class="fa-solid fa-leaf text-4xl text-emerald-400 mt-1"></i>
                    <div>
                        <h4 class="text-xl font-semibold mb-2">Ringan &amp; Cepat</h4>
                        <p class="text-slate-400">Performa tinggi dengan izin minimal.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- INSTALLATION -->
    <section id="install" class="max-w-7xl mx-auto px-6 py-20">
        <div class="bg-gradient-to-br from-emerald-500 to-teal-600 rounded-3xl p-12 text-center text-slate-900">
            <h2 class="text-4xl font-bold mb-8">Siap Pakai dalam 30 Detik</h2>
            <div class="max-w-md mx-auto">
                <ol class="text-left space-y-6 text-lg">
                    <li class="flex gap-4"><span class="font-mono font-bold text-2xl">1</span> Download APK terbaru</li>
                    <li class="flex gap-4"><span class="font-mono font-bold text-2xl">2</span> Izinkan instalasi dari sumber tidak dikenal</li>
                    <li class="flex gap-4"><span class="font-mono font-bold text-2xl">3</span> Buka aplikasi → Set as Default Launcher</li>
                </ol>
            </div>
            
            <!-- Tombol Fungsional di bagian Install -->
            <button onclick="downloadAPK()" 
                    class="mt-12 px-12 py-6 bg-white text-slate-900 text-2xl font-semibold rounded-3xl flex items-center gap-4 mx-auto hover:scale-105 shadow-2xl">
                <i class="fa-solid fa-download"></i>
                DOWNLOAD APK SEKARANG
            </button>
        </div>
    </section>

    <!-- AUTHOR -->
    <footer class="border-t border-white/10 py-16">
        <div class="max-w-7xl mx-auto px-6 text-center">
            <div class="flex justify-center mb-6">
                <a href="https://github.com/01satria" target="_blank">
                    <img src="https://github.com/01satria.png" 
                         alt="Satria Bagus" 
                         class="w-24 h-24 rounded-full border-4 border-emerald-400">
                </a>
            </div>
            <h3 class="text-2xl font-semibold">Satria Bagus</h3>
            <p class="text-emerald-400">Built with ❤️ in Indonesia</p>
            
            <div class="mt-8 flex justify-center gap-6 text-3xl">
                <a href="https://github.com/01satria" target="_blank" class="hover:text-emerald-400"><i class="fa-brands fa-github"></i></a>
            </div>
            
            <p class="text-xs text-slate-500 mt-12">
                © Flow Minimal Launcher • MIT License • V3
            </p>
        </div>
    </footer>

    <!-- TOAST NOTIFICATION -->
    <div id="toast" onclick="this.classList.add('hidden')" 
         class="hidden fixed bottom-6 right-6 bg-emerald-500 text-white px-6 py-4 rounded-3xl shadow-2xl flex items-center gap-3">
        <i class="fa-solid fa-check-circle"></i>
        <span id="toast-text" class="font-medium"></span>
    </div>

    <script>
        // Tailwind CSS Configuration
        function initializeTailwind() {
            tailwind.config = {
                content: [],
                theme: {
                    extend: {}
                }
            }
        }

        // Smooth Scroll ke Section (Fungsional)
        function smoothScrollTo(section) {
            const element = document.getElementById(section);
            if (element) {
                element.scrollIntoView({
                    behavior: "smooth",
                    block: "start"
                });
            }
        }

        // Download APK Button (Fungsional)
        function downloadAPK() {
            const toast = document.getElementById('toast');
            const toastText = document.getElementById('toast-text');
            
            // Ganti dengan link releases GitHub kamu nanti
            window.open('https://github.com/01satria/releases/latest', '_blank');
            
            // Tampilkan toast
            toastText.textContent = 'Membuka halaman download...';
            toast.classList.remove('hidden');
            
            // Auto hide setelah 3 detik
            setTimeout(() => {
                toast.classList.add('hidden');
            }, 3000);
        }

        // GitHub Button (Fungsional)
        function goToGitHub() {
            window.open('https://github.com/01satria', '_blank');
            
            const toast = document.getElementById('toast');
            const toastText = document.getElementById('toast-text');
            toastText.textContent = 'Membuka GitHub profile...';
            toast.classList.remove('hidden');
            
            setTimeout(() => toast.classList.add('hidden'), 2500);
        }

        // Mobile Menu Toggle (Fungsional)
        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu');
            const icon = document.getElementById('menu-icon');
            
            if (menu.classList.contains('hidden')) {
                menu.classList.remove('hidden');
                icon.classList.replace('fa-bars', 'fa-xmark');
            } else {
                menu.classList.add('hidden');
                icon.classList.replace('fa-xmark', 'fa-bars');
            }
        }

        // Keyboard Shortcut (Bonus fungsional)
        function addKeyboardShortcuts() {
            document.addEventListener('keydown', (e) => {
                if (e.metaKey && e.key === "k") {
                    e.preventDefault();
                    downloadAPK();
                }
            });
        }

        // Initialize semua fungsi saat halaman dimuat
        window.onload = function() {
            initializeTailwind();
            addKeyboardShortcuts();
            
            console.log('%c✅ Flow Minimal Launcher HTML siap! Semua button dan ID fungsional.', 'color:#3DDC84; font-weight:bold');
        };
    </script>
</body>
</html>
