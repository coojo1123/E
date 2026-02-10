<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>랜덤 챌린지 뽑기</title>
    <style>
        /* 깔끔한 디자인을 위한 스타일 */
        body { font-family: 'Pretendard', sans-serif; display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100vh; margin: 0; background-color: #f0f2f5; }
        .card { background: white; padding: 2rem; border-radius: 20px; box-shadow: 0 10px 25px rgba(0,0,0,0.1); text-align: center; width: 320px; }
        h1 { color: #333; margin-bottom: 1.5rem; font-size: 1.5rem; }
        #display { font-size: 2rem; font-weight: bold; color: #ff4757; margin: 2rem 0; min-height: 3rem; display: flex; align-items: center; justify-content: center; border: 2px dashed #ddd; border-radius: 10px; }
        button { background-color: #5352ed; color: white; border: none; padding: 12px 25px; font-size: 1.1rem; border-radius: 10px; cursor: pointer; transition: 0.2s; width: 100%; }
        button:hover { background-color: #3736af; transform: scale(1.02); }
        button:active { transform: scale(0.98); }
    </style>
</head>
<body>

    <div class="card">
        <h1>🎲 랜덤 챌린지</h1>
        <div id="display">준비 완료!</div>
        <button onclick="startDraw()">뽑기 시작!</button>
    </div>

    <script>
        // 여기에 원하는 항목들을 넣으세요!
        const items = ["팔굽혀펴기 10회", "노래 한 곡 부르기", "물 한잔 마시기", "옆사람 칭찬하기", "꽝! 다음 기회에", "스쿼트 15회", "윙크하기"];

        function startDraw() {
            const display = document.getElementById('display');
            let count = 0;
            
            // 버튼 중복 클릭 방지
            const btn = document.querySelector('button');
            btn.disabled = true;

            // 빠르게 바뀌는 효과 (랜덤 셔플 애니메이션)
            const timer = setInterval(() => {
                const tempIndex = Math.floor(Math.random() * items.length);
                display.innerText = items[tempIndex];
                count++;

                if (count > 15) { // 15번 바뀐 뒤 멈춤
                    clearInterval(timer);
                    const finalIndex = Math.floor(Math.random() * items.length);
                    display.innerText = "✨ " + items[finalIndex] + " ✨";
                    btn.disabled = false;
                }
            }, 100);
        }
    </script>
</body>
</html>
