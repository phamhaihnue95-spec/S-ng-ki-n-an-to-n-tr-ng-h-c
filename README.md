<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Blue Flow - Góc Xanh | Nơi tiếng nói được bảo vệ</title>
    <!-- Tích hợp Tailwind CSS qua CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Tích hợp Font chữ Nunito mang lại cảm giác thân thiện, học đường -->
    <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Nunito', sans-serif;
        }
        /* Hiệu ứng scroll mượt */
        html {
            scroll-behavior: smooth;
        }
        /* Lớp CSS dùng để nháy màu đáp án */
        .correct-answer {
            background-color: #22c55e !important; /* Xanh lá */
            color: white !important;
            border-color: #22c55e !important;
        }
        .wrong-answer {
            background-color: #ef4444 !important; /* Đỏ */
            color: white !important;
            border-color: #ef4444 !important;
        }
        .disabled-btn {
            pointer-events: none;
            opacity: 0.8;
        }
        /* Thêm hiệu ứng nhấp nháy thu hút sự chú ý cho nút hướng dẫn */
        @keyframes pulse-fast {
            0%, 100% {
                transform: scale(1);
                box-shadow: 0 0 0 0 rgba(225, 29, 72, 0.4);
            }
            50% {
                transform: scale(1.03);
                box-shadow: 0 0 0 8px rgba(225, 29, 72, 0);
            }
        }
        .animate-pulse-fast {
            animation: pulse-fast 1.5s infinite;
        }
    </style>
</head>
<body class="bg-slate-50 text-gray-800 flex flex-col min-h-screen">

    <!-- Top Bar -->
    <div class="bg-slate-800 text-white py-2 px-4 text-center z-50">
        <div class="max-w-7xl mx-auto text-xs md:text-sm">
            <p class="font-bold mb-1">Dự án Blue Flow 🌊 <span class="font-normal hidden md:inline">| Sáng kiến phòng chống bạo lực học đường - An toàn, Tích cực, Yêu thương.</span></p>
            <p class="font-normal md:hidden mb-1 text-[11px]">Sáng kiến phòng chống bạo lực học đường - An toàn, Tích cực, Yêu thương.</p>
            <p class="text-gray-300 text-[10px] md:text-xs mt-1 border-t border-slate-700 pt-1 inline-block">
                &copy; 2024 Bản quyền thuộc về học sinh Nguyễn Sương Nguyệt Minh - Lớp 6A1, Trường THCS Trương Công Giai.
                <span class="hidden md:inline"> | </span><br class="md:hidden">
                Giáo viên cố vấn: Cô Phạm Thị Hải
            </p>
        </div>
    </div>

    <!-- Header -->
    <nav class="bg-white shadow-sm sticky top-0 z-40">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16 items-center">
                <div class="flex-shrink-0 flex items-center cursor-pointer" onclick="window.scrollTo(0,0)">
                    <span class="text-2xl font-extrabold text-blue-600 tracking-tight">Blue Flow <span class="text-3xl">🌊</span></span>
                </div>
                <!-- Cập nhật Menu: Thêm màu nền, chữ cho từng nút và hiệu ứng nhấp nháy -->
                <div class="hidden lg:flex gap-1 xl:gap-3 items-center">
                    <a href="#" class="text-blue-600 hover:bg-blue-100 px-3 py-2 rounded-xl font-bold transition whitespace-nowrap">Trang chủ</a>
                    <a href="#sos-section" class="bg-red-100 text-red-700 hover:bg-red-200 px-4 py-2 rounded-full font-bold transition whitespace-nowrap shadow-sm">Gửi Báo Cáo SOS</a>
                    <a href="#skills-section" class="text-green-600 hover:bg-green-100 px-3 py-2 rounded-xl font-bold transition whitespace-nowrap">Góc Kỹ Năng</a>
                    <a href="#feedback-section" class="text-amber-600 hover:bg-amber-100 px-3 py-2 rounded-xl font-bold transition whitespace-nowrap">Góp Ý & Đánh Giá</a>
                    <a href="https://drive.google.com/file/d/1lZcGnlI9YjdyT8Wqcm94G2jn73Vvo03Z/view?usp=sharing" target="_blank" class="text-purple-600 hover:bg-purple-100 px-3 py-2 rounded-xl font-bold transition flex items-center gap-1 whitespace-nowrap">
                        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"></path></svg>
                        Tài Liệu
                    </a>
                    <a href="https://youtu.be/Q7Y5aW3cdC8" target="_blank" id="guideBtn" class="bg-rose-50 border border-rose-200 text-rose-600 hover:bg-rose-100 px-4 py-2 rounded-full font-bold transition flex items-center gap-1 whitespace-nowrap shadow-sm animate-pulse-fast">
                        <svg class="w-4 h-4 text-red-500" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM9.555 7.168A1 1 0 008 8v4a1 1 0 001.555.832l3-2a1 1 0 000-1.664l-3-2z" clip-rule="evenodd" /></svg>
                        Hướng dẫn sử dụng Web
                    </a>
                </div>
                <div class="lg:hidden flex items-center">
                    <button class="text-gray-600 hover:text-blue-600 focus:outline-none">
                        <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7" />
                        </svg>
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <header class="bg-gradient-to-b from-blue-500 to-cyan-300 text-white py-20 px-4 text-center">
        <div class="max-w-4xl mx-auto">
            <h1 class="text-4xl md:text-5xl font-extrabold mb-6 leading-tight drop-shadow-md">
                Nơi tiếng nói của bạn được bảo vệ.
            </h1>
            <p class="text-lg md:text-xl mb-10 font-medium opacity-90 drop-shadow-sm max-w-2xl mx-auto">
                Bạn không đơn độc tại THCS Trương Công Giai.<br class="hidden md:block"> Hãy lên tiếng để bảo vệ chính mình và bạn bè.
            </p>
            <div class="flex flex-col sm:flex-row justify-center items-center gap-4">
                <a href="#sos-section" class="w-full sm:w-auto bg-orange-500 hover:bg-orange-600 text-white font-bold py-3 px-8 rounded-full shadow-lg transition transform hover:-translate-y-1">
                    Gửi Báo Cáo SOS
                </a>
                <a href="#skills-section" class="w-full sm:w-auto bg-white text-blue-600 hover:bg-gray-100 font-bold py-3 px-8 rounded-full shadow-lg transition transform hover:-translate-y-1">
                    Khám phá Kỹ Năng
                </a>
            </div>
        </div>
    </header>

    <!-- Nội dung chính -->
    <main class="flex-grow max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12 w-full">
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-10">
            
            <!-- Hộp thư SOS -->
            <section id="sos-section" class="lg:col-span-5 bg-blue-50 rounded-3xl p-6 md:p-8 shadow-sm border border-blue-100">
                <div class="text-center mb-6">
                    <h2 class="text-2xl font-extrabold text-blue-800">Gửi Báo Cáo SOS Ẩn danh</h2>
                    <p class="text-gray-600 mt-1 font-medium">Báo Cáo An Toàn. Ẩn Danh Hoàn Toàn.</p>
                </div>

                <form id="sosForm" class="space-y-5">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-sm font-bold text-gray-700 mb-1">Vấn đề bạn gặp phải?</label>
                            <select id="issue" required class="w-full px-4 py-2.5 rounded-xl border border-gray-300 focus:ring-2 focus:ring-blue-400 focus:border-blue-400 outline-none bg-white text-gray-700">
                                <option value="" disabled selected>Chọn vấn đề...</option>
                                <option value="the_chat">Bạo lực thể chất</option>
                                <option value="loi_noi">Bắt nạt bằng lời nói</option>
                                <option value="co_lap">Tẩy chay/Cô lập</option>
                                <option value="mang">Bạo lực mạng (Cyberbullying)</option>
                                <option value="khac">Khác</option>
                            </select>
                        </div>
                        <div>
                            <label class="block text-sm font-bold text-gray-700 mb-1">Mức độ khẩn cấp?</label>
                            <select id="urgency" required class="w-full px-4 py-2.5 rounded-xl border border-gray-300 focus:ring-2 focus:ring-blue-400 focus:border-blue-400 outline-none bg-white text-gray-700">
                                <option value="" disabled selected>Chọn mức độ...</option>
                                <option value="thap">Thấp</option>
                                <option value="trung_binh">Trung bình</option>
                                <option value="nguy_hiem" class="text-red-600 font-bold">Nguy hiểm (Cần can thiệp ngay)</option>
                            </select>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-sm font-bold text-gray-700 mb-1">Họ và tên (Tùy chọn)</label>
                            <input type="text" id="fullName" placeholder="Nhập tên của bạn..." class="w-full px-4 py-2.5 rounded-xl border border-gray-300 focus:ring-2 focus:ring-blue-400 focus:border-blue-400 outline-none bg-white text-gray-700">
                        </div>
                        <div>
                            <label class="block text-sm font-bold text-gray-700 mb-1">Lớp (Tùy chọn)</label>
                            <input type="text" id="className" placeholder="VD: 6A1..." class="w-full px-4 py-2.5 rounded-xl border border-gray-300 focus:ring-2 focus:ring-blue-400 focus:border-blue-400 outline-none bg-white text-gray-700">
                        </div>
                    </div>

                    <div>
                        <label class="block text-sm font-bold text-gray-700 mb-1">Chi tiết sự việc</label>
                        <textarea id="details" required rows="4" placeholder="Bạn muốn kể lại chuyện gì đã xảy ra?" class="w-full px-4 py-3 rounded-xl border border-gray-300 focus:ring-2 focus:ring-blue-400 focus:border-blue-400 outline-none bg-white text-gray-700 resize-none"></textarea>
                    </div>

                    <div>
                        <label class="block text-sm font-bold text-gray-700 mb-1">Hình ảnh/Bằng chứng (Nếu có)</label>
                        <input type="file" accept="image/*" class="w-full text-sm text-gray-500 file:mr-4 file:py-2 file:px-4 file:rounded-full file:border-0 file:text-sm file:font-semibold file:bg-blue-100 file:text-blue-700 hover:file:bg-blue-200 cursor-pointer">
                    </div>

                    <div>
                        <label class="block text-sm font-bold text-gray-700 mb-2">Bạn là ai trong chuyện này?</label>
                        <div class="flex items-center space-x-6">
                            <label class="flex items-center cursor-pointer">
                                <input type="radio" name="role" value="nan_nhan" required class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500">
                                <span class="ml-2 text-gray-700 font-medium">Nạn nhân</span>
                            </label>
                            <label class="flex items-center cursor-pointer">
                                <input type="radio" name="role" value="chung_kien" class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500">
                                <span class="ml-2 text-gray-700 font-medium">Người chứng kiến</span>
                            </label>
                        </div>
                    </div>

                    <button type="submit" class="w-full bg-white border-2 border-blue-200 text-blue-600 font-extrabold text-lg py-3 rounded-xl hover:bg-blue-50 focus:ring-4 focus:ring-blue-200 transition shadow-sm mt-4">
                        Gửi Báo Cáo Ẩn Danh
                    </button>
                    <p class="text-xs text-center text-gray-500 mt-2">Thông tin của bạn được mã hóa an toàn 100%.</p>
                </form>
            </section>

            <!-- Góc Kỹ Năng -->
            <section id="skills-section" class="lg:col-span-7 flex flex-col justify-center">
                <div class="text-center mb-8">
                    <h2 class="text-2xl font-extrabold text-gray-800">Góc Kỹ Năng</h2>
                    <p class="text-gray-600 mt-1 font-medium">Trang bị Kỹ Năng & Lan Tỏa Tình Bạn</p>
                </div>

                <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
                    
                    <!-- Card Đặc biệt: Trạm Trợ Lý Ảo AI -->
                    <div class="sm:col-span-2 bg-gradient-to-r from-blue-600 via-indigo-600 to-purple-600 rounded-3xl shadow-lg hover:shadow-2xl transition-all duration-300 overflow-hidden flex flex-col md:flex-row transform hover:-translate-y-1 ring-4 ring-purple-200">
                        <!-- Icon khu vực AI -->
                        <div class="md:w-1/3 flex items-center justify-center p-8 bg-white bg-opacity-10 backdrop-blur-sm border-b md:border-b-0 md:border-r border-white border-opacity-20">
                            <span class="text-7xl drop-shadow-xl animate-pulse">🤖✨</span>
                        </div>
                        <!-- Nội dung Text & Nút bấm -->
                        <div class="p-6 md:p-8 flex-grow flex flex-col justify-center text-left">
                            <h3 class="font-extrabold text-2xl text-white mb-3 drop-shadow-sm">Trợ lý Ảo Cố Vấn Tâm Lý AI</h3>
                            <p class="text-blue-50 text-sm md:text-base mb-6 leading-relaxed opacity-90">
                                Bạn đang bối rối không biết xử lý sao với một tình huống khó nói? Hãy nhấn nút bên dưới để trò chuyện trực tiếp với Trợ lý AI thông minh của Blue Flow. Hoàn toàn bảo mật và khách quan!
                            </p>
                            <div>
                                <a href="https://gemini.google.com/share/30cab447510a" target="_blank" class="inline-flex items-center justify-center font-extrabold text-indigo-700 bg-white hover:bg-indigo-50 py-3 px-8 rounded-full transition-all duration-300 shadow-[0_0_15px_rgba(255,255,255,0.4)] hover:shadow-[0_0_25px_rgba(255,255,255,0.8)] hover:scale-105">
                                    <svg class="w-5 h-5 mr-2 text-purple-600" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-8-3a1 1 0 00-.867.5 1 1 0 11-1.731-1A3 3 0 0113 8a3.001 3.001 0 01-2 2.83V11a1 1 0 11-2 0v-1a1 1 0 011-1 1 1 0 100-2zm0 8a1 1 0 100-2 1 1 0 000 2z" clip-rule="evenodd" /></svg>
                                    Trò chuyện với AI ngay
                                </a>
                            </div>
                        </div>
                    </div>

                    <!-- Card 1 -->
                    <div class="bg-white rounded-2xl shadow-sm border border-gray-100 hover:shadow-md transition overflow-hidden flex flex-col h-full transform hover:-translate-y-1">
                        <div class="h-32 bg-red-50 flex items-center justify-center text-5xl">
                            📱🚫
                        </div>
                        <div class="p-4 flex-grow flex flex-col justify-between text-center">
                            <div>
                                <h3 class="font-bold text-gray-800 mb-2 leading-tight">Nhận diện Cyberbullying & Cách chặn đứng</h3>
                                <p class="text-xs text-gray-500 mb-4">Bảo vệ bản thân khỏi những lời lẽ tiêu cực trên mạng xã hội.</p>
                            </div>
                            <a href="https://www.youtube.com/watch?v=S_Av1erAjxs" target="_blank" class="inline-flex items-center justify-center text-sm font-bold text-red-600 hover:text-red-700 bg-red-50 hover:bg-red-100 py-2 rounded-xl transition mt-auto">
                                <svg class="w-5 h-5 mr-1.5" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM9.555 7.168A1 1 0 008 8v4a1 1 0 001.555.832l3-2a1 1 0 000-1.664l-3-2z" clip-rule="evenodd" /></svg>
                                Xem Video
                            </a>
                        </div>
                    </div>

                    <!-- Card 2 -->
                    <div class="bg-white rounded-2xl shadow-sm border border-gray-100 hover:shadow-md transition overflow-hidden flex flex-col h-full transform hover:-translate-y-1">
                        <div class="h-32 bg-green-50 flex items-center justify-center text-5xl">
                            🧠🧘‍♂️
                        </div>
                        <div class="p-4 flex-grow flex flex-col justify-between text-center">
                            <div>
                                <h3 class="font-bold text-gray-800 mb-2 leading-tight">Quản Lý Cơn Giận Khoa Học</h3>
                                <p class="text-xs text-gray-500 mb-4">Hãy cùng Dr. Binocs khám phá cách não bộ và các hormone điều khiển cảm xúc, từ đó học cách 'hạ nhiệt' thông minh nhé!</p>
                            </div>
                            <a href="https://www.youtube.com/watch?v=iGx8LKqt0k0" target="_blank" class="inline-flex items-center justify-center text-sm font-bold text-green-600 hover:text-green-700 bg-green-50 hover:bg-green-100 py-2 rounded-xl transition mt-auto">
                                <svg class="w-5 h-5 mr-1.5" fill="currentColor" viewBox="0 0 20 20">
                                    <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM9.555 7.168A1 1 0 008 8v4a1 1 0 001.555.832l3-2a1 1 0 000-1.664l-3-2z" clip-rule="evenodd" />
                                </svg>
                                Xem Video
                            </a>
                        </div>
                    </div>

                    <!-- Card 3: Thử Thách Đại Sứ Xanh -->
                    <div class="bg-white rounded-2xl shadow-sm border border-blue-200 hover:shadow-md transition overflow-hidden flex flex-col h-full transform hover:-translate-y-1 ring-2 ring-blue-100">
                        <div class="h-32 bg-blue-50 flex items-center justify-center text-5xl">
                            🏆🎮
                        </div>
                        <div class="p-4 flex-grow flex flex-col justify-between text-center">
                            <div>
                                <h3 class="font-bold text-blue-800 mb-2 leading-tight">Thử Thách Đại Sứ Xanh</h3>
                                <p class="text-xs text-gray-500 mb-4">Tham gia trả lời 15 câu hỏi tình huống và nhận ngay Giấy chứng nhận!</p>
                            </div>
                            <button onclick="openQuizModal()" class="w-full inline-flex items-center justify-center text-sm font-bold text-white bg-blue-600 hover:bg-blue-700 py-2 rounded-xl transition mt-auto shadow-md">
                                Tham gia ngay
                            </button>
                        </div>
                    </div>

                    <!-- Card 4: Tài Liệu Tham Khảo -->
                    <div class="bg-white rounded-2xl shadow-sm border border-purple-100 hover:shadow-md transition overflow-hidden flex flex-col h-full transform hover:-translate-y-1 ring-1 ring-purple-50">
                        <div class="h-32 bg-purple-50 flex items-center justify-center text-5xl">
                            📖📚
                        </div>
                        <div class="p-4 flex-grow flex flex-col justify-between text-center">
                            <div>
                                <h3 class="font-bold text-purple-800 mb-2 leading-tight">Tài Liệu Tham Khảo</h3>
                                <p class="text-xs text-gray-500 mb-4">Cẩm nang kiến thức và tài liệu phòng chống bạo lực học đường.</p>
                            </div>
                            <div class="flex flex-col gap-2 mt-auto">
                                <a href="https://drive.google.com/file/d/1lZcGnlI9YjdyT8Wqcm94G2jn73Vvo03Z/view?usp=sharing" target="_blank" class="w-full inline-flex items-center justify-center text-sm font-bold text-purple-700 bg-purple-100 hover:bg-purple-200 py-2 rounded-xl transition shadow-sm">
                                    <svg class="w-5 h-5 mr-1.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"></path></svg>
                                    Bảo vệ bản thân
                                </a>
                                <a href="https://drive.google.com/file/d/1Bgz3NQEMSD2q27kt5XhCAdAktSaa97_2/view?usp=sharing" target="_blank" class="w-full inline-flex items-center justify-center text-sm font-bold text-purple-700 bg-purple-50 border border-purple-200 hover:bg-purple-100 py-2 rounded-xl transition shadow-sm">
                                    <svg class="w-5 h-5 mr-1.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"></path></svg>
                                    Làm chủ cơn giận
                                </a>
                            </div>
                        </div>
                    </div>

                </div>
            </section>

        </div>
    </main>

    <!-- Khu vực Góp Ý & Đánh Giá (MỚI) -->
    <section id="feedback-section" class="bg-white py-16 border-t border-gray-200">
        <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
            <h2 class="text-3xl font-extrabold text-gray-800 mb-3">Lắng Nghe Để Hoàn Thiện Hơn</h2>
            <p class="text-gray-600 mb-8 font-medium">Mọi ý kiến đóng góp ẩn danh của bạn đều là viên gạch quý giá giúp xây dựng Góc Xanh an toàn và tuyệt vời hơn. Hãy dành 2 phút để đánh giá nhé!</p>

            <!-- Khung Iframe hiển thị Google Form -->
            <div class="bg-slate-50 rounded-2xl shadow-xl border border-gray-100 overflow-hidden w-full relative h-[800px]">
                <iframe 
                    src="https://docs.google.com/forms/d/e/1FAIpQLScckUeGCp-tYS_poHHHTvRfklf97EzQpn27CUPiOW6Mk_wTwg/viewform?embedded=true" 
                    width="100%" 
                    height="100%" 
                    frameborder="0" 
                    marginheight="0" 
                    marginwidth="0" 
                    class="absolute inset-0 w-full h-full">
                    Đang tải…
                </iframe>
            </div>
        </div>
    </section>

    <!-- Khu vực Quản Trị Giáo Viên -->
    <section id="admin-section" class="bg-slate-200 py-12 border-t border-gray-300">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex flex-col md:flex-row justify-between items-center mb-6 gap-4">
                <div>
                    <h2 class="text-2xl font-extrabold text-gray-800">Khu Vực Quản Trị</h2>
                    <p class="text-gray-600 font-medium">Dành cho Giáo Viên Chủ Nhiệm</p>
                </div>
                <div class="flex items-center gap-3">
                    <!-- Nút xóa thư rác (ẩn mặc định) -->
                    <button id="clearTrashBtn" onclick="handleClearTrash()" class="hidden bg-gray-100 border border-gray-300 text-gray-400 font-bold py-3 px-4 rounded-xl shadow-sm transition items-center gap-2 cursor-not-allowed opacity-70" title="Tự động kích hoạt khi đạt 1000 thư">
                        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"></path></svg>
                        <span id="trashCount" class="hidden md:inline">0/1000</span>
                    </button>
                    <!-- Nút Tải CSV -->
                    <button id="exportCsvBtn" class="hidden bg-green-500 hover:bg-green-600 text-white font-bold py-3 px-6 rounded-xl shadow-lg transition transform hover:-translate-y-1 items-center gap-2">
                        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4"></path></svg>
                        Tải danh sách
                    </button>
                </div>
            </div>

            <div id="adminLogin" class="bg-white rounded-2xl shadow-sm border border-gray-200 p-8 max-w-md mx-auto text-center my-8">
                <div class="text-4xl mb-4">🔐</div>
                <h3 class="text-lg font-bold text-gray-800 mb-2">Xác Thực Quyền Truy Cập</h3>
                <p class="text-gray-600 text-sm mb-6">Vui lòng xác thực quyền giáo viên để xem dữ liệu.</p>
                <input type="email" id="teacherEmail" placeholder="Nhập email giáo viên..." class="w-full px-4 py-3 rounded-xl border border-gray-300 focus:ring-2 focus:ring-blue-400 focus:border-blue-400 outline-none mb-4 text-gray-700">
                <button id="authBtn" class="w-full bg-slate-800 hover:bg-slate-900 text-white font-bold py-3 rounded-xl transition shadow-md">
                    Xác thực
                </button>
                <p id="authError" class="text-red-500 text-sm mt-3 hidden font-medium">Tài khoản không hợp lệ. Khu vực này chỉ dành cho Giáo viên chủ nhiệm!</p>
                <p id="authSuccessMsg" class="text-green-600 text-sm mt-3 hidden font-bold">Đã tải danh sách thành công. Hệ thống tự động khóa để bảo mật!</p>
            </div>
            
            <div id="adminTableContainer" class="hidden bg-white rounded-2xl shadow-sm border border-gray-200 overflow-hidden">
                <div class="overflow-x-auto">
                    <table class="min-w-full divide-y divide-gray-200">
                        <thead class="bg-gray-50">
                            <tr>
                                <th scope="col" class="px-6 py-4 text-left text-xs font-bold text-gray-500 uppercase tracking-wider">Thời gian</th>
                                <th scope="col" class="px-6 py-4 text-left text-xs font-bold text-gray-500 uppercase tracking-wider">Người báo cáo</th>
                                <th scope="col" class="px-6 py-4 text-left text-xs font-bold text-gray-500 uppercase tracking-wider">Vấn đề</th>
                                <th scope="col" class="px-6 py-4 text-left text-xs font-bold text-gray-500 uppercase tracking-wider">Mức độ</th>
                                <th scope="col" class="px-6 py-4 text-left text-xs font-bold text-gray-500 uppercase tracking-wider">Chi tiết sự việc</th>
                            </tr>
                        </thead>
                        <tbody id="reportTableBody" class="bg-white divide-y divide-gray-200">
                            <tr>
                                <td colspan="5" class="px-6 py-8 text-center text-gray-500 font-medium">Chưa có báo cáo nào được ghi nhận.</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </section>

    <!-- Modal Form Gửi Thành Công -->
    <div id="successModal" class="fixed inset-0 bg-black bg-opacity-50 z-[100] hidden flex items-center justify-center backdrop-blur-sm transition-opacity">
        <div class="bg-white rounded-2xl shadow-2xl p-8 max-w-sm w-full mx-4 transform transition-all text-center">
            <div class="mx-auto flex items-center justify-center h-16 w-16 rounded-full bg-green-100 mb-6">
                <svg class="h-10 w-10 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
            </div>
            <h3 class="text-xl font-extrabold text-gray-900 mb-2">Gửi thành công!</h3>
            <p class="text-gray-600 mb-6">Cảm ơn bạn đã dũng cảm lên tiếng. Thông tin của bạn đã được mã hóa và gửi tới Ban cố vấn!</p>
            <button onclick="closeModal()" class="w-full bg-blue-600 hover:bg-blue-700 text-white font-bold py-3 rounded-xl transition focus:outline-none focus:ring-4 focus:ring-blue-300">Đóng thông báo</button>
        </div>
    </div>

    <!-- Modal Thông báo Dọn dẹp Thư rác -->
    <div id="trashModal" class="fixed inset-0 bg-black bg-opacity-50 z-[100] hidden flex items-center justify-center backdrop-blur-sm transition-opacity">
        <div class="bg-white rounded-2xl shadow-2xl p-8 max-w-sm w-full mx-4 transform transition-all text-center">
            <div class="mx-auto flex items-center justify-center h-16 w-16 rounded-full bg-red-100 mb-6">
                <svg class="h-10 w-10 text-red-600" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"></path></svg>
            </div>
            <h3 class="text-xl font-extrabold text-gray-900 mb-2">Đã dọn dẹp hệ thống!</h3>
            <p class="text-gray-600 mb-6">Bạn đã đọc thư. Hệ thống đã tự động xóa 1000 báo cáo cũ nhất để giải phóng dung lượng.</p>
            <button onclick="closeTrashModal()" class="w-full bg-slate-800 hover:bg-slate-900 text-white font-bold py-3 rounded-xl transition focus:outline-none focus:ring-4 focus:ring-slate-300">Đóng thông báo</button>
        </div>
    </div>

    <!-- Modal Quiz Thử Thách Đại Sứ Xanh -->
    <div id="quizModal" class="fixed inset-0 bg-black bg-opacity-70 z-[110] hidden flex items-center justify-center backdrop-blur-sm transition-opacity">
        <div class="bg-white rounded-3xl shadow-2xl p-6 md:p-8 max-w-2xl w-full mx-4 transform transition-all relative flex flex-col max-h-[90vh]">
            
            <!-- Nút đóng Quiz -->
            <button onclick="closeQuizModal()" class="absolute top-4 right-4 text-gray-400 hover:text-gray-700 focus:outline-none">
                <svg class="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" /></svg>
            </button>

            <!-- Màn hình 1: Nhập thông tin -->
            <div id="quizIntro" class="text-center py-4 overflow-y-auto">
                <div class="text-6xl mb-4">🏆</div>
                <h2 class="text-3xl font-extrabold text-blue-800 mb-2">Thử Thách Đại Sứ Xanh</h2>
                <p class="text-gray-600 mb-8 font-medium">Trả lời 15 câu hỏi tình huống để nhận Giấy Chứng Nhận từ dự án Blue Flow nhé!</p>
                
                <div class="space-y-4 max-w-sm mx-auto text-left">
                    <div>
                        <label class="block text-sm font-bold text-gray-700 mb-1">Họ và Tên của bạn</label>
                        <input type="text" id="quizName" placeholder="Ví dụ: Nguyễn Văn A..." class="w-full px-4 py-3 rounded-xl border border-gray-300 focus:ring-2 focus:ring-blue-400 outline-none text-gray-700">
                    </div>
                    <div>
                        <label class="block text-sm font-bold text-gray-700 mb-1">Lớp</label>
                        <input type="text" id="quizClass" placeholder="Ví dụ: 6A1..." class="w-full px-4 py-3 rounded-xl border border-gray-300 focus:ring-2 focus:ring-blue-400 outline-none text-gray-700">
                    </div>
                    <button onclick="startQuiz()" class="w-full bg-blue-600 hover:bg-blue-700 text-white font-extrabold text-lg py-3 rounded-xl transition shadow-lg mt-6">
                        BẮT ĐẦU CHƠI
                    </button>
                </div>
            </div>

            <!-- Màn hình 2: Đang chơi -->
            <div id="quizPlay" class="hidden flex-col h-full overflow-y-auto pb-2">
                <div class="flex justify-between items-center mb-6 border-b pb-4">
                    <span id="quizProgress" class="text-sm font-bold text-blue-600 bg-blue-100 px-3 py-1 rounded-full">Câu 1/15</span>
                    <span class="text-sm font-bold text-gray-500">Điểm: <span id="quizScoreDisplay" class="text-orange-500">0</span></span>
                </div>
                
                <h3 id="questionText" class="text-xl md:text-2xl font-bold text-gray-800 mb-8 leading-snug">
                    Nội dung câu hỏi sẽ nằm ở đây?
                </h3>
                
                <!-- Khu vực chứa 4 nút đáp án -->
                <div id="optionsContainer" class="grid grid-cols-1 gap-3 flex-grow">
                    <!-- Các nút sinh ra bằng JS -->
                </div>
            </div>

            <!-- Màn hình 3: Kết quả -->
            <div id="quizResult" class="hidden text-center py-8 overflow-y-auto">
                <div class="text-7xl mb-4" id="resultEmoji">🎉</div>
                <h2 class="text-3xl font-extrabold text-gray-900 mb-2">Hoàn Thành Thử Thách!</h2>
                <p class="text-lg text-gray-600 mb-6">Bạn đã đạt được: <span id="finalScore" class="font-extrabold text-blue-600 text-2xl">0/15</span> điểm</p>
                <p class="text-sm text-gray-500 italic mb-8 px-4">"Bạn đã chính thức nắm vững kỹ năng phòng chống bạo lực học đường tại THCS Trương Công Giai!"</p>
                
                <button onclick="downloadCertificate()" class="w-full sm:w-auto mx-auto bg-green-500 hover:bg-green-600 text-white font-bold py-4 px-8 rounded-xl shadow-lg transition transform hover:-translate-y-1 flex items-center justify-center gap-2 text-lg mb-4">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4"></path></svg>
                    Tải Giấy Chứng Nhận (TXT)
                </button>
                <button onclick="closeQuizModal()" class="text-gray-500 font-bold hover:text-gray-800 underline">Đóng và quay lại trang</button>
            </div>

        </div>
    </div>

    <!-- Script xử lý sự kiện tích hợp Database Đám mây -->
    <script type="module">
        // Import các module của Firebase Đám mây
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, collection, addDoc, onSnapshot, query, doc, deleteDoc } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // --- CẤU HÌNH HỆ THỐNG CLOUD DATABASE ---
        let app, auth, db, currentUser;
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'blue-flow-v1';
        let isCloudActive = false;
        let reportsData = []; // Mảng chứa dữ liệu

        try {
            // Chỉ kích hoạt lưu trữ đám mây khi hệ thống cho phép
            if (typeof __firebase_config !== 'undefined') {
                const firebaseConfig = JSON.parse(__firebase_config);
                app = initializeApp(firebaseConfig);
                auth = getAuth(app);
                db = getFirestore(app);
                isCloudActive = true;
                
                const initAuth = async () => {
                    if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                        await signInWithCustomToken(auth, __initial_auth_token);
                    } else {
                        await signInAnonymously(auth);
                    }
                };
                initAuth();

                // Lắng nghe dữ liệu theo thời gian thực từ tất cả các người dùng
                onAuthStateChanged(auth, (user) => {
                    currentUser = user;
                    if (user) {
                        const reportsRef = collection(db, 'artifacts', appId, 'public', 'data', 'sos_reports');
                        onSnapshot(query(reportsRef), (snapshot) => {
                            reportsData = [];
                            snapshot.forEach(docSnap => reportsData.push({ _id: docSnap.id, ...docSnap.data() }));
                            renderAdminTable(); // Cập nhật lại bảng quản trị ngay lập tức
                        }, (error) => console.error("Lỗi đồng bộ dữ liệu:", error));
                    }
                });
            }
        } catch(e) {
            console.warn("Chạy ở chế độ Demo (Bộ nhớ tạm cục bộ) do chưa có kết nối CSDL:", e);
        }

        // --- 1. LOGIC GỬI BÁO CÁO SOS LÊN ĐÁM MÂY ---
        document.getElementById('sosForm').addEventListener('submit', async function(e) {
            e.preventDefault(); 
            const issueSelect = document.getElementById('issue');
            const urgencySelect = document.getElementById('urgency');
            const fullName = document.getElementById('fullName').value.trim();
            const className = document.getElementById('className').value.trim();
            const detailsText = document.getElementById('details').value;
            const roleInput = document.querySelector('input[name="role"]:checked');
            
            const newReport = {
                time: new Date().toLocaleString('vi-VN'),
                createdAt: Date.now(), // Thời gian lưu trữ chuẩn để sắp xếp
                fullName: fullName || 'Ẩn danh',
                className: className || 'Không rõ',
                issue: issueSelect.options[issueSelect.selectedIndex].text,
                urgency: urgencySelect.options[urgencySelect.selectedIndex].text,
                details: detailsText,
                role: roleInput && roleInput.value === 'nan_nhan' ? 'Nạn nhân' : 'Người chứng kiến'
            };

            // Đẩy dữ liệu lên Cloud Database
            if (isCloudActive && currentUser) {
                try {
                    const reportsRef = collection(db, 'artifacts', appId, 'public', 'data', 'sos_reports');
                    await addDoc(reportsRef, newReport);
                    // Không cần reportsData.push() vì onSnapshot ở trên sẽ tự động kéo dữ liệu về
                } catch(err) {
                    console.error("Lỗi gửi dữ liệu lên Cloud:", err);
                    reportsData.push(newReport); renderAdminTable(); // Chế độ dự phòng cục bộ
                }
            } else {
                reportsData.push(newReport); renderAdminTable(); // Chế độ dự phòng cục bộ
            }

            document.getElementById('successModal').classList.remove('hidden');
            this.reset();
        });

        // Hàm render giao diện Bảng quản trị
        function renderAdminTable() {
            const tbody = document.getElementById('reportTableBody');
            tbody.innerHTML = '';
            
            // Cập nhật trạng thái của nút Xóa Thư rác
            checkTrashState();
            
            if (reportsData.length === 0) {
                tbody.innerHTML = '<tr><td colspan="5" class="px-6 py-8 text-center text-gray-500 font-medium">Chưa có báo cáo nào được ghi nhận.</td></tr>';
                return;
            }
            
            // Sắp xếp tự động các báo cáo mới nhất lên đầu tiên
            const sortedReports = [...reportsData].sort((a, b) => b.createdAt - a.createdAt);
            
            sortedReports.forEach(report => {
                const tr = document.createElement('tr');
                tr.className = "hover:bg-slate-50 transition";
                let urgencyColorClass = "text-gray-700";
                if (report.urgency.includes("Nguy hiểm")) urgencyColorClass = "text-red-600 font-bold";
                else if (report.urgency.includes("Trung bình")) urgencyColorClass = "text-orange-500 font-semibold";

                tr.innerHTML = `
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${report.time}</td>
                    <td class="px-6 py-4 whitespace-nowrap"><div class="font-medium text-gray-900">${report.fullName}</div><div class="text-xs text-gray-500">Lớp: ${report.className}</div></td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm font-semibold text-gray-800">${report.issue}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm ${urgencyColorClass}">${report.urgency}</td>
                    <td class="px-6 py-4 text-sm text-gray-600 max-w-xs truncate" title="${report.details} (${report.role})">${report.details} <br><span class="text-xs text-blue-500 font-medium">[${report.role}]</span></td>
                `;
                tbody.appendChild(tr);
            });
        }

        // Hàm kiểm tra và kích hoạt nút Thùng rác
        function checkTrashState() {
            const clearTrashBtn = document.getElementById('clearTrashBtn');
            const trashCount = document.getElementById('trashCount');
            
            // Nếu khu vực bảng chưa hiện (giáo viên chưa đăng nhập) thì bỏ qua
            if (document.getElementById('adminTableContainer').classList.contains('hidden')) return;

            trashCount.innerText = `${reportsData.length}/1000`;

            if (reportsData.length >= 1000) {
                clearTrashBtn.className = "flex bg-red-50 border border-red-200 text-red-600 hover:bg-red-100 font-bold py-3 px-4 rounded-xl shadow-sm transition items-center gap-2 animate-pulse-fast cursor-pointer";
            } else {
                clearTrashBtn.className = "flex bg-gray-100 border border-gray-300 text-gray-400 font-bold py-3 px-4 rounded-xl shadow-sm transition items-center gap-2 cursor-not-allowed opacity-70";
            }
        }

        // --- 2. XUẤT FILE CSV & KIỂM TRA MẬT KHẨU GIÁO VIÊN ---
        document.getElementById('exportCsvBtn').addEventListener('click', function() {
            if (reportsData.length === 0) return; 
            
            // Sắp xếp lại file xuất ra theo thời gian mới nhất
            const sortedData = [...reportsData].sort((a, b) => b.createdAt - a.createdAt);
            
            let csvContent = "\uFEFFThời gian,Họ tên,Lớp,Vấn đề,Mức độ khẩn cấp,Vai trò,Chi tiết sự việc\n";
            sortedData.forEach(report => {
                let safeDetails = `"${report.details.replace(/"/g, '""')}"`; 
                csvContent += `"${report.time}","${report.fullName}","${report.className}","${report.issue}","${report.urgency}","${report.role}",${safeDetails}\n`;
            });
            const link = document.createElement("a");
            link.href = URL.createObjectURL(new Blob([csvContent], { type: 'text/csv;charset=utf-8;' }));
            link.download = "BlueFlow_BaoCao.csv";
            document.body.appendChild(link); link.click(); document.body.removeChild(link);
            
            // === LOGIC MỚI: Tự động khóa bảo mật sau khi tải ===
            // 1. Ẩn bảng dữ liệu và các nút
            document.getElementById('adminTableContainer').classList.add('hidden');
            document.getElementById('exportCsvBtn').classList.add('hidden');
            document.getElementById('exportCsvBtn').classList.remove('flex');
            document.getElementById('clearTrashBtn').classList.add('hidden');
            document.getElementById('clearTrashBtn').classList.remove('flex');
            
            // 2. Hiện lại Form đăng nhập và xóa trống email
            document.getElementById('adminLogin').classList.remove('hidden');
            document.getElementById('teacherEmail').value = '';
            
            // 3. Hiện dòng chữ thông báo đã khóa màu xanh
            document.getElementById('authSuccessMsg').classList.remove('hidden');
            document.getElementById('authError').classList.add('hidden');
        });

        function closeModal() { document.getElementById('successModal').classList.add('hidden'); }
        
        document.getElementById('authBtn').addEventListener('click', function() {
            // Ẩn thông báo khóa bảo mật (nếu đang hiện) khi bấm xác thực lại
            document.getElementById('authSuccessMsg').classList.add('hidden');
            
            if (document.getElementById('teacherEmail').value.trim() === 'phamhaihnue95@gmail.com') {
                document.getElementById('adminLogin').classList.add('hidden');
                document.getElementById('adminTableContainer').classList.remove('hidden');
                document.getElementById('exportCsvBtn').classList.remove('hidden');
                document.getElementById('exportCsvBtn').classList.add('flex');
                
                // Hiển thị nút Thùng rác khi đăng nhập thành công
                document.getElementById('clearTrashBtn').classList.remove('hidden');
                document.getElementById('clearTrashBtn').classList.add('flex');
                checkTrashState();
                
                document.getElementById('authError').classList.add('hidden'); 
            } else {
                document.getElementById('authError').classList.remove('hidden');
            }
        });

        // Hàm xử lý khi giáo viên click vào nút Thư rác đang sáng
        async function handleClearTrash() {
            if (reportsData.length < 1000) return; // Chưa đủ 1000 thư thì không làm gì cả
            
            // Hiện Modal thông báo thành công
            document.getElementById('trashModal').classList.remove('hidden');
            
            // Xóa 1000 item cũ nhất (ưu tiên xóa các báo cáo gửi lâu nhất)
            const sortedData = [...reportsData].sort((a, b) => a.createdAt - b.createdAt);
            const docsToDelete = sortedData.slice(0, 1000);
            
            if (isCloudActive && currentUser) {
                try {
                    // Chạy vòng lặp để yêu cầu Cloud xóa từng file một
                    for (let item of docsToDelete) {
                        if(item._id) {
                            await deleteDoc(doc(db, 'artifacts', appId, 'public', 'data', 'sos_reports', item._id));
                        }
                    }
                } catch (e) { 
                    console.error("Lỗi khi dọn dẹp:", e); 
                }
            } else {
                // Xử lý bộ nhớ cục bộ nếu không có mạng
                reportsData = sortedData.slice(1000);
                renderAdminTable();
            }
        }

        // =========================================================
        // --- LOGIC TRÒ CHƠI "THỬ THÁCH ĐẠI SỨ XANH" ---
        // =========================================================
        const quizQuestions = [
            { q: "Khi chúng ta tức giận, cơ thể sẽ tiết ra hormone nào khiến tim đập nhanh và huyết áp tăng?", options: ["Endorphin và Dopamine", "Adrenaline và Cortisol", "Melatonin và Serotonin", "Insulin và Thyroxine"], correct: 1 },
            { q: "Bộ phận nào trong não bộ hoạt động như một 'cái phanh' giúp chúng ta suy nghĩ logic và không phản ứng bốc đồng?", options: ["Hạch hạnh nhân (Amygdala)", "Hồi hải mã (Hippocampus)", "Tiểu não", "Vỏ não trước (Prefrontal cortex)"], correct: 3 },
            { q: "Hít thở sâu khi cáu giận có tác dụng khoa học gì?", options: ["Cung cấp thêm oxy cho não, giảm nhịp tim và làm dịu hệ thần kinh", "Làm tăng adrenaline để sẵn sàng chiến đấu", "Giúp cơ bắp căng cứng hơn để chịu đòn", "Không có tác dụng gì, chỉ là thói quen"], correct: 0 },
            { q: "'Body shaming' (Miệt thị ngoại hình) có thể gây ra hậu quả sinh lý nào cho nạn nhân?", options: ["Tăng cường hệ miễn dịch", "Căng thẳng mãn tính, mất ngủ và suy giảm trí nhớ", "Giúp nạn nhân cao lớn hơn", "Tăng cường thị lực"], correct: 1 },
            { q: "Khi bị bắt nạt, việc chia sẻ với người lớn giúp giải phóng hormone nào tạo cảm giác an toàn và gắn kết?", options: ["Adrenaline", "Cortisol", "Oxytocin", "Testosterone"], correct: 2 },
            { q: "Khi thấy một bức ảnh chế giễu bạn cùng lớp bị phát tán trên nhóm chat, bạn nên làm gì?", options: ["Cười theo và chuyển tiếp cho nhóm khác", "Lặng lẽ lưu ảnh về máy", "Tuyệt đối không chia sẻ tiếp, khuyên các bạn dừng lại và chụp màn hình báo cáo giáo viên", "Vào chửi bới người đăng ảnh để bảo vệ bạn"], correct: 2 },
            { q: "Một người bạn trên mạng xin mật khẩu tài khoản của bạn để 'chơi game hộ'. Bạn xử lý thế nào?", options: ["Cho mượn nhưng dặn không được đổi pass", "Từ chối ngay lập tức, mật khẩu là thông tin cá nhân tuyệt mật", "Đưa mật khẩu và xin lại mật khẩu của bạn ấy", "Đổi mật khẩu dễ nhớ rồi đưa cho bạn"], correct: 1 },
            { q: "Dấu hiệu rõ nhất của 'Cyberbullying' (Bắt nạt mạng) là gì?", options: ["Những tin nhắn, bình luận lặp đi lặp lại mang tính đe dọa, xúc phạm hoặc bôi nhọ", "Bạn bè trêu đùa nhau 1-2 câu vui vẻ", "Một người bạn không like ảnh của bạn", "Bị chặn tin nhắn vì gửi quá nhiều spam"], correct: 0 },
            { q: "Quy tắc 'Ngoảnh mặt làm ngơ' khi bị chê bai trên mạng nghĩa là gì?", options: ["Tắt máy tính đi ngủ ngay lập tức", "Chửi lại một câu thật đau rồi mới block", "Đăng một bài status dài để giải thích", "Không phản hồi, không cãi vã lại, lập tức block (chặn) tài khoản độc hại"], correct: 3 },
            { q: "Nếu vô tình nhấn vào một đường link lạ và bị đe dọa tống tiền bằng hình ảnh, bước đầu tiên cần làm là?", options: ["Không chuyển tiền, ngắt kết nối mạng và báo ngay cho phụ huynh/giáo viên", "Chuyển một ít tiền để họ tha cho mình", "Xóa tài khoản mạng xã hội ngay lập tức", "Tự mình tìm cách hack lại kẻ xấu"], correct: 0 },
            { q: "Bạn tình cờ thấy một nhóm anh chị khóa trên đang đe dọa một em lớp 6 mới vào trường. Bạn nên làm gì an toàn nhất?", options: ["Lao vào đánh lại nhóm anh chị đó", "Tránh đối đầu trực tiếp nếu nguy hiểm, lùi ra xa và dùng tính năng gửi SOS ẩn danh trên Blue Flow", "Lấy điện thoại ra quay video up Tiktok câu view", "Giả vờ không thấy và đi nhanh qua"], correct: 1 },
            { q: "Mục đích lớn nhất của tính năng 'Hộp thư Ẩn danh' trên nền tảng Blue Flow là gì?", options: ["Để học sinh có thể nói xấu người khác mà không bị phát hiện", "Để giáo viên phạt học sinh dễ hơn", "Bảo vệ danh tính người báo cáo, giúp học sinh xóa bỏ rào cản sợ bị trả thù", "Để nộp bài tập về nhà môn Tin học"], correct: 2 },
            { q: "Bạn là người đi ngang qua và thấy một vụ đánh nhau nhưng chỉ đứng quay video. Hành động đó gọi là gì?", options: ["Người đưa tin dũng cảm", "Phóng viên hiện trường", "Hành động tự vệ chính đáng", "Sự vô cảm của người chứng kiến (Bystander effect) - gián tiếp tiếp tay cho bạo lực"], correct: 3 },
            { q: "Theo thông điệp của dự án Blue Flow, ai là người có trách nhiệm xây dựng 'Trường học Hạnh phúc'?", options: ["Chỉ có Hiệu trưởng", "Tất cả mọi người: Học sinh, giáo viên, phụ huynh và nhà trường", "Chỉ có Giáo viên chủ nhiệm", "Chỉ có Học sinh ngoan"], correct: 1 },
            { q: "Khi xảy ra mâu thuẫn nhỏ với bạn thân, cách giải quyết tốt nhất để giữ 'Tình bạn đẹp' là gì?", options: ["Lên mạng xã hội viết status nói bóng gió", "Chờ cả hai bình tĩnh và mở một cuộc đối thoại trực tiếp, chân thành", "Nhờ một nhóm bạn khác ra mặt dằn mặt bạn đó", "Lờ đi coi như chưa có chuyện gì và không bao giờ nói chuyện lại"], correct: 1 }
        ];

        let currentQuestionIndex = 0;
        let score = 0;
        let playerInfo = { name: "Ẩn danh", className: "Không rõ" };

        function openQuizModal() {
            document.getElementById('quizModal').classList.remove('hidden');
            document.getElementById('quizIntro').classList.remove('hidden');
            document.getElementById('quizPlay').classList.add('hidden');
            document.getElementById('quizPlay').classList.remove('flex');
            document.getElementById('quizResult').classList.add('hidden');
            currentQuestionIndex = 0; score = 0;
            document.getElementById('quizName').value = ''; document.getElementById('quizClass').value = '';
        }

        function closeQuizModal() { document.getElementById('quizModal').classList.add('hidden'); }

        function startQuiz() {
            playerInfo.name = document.getElementById('quizName').value.trim() || "Ẩn danh";
            playerInfo.className = document.getElementById('quizClass').value.trim() || "Không rõ";
            document.getElementById('quizIntro').classList.add('hidden');
            document.getElementById('quizPlay').classList.remove('hidden');
            document.getElementById('quizPlay').classList.add('flex');
            loadQuestion();
        }

        function loadQuestion() {
            document.getElementById('quizProgress').innerText = `Câu ${currentQuestionIndex + 1}/${quizQuestions.length}`;
            document.getElementById('quizScoreDisplay').innerText = score;
            const qData = quizQuestions[currentQuestionIndex];
            document.getElementById('questionText').innerText = qData.q;
            const optionsContainer = document.getElementById('optionsContainer');
            optionsContainer.innerHTML = '';
            qData.options.forEach((optionText, index) => {
                const btn = document.createElement('button');
                btn.className = "w-full text-left p-4 rounded-xl border-2 border-gray-200 hover:border-blue-400 hover:bg-blue-50 font-semibold text-gray-700 transition duration-200 outline-none";
                btn.innerText = optionText;
                btn.onclick = () => selectOption(btn, index);
                optionsContainer.appendChild(btn);
            });
        }

        function selectOption(clickedBtn, selectedIndex) {
            const qData = quizQuestions[currentQuestionIndex];
            const isCorrect = (selectedIndex === qData.correct);
            const buttons = document.getElementById('optionsContainer').children;
            for (let btn of buttons) btn.classList.add('disabled-btn');

            if (isCorrect) {
                score++; clickedBtn.classList.add('correct-answer');
                document.getElementById('quizScoreDisplay').innerText = score;
            } else {
                clickedBtn.classList.add('wrong-answer');
                buttons[qData.correct].classList.add('correct-answer');
            }

            setTimeout(() => {
                currentQuestionIndex++;
                if (currentQuestionIndex < quizQuestions.length) loadQuestion();
                else showQuizResult();
            }, 1500);
        }

        function showQuizResult() {
            document.getElementById('quizPlay').classList.add('hidden');
            document.getElementById('quizPlay').classList.remove('flex');
            document.getElementById('quizResult').classList.remove('hidden');
            document.getElementById('finalScore').innerText = `${score}/${quizQuestions.length}`;
            const emoji = document.getElementById('resultEmoji');
            if(score === 15) emoji.innerText = "🏆"; else if(score >= 10) emoji.innerText = "🌟"; else emoji.innerText = "👍";
        }

        function downloadCertificate() {
            let txtContent = "========================================================\n          BÁO CÁO THỬ THÁCH ĐẠI SỨ XANH\n                  DỰ ÁN BLUE FLOW\n========================================================\n\n";
            txtContent += `Học sinh: ${playerInfo.name} - Lớp: ${playerInfo.className}.\nĐã đạt ${score}/15 điểm.\n\n`;
            txtContent += "Bạn đã chính thức nắm vững kỹ năng phòng chống bạo lực học đường tại THCS Trương Công Giai!\n";
            txtContent += "Hãy lan tỏa tình yêu thương và sự tích cực nhé! 🌊\n";
            const link = document.createElement("a");
            link.href = URL.createObjectURL(new Blob(["\uFEFF" + txtContent], { type: 'text/plain;charset=utf-8;' }));
            link.download = `ChungNhan_DaiSuXanh_${playerInfo.name}.txt`;
            document.body.appendChild(link); link.click(); document.body.removeChild(link);
        }

        // Tắt hiệu ứng nhấp nháy khi người dùng click vào nút Hướng dẫn
        document.getElementById('guideBtn').addEventListener('click', function() {
            this.classList.remove('animate-pulse-fast');
        });

        // Gắn các hàm tương tác với giao diện ra cấp toàn cục (Window) để HTML có thể gọi được
        window.closeModal = closeModal;
        window.closeTrashModal = () => document.getElementById('trashModal').classList.add('hidden');
        window.handleClearTrash = handleClearTrash;
        window.openQuizModal = openQuizModal;
        window.closeQuizModal = closeQuizModal;
        window.startQuiz = startQuiz;
        window.downloadCertificate = downloadCertificate;
        window.selectOption = selectOption;
    </script>
</body>
</html>

