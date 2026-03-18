# 前端练手好项目：纯 HTML+JS 实现网页版贪吃蛇（附源码）

## 为什么推荐用网页写游戏？
对于初学编程的朋友来说，利用 HTML5 的 `<canvas>` 元素和 JavaScript 写小游戏是最好的练手方式。它不需要配置复杂的环境，只要有一个浏览器和文本编辑器就能立刻看到效果，正反馈极强！

## 源码分享：极简贪吃蛇
下面是一个非常基础的贪吃蛇核心代码。新建一个 `index.html` 文件，把代码复制进去，双击用浏览器打开就能直接玩！

```html
<!DOCTYPE html>
<html>
<head>
    <title>贪吃蛇小游戏</title>
    <style>
        canvas { background: #eee; display: block; margin: 0 auto; }
        body { text-align: center; padding-top: 50px; font-family: sans-serif;}
    </style>
</head>
<body>
    <h2>网页贪吃蛇</h2>
    <canvas id="gameCanvas" width="400" height="400"></canvas>
    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        const gridSize = 20;
        let snake = [{x: 200, y: 200}];
        let food = {x: 100, y: 100};
        let dx = gridSize;
        let dy = 0;

        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            // 画食物
            ctx.fillStyle = 'red';
            ctx.fillRect(food.x, food.y, gridSize, gridSize);
            // 画蛇
            ctx.fillStyle = 'green';
            snake.forEach(part => ctx.fillRect(part.x, part.y, gridSize, gridSize));
        }

        function update() {
            const head = {x: snake[0].x + dx, y: snake[0].y + dy};
            snake.unshift(head);
            if (head.x === food.x && head.y === food.y) {
                food = {x: Math.floor(Math.random() * 20) * gridSize, y: Math.floor(Math.random() * 20) * gridSize};
            } else {
                snake.pop();
            }
        }

        document.addEventListener('keydown', e => {
            if (e.key === 'ArrowUp' && dy === 0) { dx = 0; dy = -gridSize; }
            if (e.key === 'ArrowDown' && dy === 0) { dx = 0; dy = gridSize; }
            if (e.key === 'ArrowLeft' && dx === 0) { dx = -gridSize; dy = 0; }
            if (e.key === 'ArrowRight' && dx === 0) { dx = gridSize; dy = 0; }
        });

        setInterval(() => { update(); draw(); }, 100);
    </script>
</body>
</html>