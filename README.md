<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Birthday Gift Card</title>
    <script src="https://cdn.tailwindcss.com/3.4.16"></script>
    <script>tailwind.config={theme:{extend:{colors:{primary:'#FF69B4',secondary:'#9370DB'},borderRadius:{'none':'0px','sm':'4px',DEFAULT:'8px','md':'12px','lg':'16px','xl':'20px','2xl':'24px','3xl':'32px','full':'9999px','button':'8px'}}}}</script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Quicksand:wght@400;500;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/remixicon/4.6.0/remixicon.min.css">
    <style>
        :where([class^="ri-"])::before { content: "\f3c2"; }
        body {
            font-family: 'Quicksand', sans-serif;
            background-color: #f8f9fa;
        }
        .birthday-title {
            font-family: 'Dancing Script', cursive;
        }
        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            background-color: #FFD700;
            opacity: 0;
            animation: confetti-fall 5s ease-out forwards;
        }
        @keyframes confetti-fall {
            0% {
                transform: translateY(-100px) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(500px) rotate(360deg);
                opacity: 0;
            }
        }
        .balloon {
            position: absolute;
            animation: float 6s ease-in-out infinite;
        }
        @keyframes float {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-20px);
            }
        }
        .pulse {
            animation: pulse 2s infinite;
        }
        @keyframes pulse {
            0% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.05);
            }
            100% {
                transform: scale(1);
            }
        }
    </style>
</head>
<body class="bg-gradient-to-b from-pink-50 to-purple-50 min-h-screen flex items-center justify-center px-4">
    <div class="w-full max-w-md">
        <div class="relative bg-white rounded-2xl shadow-lg overflow-hidden border-4 border-primary p-6 mb-20">
            <!-- Decorative Elements -->
            <div class="balloon text-5xl text-red-500" style="top: -20px; left: 10px;">🎈</div>
            <div class="balloon text-5xl text-blue-500" style="top: -15px; right: 10px; animation-delay: 1s;">🎈</div>
            <div class="balloon text-5xl text-yellow-500" style="top: -25px; left: 40%; animation-delay: 2s;">🎈</div>
            
            <!-- Header -->
            <div class="text-center mb-6">
                <h1 class="birthday-title text-4xl font-bold text-primary mb-2 pulse">Happy Birthday!</h1>
                <h2 class="text-2xl font-['Pacifico'] text-secondary">Hassan Icon</h2>
            </div>
            
            <!-- Cake Image -->
            <div class="flex justify-center mb-6">
                <img src="https://readdy.ai/api/search-image?query=3D%20cartoon%20birthday%20cake%20with%20lit%20candles%2C%20colorful%20frosting%2C%20festive%20decorations%2C%20the%20cake%20should%20take%20up%2070%25%20of%20the%20frame%2C%20isolated%20on%20white%20background%2C%20centered%20composition%2C%20soft%20lighting%2C%20subtle%20shadows%2C%20celebration%20theme%2C%20highly%20detailed%2C%20vibrant%20colors&width=200&height=200&seq=cake123&orientation=squarish" alt="Birthday Cake" class="w-40 h-40 object-contain">
            </div>
            
            <!-- Personal Message -->
            <div class="bg-pink-50 rounded-xl p-4 mb-6 border-2 border-dashed border-secondary">
                <h3 class="text-lg font-semibold text-gray-800 mb-2">A Special Message For You:</h3>
                <p class="text-gray-700">
                    On this wonderful day, I want to celebrate you and all the joy you bring to everyone around you. May your day be filled with laughter, love, and unforgettable moments. Here's to another amazing year ahead!
                </p>
                <p class="text-gray-700 mt-3 font-medium">
                    Wishing you all the best,<br>
                    Your Friend
                </p>
            </div>
            
            <!-- Surprise Button -->
            <div class="text-center">
                <button id="surpriseBtn" class="bg-primary hover:bg-pink-600 text-white font-bold py-3 px-8 rounded-button transition-all duration-300 shadow-md hover:shadow-lg flex items-center justify-center mx-auto pulse cursor-pointer">
                    <i class="ri-gift-2-fill ri-lg mr-2 w-6 h-6 flex items-center justify-center"></i>
                    Open Your Surprise!
                </button>
            </div>
            
            <!-- Decorative bottom elements -->
            <div class="text-2xl absolute bottom-2 left-4">🎁</div>
            <div class="text-2xl absolute bottom-2 right-4">🎉</div>
        </div>
    </div>
    
    <!-- Modal -->
    <div id="surpriseModal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 hidden">
        <div class="bg-white rounded-2xl p-6 max-w-sm mx-4 relative transform transition-all">
            <button id="closeModal" class="absolute top-2 right-2 text-gray-500 hover:text-gray-700 cursor-pointer">
                <i class="ri-close-line ri-lg w-6 h-6 flex items-center justify-center"></i>
            </button>
            <div class="text-center">
                <div class="text-5xl mb-4">🎉</div>
                <h3 class="birthday-title text-3xl font-bold text-primary mb-4">Surprise!</h3>
                <div id="birthdayGif" class="mb-4 rounded-lg overflow-hidden">
                    <img src="https://readdy.ai/api/search-image?query=animated%20style%20confetti%20explosion%20with%20colorful%20streamers%20and%20party%20poppers%2C%20festive%20celebration%2C%20dynamic%20motion%2C%20vibrant%20colors%2C%20joyful%20atmosphere%2C%20birthday%20party%20theme%2C%20isolated%20on%20white%20background%2C%20centered%20composition&width=300&height=200&seq=surprise456&orientation=landscape" alt="Birthday Celebration" class="w-full">
                </div>
                <p class="text-gray-700 mb-4">May your day be as wonderful as you are! Enjoy this special day and the year ahead!</p>
                <button id="makeWish" class="bg-secondary hover:bg-purple-600 text-white font-bold py-2 px-6 rounded-button transition-all duration-300 cursor-pointer">
                    Make a Wish
                </button>
            </div>
        </div>
    </div>

    <script id="confettiScript">
        document.addEventListener('DOMContentLoaded', function() {
            function createConfetti() {
                const colors = ['#FF69B4', '#9370DB', '#FFD700', '#87CEEB', '#FF6347'];
                const confettiContainer = document.body;
                
                for (let i = 0; i < 100; i++) {
                    setTimeout(() => {
                        const confetti = document.createElement('div');
                        confetti.classList.add('confetti');
                        confetti.style.left = Math.random() * 100 + 'vw';
                        confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                        confetti.style.width = Math.random() * 10 + 5 + 'px';
                        confetti.style.height = Math.random() * 10 + 5 + 'px';
                        confetti.style.animationDuration = Math.random() * 3 + 2 + 's';
                        confettiContainer.appendChild(confetti);
                        
                        setTimeout(() => {
                            confetti.remove();
                        }, 5000);
                    }, i * 50);
                }
            }
            
            // Initial confetti
            createConfetti();
        });
    </script>

    <script id="modalScript">
        document.addEventListener('DOMContentLoaded', function() {
            const surpriseBtn = document.getElementById('surpriseBtn');
            const surpriseModal = document.getElementById('surpriseModal');
            const closeModal = document.getElementById('closeModal');
            const makeWish = document.getElementById('makeWish');
            
            surpriseBtn.addEventListener('click', function() {
                surpriseModal.classList.remove('hidden');
                createConfetti();
            });
            
            closeModal.addEventListener('click', function() {
                surpriseModal.classList.add('hidden');
            });
            
            makeWish.addEventListener('click', function() {
                alert('Your wish has been sent to the birthday universe! ✨');
                surpriseModal.classList.add('hidden');
            });
            
            function createConfetti() {
                const colors = ['#FF69B4', '#9370DB', '#FFD700', '#87CEEB', '#FF6347'];
                const confettiContainer = document.body;
                
                for (let i = 0; i < 150; i++) {
                    setTimeout(() => {
                        const confetti = document.createElement('div');
                        confetti.classList.add('confetti');
                        confetti.style.left = Math.random() * 100 + 'vw';
                        confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                        confetti.style.width = Math.random() * 10 + 5 + 'px';
                        confetti.style.height = Math.random() * 10 + 5 + 'px';
                        confetti.style.animationDuration = Math.random() * 3 + 2 + 's';
                        confettiContainer.appendChild(confetti);
                        
                        setTimeout(() => {
                            confetti.remove();
                        }, 5000);
                    }, i * 30);
                }
            }
        });
    </script>
</body>
</html>
