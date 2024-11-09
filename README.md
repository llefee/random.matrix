<!DOCTYPE html>
<html>
<head>
    <title>Random Matrix</title>
    <style>
        body {
            background-color: black;
            color: white;
            margin: 0;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .matrix {
            font-family: monospace;
            white-space: pre;
            display: flex;
            flex-wrap: wrap;
        }
        .green {
            color: green;
        }
    </style>
    <script>
        function getRandomInt(max) {
            return Math.floor(Math.random() * max) + 1;
        }

        function getRandomCharacter() {
            const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
            return chars[Math.floor(Math.random() * chars.length)];
        }

        function generateMatrix(rows, cols) {
            const container = document.getElementById('matrix');
            container.innerHTML = ''; // Clear previous matrix

            for (let i = 0; i < rows; i++) {
                let row = '';
                for (let j = 0; j < cols; j++) {
                    let char = getRandomCharacter();
                    row += `<span class="green">${char}</span> `;
                }
                const div = document.createElement('div');
                div.innerHTML = row;
                container.appendChild(div);
            }
        }

        function adjustMatrixSize() {
            const width = window.innerWidth;
            const height = window.innerHeight;
            const fontSize = 20; // Adjust font size if needed
            const cols = Math.floor(width / fontSize);
            const rows = Math.floor(height / fontSize);
            generateMatrix(rows, cols);
        }

        window.onload = function() {
            adjustMatrixSize();
            setInterval(adjustMatrixSize, 1000); // Refresh every 1 second for better performance
        };

        window.onresize = adjustMatrixSize; // Adjust matrix on window resize
    </script>
</head>
<body>
    <div id="matrix" class="matrix"></div>
</body>
</html>
