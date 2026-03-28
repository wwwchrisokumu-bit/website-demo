<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chris Ororo Son Website</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
        
        * {
            font-family: 'Inter', sans-serif;
        }
        
        .glass-effect {
            background: rgba(17, 24, 39, 0.7);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .gradient-bg {
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #0f172a 100%);
        }
        
        .neon-glow {
            box-shadow: 0 0 20px rgba(59, 130, 246, 0.3);
        }
        
        .file-card {
            transition: all 0.3s ease;
        }
        
        .file-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }
        
        .sidebar-link {
            transition: all 0.2s ease;
        }
        
        .sidebar-link:hover, .sidebar-link.active {
            background: rgba(59, 130, 246, 0.1);
            border-right: 3px solid #3b82f6;
            color: #3b82f6;
        }
        
        .upload-area {
            background: repeating-linear-gradient(
                45deg,
                rgba(59, 130, 246, 0.05),
                rgba(59, 130, 246, 0.05) 10px,
                rgba(59, 130, 246, 0.02) 10px,
                rgba(59, 130, 246, 0.02) 20px
            );
            border: 2px dashed rgba(59, 130, 246, 0.4);
        }
        
        .upload-area.dragover {
            background: rgba(59, 130, 246, 0.1);
            border-color: #3b82f6;
        }
        
        .custom-scrollbar::-webkit-scrollbar {
            width: 6px;
        }
        
        .custom-scrollbar::-webkit-scrollbar-track {
            background: #1e293b;
        }
        
        .custom-scrollbar::-webkit-scrollbar-thumb {
            background: #3b82f6;
            border-radius: 3px;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .animate-fade-in {
            animation: fadeIn 0.5s ease-out;
        }
        
        .login-bg {
            background-image: 
                radial-gradient(circle at 20% 50%, rgba(59, 130, 246, 0.15) 0%, transparent 50%),
                radial-gradient(circle at 80% 80%, rgba(139, 92, 246, 0.15) 0%, transparent 50%),
                radial-gradient(circle at 40% 20%, rgba(59, 130, 246, 0.1) 0%, transparent 50%);
        }
    </style>
</head>
<body class="gradient-bg text-gray-100 min-h-screen overflow-hidden">

    <!-- Login Screen -->
    <div id="loginScreen" class="fixed inset-0 z-50 flex items-center justify-center login-bg">
        <div class="glass-effect p-8 rounded-2xl w-full max-w-md mx-4 shadow-2xl border border-blue-500/20">
            <div class="text-center mb-8">
                <div class="w-16 h-16 bg-blue-600 rounded-xl flex items-center justify-center mx-auto mb-4 neon-glow">
                    <i data-lucide="shield" class="w-8 h-8 text-white"></i>
                </div>
                <h1 class="text-2xl font-bold text-white mb-2">Chris Ororo Son</h1>
                <p class="text-gray-400 text-sm">Secure Document Management System</p>
            </div>
            
            <form id="loginForm" class="space-y-6">
                <div>
                    <label class="block text-sm font-medium text-gray-300 mb-2">Username</label>
                    <div class="relative">
                        <i data-lucide="user" class="absolute left-3 top-3 w-5 h-5 text-gray-500"></i>
                        <input type="text" id="username" required 
                            class="w-full pl-10 pr-4 py-3 bg-gray-800/50 border border-gray-700 rounded-lg focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all text-white placeholder-gray-500"
                            placeholder="Enter username">
                    </div>
                </div>
                
                <div>
                    <label class="block text-sm font-medium text-gray-300 mb-2">Password</label>
                    <div class="relative">
                        <i data-lucide="lock" class="absolute left-3 top-3 w-5 h-5 text-gray-500"></i>
                        <input type="password" id="password" required 
                            class="w-full pl-10 pr-4 py-3 bg-gray-800/50 border border-gray-700 rounded-lg focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none transition-all text-white placeholder-gray-500"
                            placeholder="Enter password">
                        <button type="button" id="togglePassword" class="absolute right-3 top-3 text-gray-500 hover:text-gray-300">
                            <i data-lucide="eye" class="w-5 h-5"></i>
                        </button>
                    </div>
                </div>
                
                <div id="loginError" class="hidden text-red-400 text-sm text-center bg-red-900/20 p-2 rounded-lg border border-red-500/30">
                    Invalid credentials. Please try again.
                </div>
                
                <div class="flex items-center justify-between text-sm">
                    <label class="flex items-center text-gray-400 cursor-pointer">
                        <input type="checkbox" id="rememberMe" class="mr-2 rounded bg-gray-800 border-gray-700 text-blue-600 focus:ring-blue-500">
                        Remember me
                    </label>
                    <a href="#" class="text-blue-400 hover:text-blue-300 transition-colors">Forgot password?</a>
                </div>
                
                <button type="submit" 
                    class="w-full bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 rounded-lg transition-all transform hover:scale-[1.02] neon-glow flex items-center justify-center gap-2">
                    <i data-lucide="log-in" class="w-5 h-5"></i>
                    Secure Login
                </button>
            </form>
            
            <div class="mt-6 text-center text-xs text-gray-500">
                <p>Credentials: <span class="text-blue-400">admin</span> / <span class="text-blue-400">TechSecure2024!</span></p>
            </div>
        </div>
    </div>

    <!-- Main Application -->
    <div id="app" class="hidden flex h-screen">
        <!-- Sidebar -->
        <aside class="w-64 glass-effect flex flex-col border-r border-gray-800">
            <div class="p-6 border-b border-gray-800">
                <div class="flex items-center gap-3">
                    <div class="w-10 h-10 bg-blue-600 rounded-lg flex items-center justify-center">
                        <i data-lucide="shield-check" class="w-6 h-6 text-white"></i>
                    </div>
                    <div>
                        <h2 class="font-bold text-white">Chris Ororo Son</h2>
                        <p class="text-xs text-gray-400">Expert Mode</p>
                    </div>
                </div>
            </div>
            
            <nav class="flex-1 overflow-y-auto custom-scrollbar p-4 space-y-2">
                <button onclick="showSection('dashboard')" class="sidebar-link active w-full flex items-center gap-3 px-4 py-3 rounded-lg text-gray-300 hover:text-white">
                    <i data-lucide="layout-dashboard" class="w-5 h-5"></i>
                    <span>Dashboard</span>
                </button>
                
                <button onclick="showSection('documents')" class="sidebar-link w-full flex items-center gap-3 px-4 py-3 rounded-lg text-gray-300 hover:text-white">
                    <i data-lucide="file-text" class="w-5 h-5"></i>
                    <span>All Documents</span>
                    <span id="docCount" class="ml-auto bg-blue-600 text-xs px-2 py-1 rounded-full">0</span>
                </button>
                
                <div class="pt-4 pb-2 px-4 text-xs font-semibold text-gray-500 uppercase tracking-wider">Categories</div>
                
                <button onclick="filterByCategory('technical')" class="sidebar-link w-full flex items-center gap-3 px-4 py-2 rounded-lg text-gray-400 hover:text-white text-sm">
                    <i data-lucide="code" class="w-4 h-4"></i>
                    <span>Technical Docs</span>
                </button>
                
                <button onclick="filterByCategory('certificates')" class="sidebar-link w-full flex items-center gap-3 px-4 py-2 rounded-lg text-gray-400 hover:text-white text-sm">
                    <i data-lucide="award" class="w-4 h-4"></i>
                    <span>Certificates</span>
                </button>
                
                <button onclick="filterByCategory('projects')" class="sidebar-link w-full flex items-center gap-3 px-4 py-2 rounded-lg text-gray-400 hover:text-white text-sm">
                    <i data-lucide="folder-git" class="w-4 h-4"></i>
                    <span>Projects</span>
                </button>
                
                <button onclick="filterByCategory('images')" class="sidebar-link w-full flex items-center gap-3 px-4 py-2 rounded-lg text-gray-400 hover:text-white text-sm">
                    <i data-lucide="image" class="w-4 h-4"></i>
                    <span>Images</span>
                </button>
                
                <button onclick="filterByCategory('system')" class="sidebar-link w-full flex items-center gap-3 px-4 py-2 rounded-lg text-gray-400 hover:text-white text-sm">
                    <i data-lucide="terminal" class="w-4 h-4"></i>
                    <span>System Files</span>
                </button>
            </nav>
            
            <div class="p-4 border-t border-gray-800 space-y-2">
                <button onclick="showSection('profile')" class="sidebar-link w-full flex items-center gap-3 px-4 py-3 rounded-lg text-gray-300 hover:text-white">
                    <i data-lucide="user-circle" class="w-5 h-5"></i>
                    <span>Profile</span>
                </button>
                
                <button onclick="logout()" class="w-full flex items-center gap-3 px-4 py-3 rounded-lg text-red-400 hover:bg-red-900/20 hover:text-red-300 transition-all">
                    <i data-lucide="log-out" class="w-5 h-5"></i>
                    <span>Logout</span>
                </button>
            </div>
        </aside>

        <!-- Main Content -->
        <main class="flex-1 flex flex-col overflow-hidden relative">
            <!-- Header -->
            <header class="glass-effect border-b border-gray-800 px-8 py-4 flex items-center justify-between">
                <div class="flex items-center gap-4 flex-1">
                    <h1 id="pageTitle" class="text-2xl font-bold text-white">Dashboard</h1>
                    
                    <div class="flex-1 max-w-md ml-8 relative">
                        <i data-lucide="search" class="absolute left-3 top-2.5 w-5 h-5 text-gray-500"></i>
                        <input type="text" id="searchInput" placeholder="Search documents..." 
                            class="w-full pl-10 pr-4 py-2 bg-gray-800/50 border border-gray-700 rounded-lg focus:border-blue-500 focus:ring-2 focus:ring-blue-500/20 outline-none text-white placeholder-gray-500"
                            onkeyup="searchDocuments()">
                    </div>
                </div>
                
                <div class="flex items-center gap-4">
                    <button onclick="showUploadModal()" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-lg flex items-center gap-2 transition-all hover:scale-105">
                        <i data-lucide="upload-cloud" class="w-5 h-5"></i>
                        <span class="hidden sm:inline">Upload</span>
                    </button>
                    
                    <div class="flex items-center gap-3 pl-4 border-l border-gray-700">
                        <div class="text-right hidden md:block">
                            <p class="text-sm font-medium text-white">Chris Ororo Son</p>
                            <p class="text-xs text-gray-400">Son Of Yahweh</p>
                        </div>
                        <img src="http://static.photos/technology/200x200/42" alt="Profile" class="w-10 h-10 rounded-full border-2 border-blue-500">
                    </div>
                </div>
            </header>

            <!-- Content Area -->
            <div id="contentArea" class="flex-1 overflow-y-auto custom-scrollbar p-8">
                
                <!-- Dashboard Section -->
                <div id="dashboardSection" class="animate-fade-in">
                    <div class="grid grid-cols-1 md:grid-cols-4 gap-6 mb-8">
                        <div class="glass-effect p-6 rounded-xl border border-gray-700">
                            <div class="flex items-center justify-between mb-4">
                                <div class="p-3 bg-blue-500/20 rounded-lg">
                                    <i data-lucide="files" class="w-6 h-6 text-blue-400"></i>
                                </div>
                                <span class="text-xs text-gray-400">Total Files</span>
                            </div>
                            <p class="text-3xl font-bold text-white" id="totalFiles">0</p>
                            <p class="text-sm text-gray-400 mt-1">Documents stored</p>
                        </div>
                        
                        <div class="glass-effect p-6 rounded-xl border border-gray-700">
                            <div class="flex items-center justify-between mb-4">
                                <div class="p-3 bg-green-500/20 rounded-lg">
                                    <i data-lucide="hard-drive" class="w-6 h-6 text-green-400"></i>
                                </div>
                                <span class="text-xs text-gray-400">Storage Used</span>
                            </div>
                            <p class="text-3xl font-bold text-white" id="storageUsed">0 MB</p>
                            <p class="text-sm text-gray-400 mt-1">of 10 GB limit</p>
                        </div>
                        
                        <div class="glass-effect p-6 rounded-xl border border-gray-700">
                            <div class="flex items-center justify-between mb-4">
                                <div class="p-3 bg-purple-500/20 rounded-lg">
                                    <i data-lucide="calendar" class="w-6 h-6 text-purple-400"></i>
                                </div>
                                <span class="text-xs text-gray-400">Last Upload</span>
                            </div>
                            <p class="text-3xl font-bold text-white" id="lastUpload">Today</p>
                            <p class="text-sm text-gray-400 mt-1">2 hours ago</p>
                        </div>
                        
                        <div class="glass-effect p-6 rounded-xl border border-gray-700">
                            <div class="flex items-center justify-between mb-4">
                                <div class="p-3 bg-orange-500/20 rounded-lg">
                                    <i data-lucide="shield" class="w-6 h-6 text-orange-400"></i>
                                </div>
                                <span class="text-xs text-gray-400">Security</span>
                            </div>
                            <p class="text-3xl font-bold text-white">Active</p>
                            <p class="text-sm text-green-400 mt-1">Protected</p>
                        </div>
                    </div>
                    
                    <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                        <div class="lg:col-span-2">
                            <div class="glass-effect rounded-xl border border-gray-700 p-6">
                                <h3 class="text-lg font-semibold text-white mb-4 flex items-center gap-2">
                                    <i data-lucide="clock" class="w-5 h-5 text-blue-400"></i>
                                    Recent Documents
                                </h3>
                                <div id="recentDocuments" class="space-y-3">
                                    <!-- Recent docs injected here -->
                                </div>
                            </div>
                        </div>
                        
                        <div>
                            <div class="glass-effect rounded-xl border border-gray-700 p-6">
                                <h3 class="text-lg font-semibold text-white mb-4 flex items-center gap-2">
                                    <i data-lucide="pie-chart" class="w-5 h-5 text-blue-400"></i>
                                    Storage Distribution
                                </h3>
                                <div class="space-y-3">
                                    <div>
                                        <div class="flex justify-between text-sm mb-1">
                                            <span class="text-gray-300">Technical Docs</span>
                                            <span class="text-gray-400">45%</span>
                                        </div>
                                        <div class="w-full bg-gray-700 rounded-full h-2">
                                            <div class="bg-blue-500 h-2 rounded-full" style="width: 45%"></div>
                                        </div>
                                    </div>
                                    <div>
                                        <div class="flex justify-between text-sm mb-1">
                                            <span class="text-gray-300">Images</span>
                                            <span class="text-gray-400">25%</span>
                                        </div>
                                        <div class="w-full bg-gray-700 rounded-full h-2">
                                            <div class="bg-green-500 h-2 rounded-full" style="width: 25%"></div>
                                        </div>
                                    </div>
                                    <div>
                                        <div class="flex justify-between text-sm mb-1">
                                            <span class="text-gray-300">Certificates</span>
                                            <span class="text-gray-400">15%</span>
                                        </div>
                                        <div class="w-full bg-gray-700 rounded-full h-2">
                                            <div class="bg-purple-500 h-2 rounded-full" style="width: 15%"></div>
                                        </div>
                                    </div>
                                    <div>
                                        <div class="flex justify-between text-sm mb-1">
                                            <span class="text-gray-300">Others</span>
                                            <span class="text-gray-400">15%</span>
                                        </div>
                                        <div class="w-full bg-gray-700 rounded-full h-2">
                                            <div class="bg-gray-500 h-2 rounded-full" style="width: 15%"></div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Documents Section -->
                <div id="documentsSection" class="hidden animate-fade-in">
                    <div class="flex justify-between items-center mb-6">
                        <div class="flex gap-2">
                            <button onclick="setView('grid')" id="gridViewBtn" class="p-2 rounded-lg bg-blue-600 text-white">
                                <i data-lucide="grid" class="w-5 h-5"></i>
                            </button>
                            <button onclick="setView('list')" id="listViewBtn" class="p-2 rounded-lg bg-gray-800 text-gray-400 hover:text-white">
                                <i data-lucide="list" class="w-5 h-5"></i>
                            </button>
                        </div>
                        
                        <select id="sortSelect" onchange="sortDocuments()" class="bg-gray-800 border border-gray-700 text-white rounded-lg px-4 py-2 outline-none focus:border-blue-500">
                            <option value="newest">Newest First</option>
                            <option value="oldest">Oldest First</option>
                            <option value="name">Name (A-Z)</option>
                            <option value="size">Size (Large-Small)</option>
                        </select>
                    </div>
                    
                    <div id="documentsGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
                        <!-- Documents injected here -->
                    </div>
                    
                    <div id="emptyState" class="hidden text-center py-20">
                        <i data-lucide="folder-open" class="w-20 h-20 text-gray-600 mx-auto mb-4"></i>
                        <p class="text-gray-400 text-lg">No documents found</p>
                        <button onclick="showUploadModal()" class="mt-4 text-blue-400 hover:text-blue-300">Upload your first document</button>
                    </div>
                </div>

                <!-- Profile Section -->
                <div id="profileSection" class="hidden animate-fade-in">
                    <div class="max-w-4xl mx-auto">
                        <div class="glass-effect rounded-2xl border border-gray-700 overflow-hidden">
                            <div class="h-32 bg-gradient-to-r from-blue-600 to-purple-600"></div>
                            <div class="px-8 pb-8">
                                <div class="relative flex justify-between items-end -mt-12 mb-6">
                                    <img src="http://static.photos/technology/200x200/42" alt="Profile" class="w-24 h-24 rounded-2xl border-4 border-gray-900 shadow-xl">
                                    <button class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-lg text-sm transition-colors">
                                        Edit Profile
                                    </button>
                                </div>
                                
                                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                                    <div>
                                        <h2 class="text-2xl font-bold text-white mb-1">Chris Ororo Son</h2>
                                        <p class="text-blue-400 mb-4">Son of Yahweh's System Architect</p>
                                        
                                        <div class="space-y-3 text-gray-300">
                                            <div class="flex items-center gap-3">
                                                <i data-lucide="mail" class="w-5 h-5 text-gray-500"></i>
                                                <span>www.chrisokumu@gmail.com</span>
                                            </div>
                                            <div class="flex items-center gap-3">
                                                <i data-lucide="map-pin" class="w-5 h-5 text-gray-500"></i>
                                                <span>Ororo Son, CA</span>
                                            </div>
                                            <div class="flex items-center gap-3">
                                                <i data-lucide="building" class="w-5 h-5 text-gray-500"></i>
                                                <span>TechCorp Industries</span>
                                            </div>
                                        </div>
                                    </div>
                                    
                                    <div class="space-y-4">
                                        <h3 class="font-semibold text-white mb-3">Skills & Expertise</h3>
                                        <div class="flex flex-wrap gap-2">
                                            <span class="px-3 py-1 bg-blue-900/30 text-blue-300 rounded-full text-sm border border-blue-700/30">System Architecture</span>
                                            <span class="px-3 py-1 bg-purple-900/30 text-purple-300 rounded-full text-sm border border-purple-700/30">Cloud Computing</span>
                                            <span class="px-3 py-1 bg-green-900/30 text-green-300 rounded-full text-sm border border-green-700/30">Cybersecurity</span>
                                            <span class="px-3 py-1 bg-orange-900/30 text-orange-300 rounded-full text-sm border border-orange-700/30">DevOps</span>
                                            <span class="px-3 py-1 bg-pink-900/30 text-pink-300 rounded-full text-sm border border-pink-700/30">Network Admin</span>
                                        </div>
                                        
                                        <h3 class="font-semibold text-white mb-3 mt-6">Security Status</h3>
                                        <div class="flex items-center gap-2 text-green-400">
                                            <i data-lucide="check-circle" class="w-5 h-5"></i>
                                            <span>2FA Enabled</span>
                                        </div>
                                        <div class="flex items-center gap-2 text-green-400">
                                            <i data-lucide="check-circle" class="w-5 h-5"></i>
                                            <span>End-to-End Encryption Active</span>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </main>
    </div>

    <!-- Upload Modal -->
    <div id="uploadModal" class="hidden fixed inset-0 z-50 flex items-center justify-center bg-black/80 backdrop-blur-sm">
        <div class="glass-effect w-full max-w-2xl mx-4 rounded-2xl border border-gray-700 shadow-2xl">
            <div class="p-6 border-b border-gray-800 flex justify-between items-center">
                <h3 class="text-xl font-bold text-white flex items-center gap-2">
                    <i data-lucide="upload-cloud" class="w-6 h-6 text-blue-400"></i>
                    Upload Documents
                </h3>
                <button onclick="closeUploadModal()" class="text-gray-400 hover:text-white transition-colors">
                    <i data-lucide="x" class="w-6 h-6"></i>
                </button>
            </div>
            
            <div class="p-6">
                <div id="uploadArea" class="upload-area rounded-xl p-12 text-center cursor-pointer transition-all" onclick="document.getElementById('fileInput').click()">
                    <input type="file" id="fileInput" multiple class="hidden" onchange="handleFileSelect(event)">
                    <i data-lucide="cloud-upload" class="w-16 h-16 text-blue-400 mx-auto mb-4"></i>
                    <p class="text-lg text-white font-medium mb-2">Drop files here or click to browse</p>
                    <p class="text-sm text-gray-400">Support for PDF, DOC, Images, and Code files up to 50MB</p>
                </div>
                
                <div class="mt-6">
                    <label class="block text-sm font-medium text-gray-300 mb-2">Category</label>
                    <select id="uploadCategory" class="w-full bg-gray-800 border border-gray-700 text-white rounded-lg px-4 py-3 outline-none focus:border-blue-500">
                        <option value="technical">Technical Documentation</option>
                        <option value="certificates">Certificates & Diplomas</option>
                        <option value="projects">Project Files</option>
                        <option value="images">Images & Screenshots</option>
                        <option value="system">System Configuration</option>
                    </select>
                </div>
                
                <div id="uploadPreview" class="hidden mt-6 space-y-2 max-h-48 overflow-y-auto custom-scrollbar">
                    <!-- Upload previews injected here -->
                </div>
            </div>
            
            <div class="p-6 border-t border-gray-800 flex justify-end gap-3">
                <button onclick="closeUploadModal()" class="px-6 py-2 rounded-lg text-gray-300 hover:text-white hover:bg-gray-800 transition-all">
                    Cancel
                </button>
                <button onclick="confirmUpload()" class="px-6 py-2 bg-blue-600 hover:bg-blue-700 text-white rounded-lg transition-all flex items-center gap-2">
                    <i data-lucide="upload" class="w-5 h-5"></i>
                    Upload Files
                </button>
            </div>
        </div>
    </div>

    <!-- Document Preview Modal -->
    <div id="previewModal" class="hidden fixed inset-0 z-50 flex items-center justify-center bg-black/90 backdrop-blur-sm">
        <div class="glass-effect w-full max-w-4xl mx-4 rounded-2xl border border-gray-700 shadow-2xl max-h-[90vh] flex flex-col">
            <div class="p-6 border-b border-gray-800 flex justify-between items-center">
                <div class="flex items-center gap-3">
                    <div id="previewIcon" class="p-2 bg-blue-900/30 rounded-lg">
                        <i data-lucide="file" class="w-6 h-6 text-blue-400"></i>
                    </div>
                    <div>
                        <h3 id="previewTitle" class="text-xl font-bold text-white">Document Title</h3>
                        <p id="previewMeta" class="text-sm text-gray-400">2.4 MB • PDF • Uploaded today</p>
                    </div>
                </div>
                <div class="flex items-center gap-2">
                    <button onclick="downloadCurrentFile()" class="p-2 text-gray-400 hover:text-white hover:bg-gray-800 rounded-lg transition-all">
                        <i data-lucide="download" class="w-5 h-5"></i>
                    </button>
                    <button onclick="deleteCurrentFile()" class="p-2 text-gray-400 hover:text-red-400 hover:bg-red-900/20 rounded-lg transition-all">
                        <i data-lucide="trash-2" class="w-5 h-5"></i>
                    </button>
                    <button onclick="closePreviewModal()" class="p-2 text-gray-400 hover:text-white hover:bg-gray-800 rounded-lg transition-all">
                        <i data-lucide="x" class="w-6 h-6"></i>
                    </button>
                </div>
            </div>
            
            <div id="previewContent" class="flex-1 p-6 overflow-auto bg-gray-900/50 flex items-center justify-center">
                <!-- Content injected here -->
            </div>
        </div>
    </div>

    <script>
        // Initialize Lucide icons
        lucide.createIcons();
        
        // Data Storage
        let documents = JSON.parse(localStorage.getItem('itVaultDocs')) || [
            {
                id: 1,
                name: 'AWS_Solutions_Architect_Cert.pdf',
                type: 'pdf',
                size: 2450000,
                category: 'certificates',
                date: new Date(Date.now() - 86400000 * 2),
                content: 'data:application/pdf;base64,JVBERi0xLjQKJdPr6eEKMSAwIG9iago8PAovVHlwZSAvQ2F0YWxvZwovUGFnZXMgMiAwIFIKPj4KZW5kb2JqCjIgMCBvYmoKPDwKL1R5cGUgL1BhZ2VzCi9LaWRzIFszIDAgUl0KL0NvdW50IDEKPj4KZW5kb2JqCjMgMCBvYmoKPDwKL1R5cGUgL1BhZ2UKL1BhcmVudCAyIDAgUgovTWVkaWFCb3ggWzAgMCA2MTIgNzkyXQovQ29udGVudHMgNCAwIFIKPj4KZW5kb2JqCjQgMCBvYmoKPDwKL0xlbmd0aCA0NAo+PgpzdHJlYW0KQlQKL0YxIDEyIFRmCjEwMCA3MDAgVGQKKCBBV1MgQ2VydGlmaWNhdGlvbiApIFRqCkVUCmVuZHN0cmVhbQplbmRvYmoKNSAwIG9iago8PAovVHlwZSAvRm9udAovU3VidHlwZSAvVHlwZTEKL0Jhc2VGb250IC9IZWx2ZXRpY2EKPj4KZW5kb2JqCnhyZWYKMCA2CjAwMDAwMDAwMDAgNjU1MzUgZiAKMDAwMDAwMDAxMCAwMDAwMCBuIAowMDAwMDAwMDU5IDAwMDAwIG4gCjAwMDAwMDAxMDIgMDAwMDAgbiAKMDAwMDAwMDE4MSAwMDAwMCBuIAowMDAwMDAwMjc0IDAwMDAwIG4gCnRyYWlsZXIKPDwKL1NpemUgNgovUm9vdCAxIDAgUgo+PgpzdGFydHhyZWYKMzQyCiUlRU9G'
            },
            {
                id: 2,
                name: 'Network_Diagram_v2.png',
                type: 'image',
                size: 1840000,
                category: 'technical',
                date: new Date(Date.now() - 86400000 * 5),
                content: 'http://static.photos/technology/800x600/123'
            },
            {
                id: 3,
                name: 'Docker_Config.yml',
                type: 'code',
                size: 12000,
                category: 'system',
                date: new Date(Date.now() - 86400000 * 1),
                content: 'version: "3.8"\nservices:\n  web:\n    image: nginx:latest\n    ports:\n      - "80:80"\n    volumes:\n      - ./html:/usr/share/nginx/html'
            },
            {
                id: 4,
                name: 'Project_Proposal_2024.docx',
                type: 'doc',
                size: 340000,
                category: 'projects',
                date: new Date(Date.now() - 86400000 * 3),
                content: 'Project Proposal: Cloud Migration Strategy...'
            }
        ];
        
        let currentUser = null;
        let currentView = 'grid';
        let currentFilter = 'all';
        let selectedFiles = [];
        let currentPreviewId = null;
        
        // Hardcoded credentials
        const VALID_USERNAME = 'admin';
        const VALID_PASSWORD = 'TechSecure2024!';
        
        // Login functionality
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            if (username === VALID_USERNAME && password === VALID_PASSWORD) {
                currentUser = { username, name: 'Ororo Son', role: 'Senior IT Expert' };
                document.getElementById('loginScreen').classList.add('hidden');
                document.getElementById('app').classList.remove('hidden');
                
                // Check remember me
                if (document.getElementById('rememberMe').checked) {
                    localStorage.setItem('itVaultSession', JSON.stringify(currentUser));
                }
                
                initApp();
            } else {
                const errorDiv = document.getElementById('loginError');
                errorDiv.classList.remove('hidden');
                setTimeout(() => errorDiv.classList.add('hidden'), 3000);
            }
        });
        
        // Toggle password visibility
        document.getElementById('togglePassword').addEventListener('click', function() {
            const passwordInput = document.getElementById('password');
            const type = passwordInput.type === 'password' ? 'text' : 'password';
            passwordInput.type = type;
            this.innerHTML = type === 'password' ? '<i data-lucide="eye" class="w-5 h-5"></i>' : '<i data-lucide="eye-off" class="w-5 h-5"></i>';
            lucide.createIcons();
        });
        
        // Check for existing session
        window.addEventListener('load', function() {
            const session = localStorage.getItem('itVaultSession');
            if (session) {
                currentUser = JSON.parse(session);
                document.getElementById('loginScreen').classList.add('hidden');
                document.getElementById('app').classList.remove('hidden');
                initApp();
            }
        });
        
        function initApp() {
            updateStats();
            renderDocuments();
            renderRecentDocuments();
            lucide.createIcons();
        }
        
        function logout() {
            localStorage.removeItem('itVaultSession');
            location.reload();
        }
        
        // Navigation
        function showSection(section) {
            // Hide all sections
            document.getElementById('dashboardSection').classList.add('hidden');
            document.getElementById('documentsSection').classList.add('hidden');
            document.getElementById('profileSection').classList.add('hidden');
            
            // Remove active states
            document.querySelectorAll('.sidebar-link').forEach(link => link.classList.remove('active'));
            
            // Show selected section
            if (section === 'dashboard') {
                document.getElementById('dashboardSection').classList.remove('hidden');
                document.getElementById('pageTitle').textContent = 'Dashboard';
                event.target.classList.add('active');
                updateStats();
            } else if (section === 'documents') {
                document.getElementById('documentsSection').classList.remove('hidden');
                document.getElementById('pageTitle').textContent = 'All Documents';
                currentFilter = 'all';
                renderDocuments();
                event.target.classList.add('active');
            } else if (section === 'profile') {
                document.getElementById('profileSection').classList.remove('hidden');
                document.getElementById('pageTitle').textContent = 'Profile';
                event.target.classList.add('active');
            }
            
            lucide.createIcons();
        }
        
        function filterByCategory(category) {
            document.getElementById('dashboardSection').classList.add('hidden');
            document.getElementById('documentsSection').classList.remove('hidden');
            document.getElementById('profileSection').classList.add('hidden');
            document.getElementById('pageTitle').textContent = category.charAt(0).toUpperCase() + category.slice(1) + ' Files';
            
            currentFilter = category;
            renderDocuments();
            
            // Update sidebar active states
            document.querySelectorAll('.sidebar-link').forEach(link => link.classList.remove('active'));
            event.target.classList.add('active');
        }
        
        // Document Management
        function renderDocuments() {
            const grid = document.getElementById('documentsGrid');
            const emptyState = document.getElementById('emptyState');
            
            let filteredDocs = documents;
            if (currentFilter !== 'all') {
                filteredDocs = documents.filter(doc => doc.category === currentFilter);
            }
            
            // Search filter
            const searchTerm = document.getElementById('searchInput').value.toLowerCase();
            if (searchTerm) {
                filteredDocs = filteredDocs.filter(doc => doc.name.toLowerCase().includes(searchTerm));
            }
            
            document.getElementById('docCount').textContent = filteredDocs.length;
            
            if (filteredDocs.length === 0) {
                grid.innerHTML = '';
                emptyState.classList.remove('hidden');
                return;
            }
            
            emptyState.classList.add('hidden');
            
            if (currentView === 'grid') {
                grid.className = 'grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6';
                grid.innerHTML = filteredDocs.map(doc => `
                    <div class="file-card glass-effect rounded-xl p-6 border border-gray-700 cursor-pointer group" onclick="previewDocument(${doc.id})">
                        <div class="flex items-start justify-between mb-4">
                            <div class="p-3 bg-blue-900/30 rounded-lg group-hover:bg-blue-800/30 transition-colors">
                                ${getFileIcon(doc.type)}
                            </div>
                            <button onclick="event.stopPropagation(); deleteDocument(${doc.id})" class="text-gray-500 hover:text-red-400 transition-colors">
                                <i data-lucide="more-vertical" class="w-5 h-5"></i>
                            </button>
                        </div>
                        <h4 class="text-white font-medium mb-1 truncate" title="${doc.name}">${doc.name}</h4>
                        <p class="text-sm text-gray-400 mb-3">${formatFileSize(doc.size)} • ${formatDate(doc.date)}</p>
                        <div class="flex items-center justify-between">
                            <span class="text-xs px-2 py-1 bg-gray-800 text-gray-300 rounded capitalize">${doc.category}</span>
                            <i data-lucide="arrow-right" class="w-4 h-4 text-gray-600 group-hover:text-blue-400 transition-colors"></i>
                        </div>
                    </div>
                `).join('');
            } else {
                grid.className = 'flex flex-col gap-3';
                grid.innerHTML = filteredDocs.map(doc => `
                    <div class="file-card glass-effect rounded-xl p-4 border border-gray-700 cursor-pointer flex items-center gap-4 group" onclick="previewDocument(${doc.id})">
                        <div class="p-3 bg-blue-900/30 rounded-lg">
                            ${getFileIcon(doc.type)}
                        </div>
                        <div class="flex-1">
                            <h4 class="text-white font-medium mb-1">${doc.name}</h4>
                            <p class="text-sm text-gray-400">${doc.category} • ${formatFileSize(doc.size)}</p>
                        </div>
                        <span class="text-sm text-gray-500">${formatDate(doc.date)}</span>
                        <button onclick="event.stopPropagation(); deleteDocument(${doc.id})" class="p-2 text-gray-500 hover:text-red-400 hover:bg-red-900/20 rounded-lg transition-all">
                            <i data-lucide="trash-2" class="w-5 h-5"></i>
                        </button>
                    </div>
                `).join('');
            }
            
            lucide.createIcons();
        }
        
        function renderRecentDocuments() {
            const recentDocs = documents.slice(0, 5);
            const container = document.getElementById('recentDocuments');
            
            container.innerHTML = recentDocs.map(doc => `
                <div class="flex items-center gap-4 p-3 rounded-lg hover:bg-gray-800/50 transition-colors cursor-pointer group" onclick="previewDocument(${doc.id})">
                    <div class="p-2 bg-gray-800 rounded-lg">
                        ${getFileIcon(doc.type, 'w-5 h-5')}
                    </div>
                    <div class="flex-1 min-w-0">
                        <p class="text-white font-medium truncate">${doc.name}</p>
                        <p class="text-xs text-gray-500">${doc.category} • ${formatDate(doc.date)}</p>
                    </div>
                    <span class="text-xs text-gray-500">${formatFileSize(doc.size)}</span>
                </div>
            `).join('');
            
            lucide.createIcons();
        }
        
        function getFileIcon(type, classes = 'w-6 h-6') {
            const icons = {
                pdf: `<i data-lucide="file-text" class="${classes} text-red-400"></i>`,
                image: `<i data-lucide="image" class="${classes} text-green-400"></i>`,
                code: `<i data-lucide="code" class="${classes} text-blue-400"></i>`,
                doc: `<i data-lucide="file-type" class="${classes} text-blue-300"></i>`,
                default: `<i data-lucide="file" class="${classes} text-gray-400"></i>`
            };
            return icons[type] || icons.default;
        }
        
        function formatFileSize(bytes) {
            if (bytes === 0) return '0 Bytes';
            const k = 1024;
            const sizes = ['Bytes', 'KB', 'MB', 'GB'];
            const i = Math.floor(Math.log(bytes) / Math.log(k));
            return Math.round(bytes / Math.pow(k, i) * 100) / 100 + ' ' + sizes[i];
        }
        
        function formatDate(date) {
            const d = new Date(date);
            const now = new Date();
            const diff = now - d;
            
            if (diff < 86400000) return 'Today';
            if (diff < 172800000) return 'Yesterday';
            return d.toLocaleDateString();
        }
        
        function updateStats() {
            document.getElementById('totalFiles').textContent = documents.length;
            
            const totalSize = documents.reduce((acc, doc) => acc + doc.size, 0);
            document.getElementById('storageUsed').textContent = formatFileSize(totalSize);
        }
        
        function setView(view) {
            currentView = view;
            document.getElementById('gridViewBtn').className = view === 'grid' ? 'p-2 rounded-lg bg-blue-600 text-white' : 'p-2 rounded-lg bg-gray-800 text-gray-400 hover:text-white';
            document.getElementById('listViewBtn').className = view === 'list' ? 'p-2 rounded-lg bg-blue-600 text-white' : 'p-2 rounded-lg bg-gray-800 text-gray-400 hover:text-white';
            renderDocuments();
        }
        
        function searchDocuments() {
            renderDocuments();
        }
        
        function sortDocuments() {
            const sort = document.getElementById('sortSelect').value;
            
            if (sort === 'newest') {
                documents.sort((a, b) => new Date(b.date) - new Date(a.date));
            } else if (sort === 'oldest') {
                documents.sort((a, b) => new Date(a.date) - new Date(b.date));
            } else if (sort === 'name') {
                documents.sort((a, b) => a.name.localeCompare(b.name));
            } else if (sort === 'size') {
                documents.sort((a, b) => b.size - a.size);
            }
            
            renderDocuments();
        }
        
        // Upload functionality
        function showUploadModal() {
            document.getElementById('uploadModal').classList.remove('hidden');
            selectedFiles = [];
            updateUploadPreview();
        }
        
        function closeUploadModal() {
            document.getElementById('uploadModal').classList.add('hidden');
            document.getElementById('fileInput').value = '';
            selectedFiles = [];
        }
        
        // Drag and drop
        const uploadArea = document.getElementById('uploadArea');
        
        uploadArea.addEventListener('dragover', (e) => {
            e.preventDefault();
            uploadArea.classList.add('dragover');
        });
        
        uploadArea.addEventListener('dragleave', () => {
            uploadArea.classList.remove('dragover');
        });
        
        uploadArea.addEventListener('drop', (e) => {
            e.preventDefault();
            uploadArea.classList.remove('dragover');
            
            const files = Array.from(e.dataTransfer.files);
            processFiles(files);
        });
        
        function handleFileSelect(event) {
            const files = Array.from(event.target.files);
            processFiles(files);
        }
        
        function processFiles(files) {
            files.forEach(file => {
                const reader = new FileReader();
                reader.onload = function(e) {
                    selectedFiles.push({
                        name: file.name,
                        type: file.name.split('.').pop().toLowerCase(),
                        size: file.size,
                        content: e.target.result
                    });
                    updateUploadPreview();
                };
                
                if (file.type.startsWith('image/')) {
                    reader.readAsDataURL(file);
                } else {
                    reader.readAsText(file);
                }
            });
        }
        
        function updateUploadPreview() {
            const preview = document.getElementById('uploadPreview');
            if (selectedFiles.length > 0) {
                preview.classList.remove('hidden');
                preview.innerHTML = selectedFiles.map((file, index) => `
                    <div class="flex items-center justify-between p-3 bg-gray-800 rounded-lg">
                        <div class="flex items-center gap-3">
                            ${getFileIcon(file.type)}
                            <span class="text-white text-sm">${file.name}</span>
                            <span class="text-gray-500 text-xs">${formatFileSize(file.size)}</span>
                        </div>
                        <button onclick="removeSelectedFile(${index})" class="text-red-400 hover:text-red-300">
                            <i data-lucide="x" class="w-4 h-4"></i>
                        </button>
                    </div>
                `).join('');
                lucide.createIcons();
            } else {
                preview.classList.add('hidden');
            }
        }
        
        function removeSelectedFile(index) {
            selectedFiles.splice(index, 1);
            updateUploadPreview();
        }
        
        function confirmUpload() {
            if (selectedFiles.length === 0) return;
            
            const category = document.getElementById('uploadCategory').value;
            
            selectedFiles.forEach(file => {
                const newDoc = {
                    id: Date.now() + Math.random(),
                    name: file.name,
                    type: getFileType(file.name),
                    size: file.size,
                    category: category,
                    date: new Date(),
                    content: file.content
                };
                documents.unshift(newDoc);
            });
            
            localStorage.setItem('itVaultDocs', JSON.stringify(documents));
            closeUploadModal();
            updateStats();
            renderDocuments();
            renderRecentDocuments();
            
            // Show success notification
            showNotification(`${selectedFiles.length} file(s) uploaded successfully`);
        }
        
        function getFileType(filename) {
            const ext = filename.split('.').pop().toLowerCase();
            if (['pdf'].includes(ext)) return 'pdf';
            if (['jpg', 'jpeg', 'png', 'gif', 'webp'].includes(ext)) return 'image';
            if (['js', 'html', 'css', 'json', 'xml', 'yml', 'yaml', 'py', 'java', 'cpp', 'c'].includes(ext)) return 'code';
            if (['doc', 'docx', 'txt', 'rtf'].includes(ext)) return 'doc';
            return 'default';
        }
        
        // Document Preview
        function previewDocument(id) {
            const doc = documents.find(d => d.id === id);
            if (!doc) return;
            
            currentPreviewId = id;
            document.getElementById('previewTitle').textContent = doc.name;
            document.getElementById('previewMeta').textContent = `${formatFileSize(doc.size)} • ${doc.type.toUpperCase()} • ${formatDate(doc.date)}`;
            
            const content = document.getElementById('previewContent');
            const iconContainer = document.getElementById('previewIcon');
            
            iconContainer.innerHTML = getFileIcon(doc.type);
            lucide.createIcons();
            
            if (doc.type === 'image') {
                content.innerHTML = `<img src="${doc.content}" class="max-w-full max-h-[60vh] rounded-lg shadow-2xl" alt="${doc.name}">`;
            } else if (doc.type === 'code') {
                content.innerHTML = `
                    <div class="w-full max-w-3xl bg-gray-900 rounded-lg p-6 overflow-auto">
                        <pre class="text-green-400 font-mono text-sm whitespace-pre-wrap">${escapeHtml(doc.content)}</pre>
                    </div>
                `;
            } else {
                content.innerHTML = `
                    <div class="text-center">
                        ${getFileIcon(doc.type, 'w-24 h-24 mx-auto mb-4')}
                        <p class="text-gray-400 mb-4">Preview not available for this file type</p>
                        <button onclick="downloadCurrentFile()" class="bg-blue-600 hover:bg-blue-700 text-white px-6 py-2 rounded-lg flex items-center gap-2 mx-auto">
                            <i data-lucide="download" class="w-5 h-5"></i>
                            Download to View
                        </button>
                    </div>
                `;
                lucide.createIcons();
            }
            
            document.getElementById('previewModal').classList.remove('hidden');
        }
        
        function closePreviewModal() {
            document.getElementById('previewModal').classList.add('hidden');
            currentPreviewId = null;
        }
        
        function downloadCurrentFile() {
            const doc = documents.find(d => d.id === currentPreviewId);
            if (!doc) return;
            
            const element = document.createElement('a');
            element.setAttribute('href', doc.content);
            element.setAttribute('download', doc.name);
            element.style.display = 'none';
            document.body.appendChild(element);
            element.click();
            document.body.removeChild(element);
        }
        
        function deleteCurrentFile() {
            if (!currentPreviewId) return;
            deleteDocument(currentPreviewId);
            closePreviewModal();
        }
        
        function deleteDocument(id) {
            if (!confirm('Are you sure you want to delete this document?')) return;
            
            documents = documents.filter(d => d.id !== id);
            localStorage.setItem('itVaultDocs', JSON.stringify(documents));
            renderDocuments();
            updateStats();
            showNotification('Document deleted successfully');
        }
        
        function escapeHtml(text) {
            const div = document.createElement('div');
            div.textContent = text;
            return div.innerHTML;
        }
        
        function showNotification(message) {
            const notification = document.createElement('div');
            notification.className = 'fixed bottom-4 right-4 bg-green-600 text-white px-6 py-3 rounded-lg shadow-xl flex items-center gap-2 z-50 animate-fade-in';
            notification.innerHTML = `
                <i data-lucide="check-circle" class="w-5 h-5"></i>
                <span>${message}</span>
            `;
            document.body.appendChild(notification);
            lucide.createIcons();
            
            setTimeout(() => {
                notification.remove();
            }, 3000);
        }
        
        // Close modals on escape key
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape') {
                closeUploadModal();
                closePreviewModal();
            }
        });
    </script>
</body>
</html>
