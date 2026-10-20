<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Moving Box</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            overflow: hidden; /* Prevents scrollbars from appearing */
            background-color: #f0f0f0;
        }

        /* Styling for the moving box */
        #movingBox {
            width: 50px;
            height: 50px;
            background-color: red;
            position: absolute;
            top: 0px;
            left: 0px;
        }
    </style>
</head>
<body>

    <!-- The Box -->
    <div id="movingBox"></div>

    <script>
        const box = document.getElementById('movingBox');
        
        // Set initial positions and movement speed
        let topPos = 100;
        let leftPos = 100;
        const speed = 15; 

        // Apply initial position
        box.style.top = topPos + 'px';
        box.style.left = leftPos + 'px';

        // Listen for keydown events
        window.addEventListener('keydown', (event) => {
            // Get current window dimensions and box dimensions dynamically
            const boxWidth = box.offsetWidth;
            const boxHeight = box.offsetHeight;
            const windowWidth = window.innerWidth;
            const windowHeight = window.innerHeight;

            switch (event.key) {
                // Move Up (Stop at top 0)
                case 'w':
                case 'W':
                case 'ArrowUp':
                    topPos = Math.max(0, topPos - speed);
                    break;
                
                // Move Down (Stop at window height minus box height)
                case 's':
                case 'S':
                case 'ArrowDown':
                    topPos = Math.min(windowHeight - boxHeight, topPos + speed);
                    break;
                
                // Move Left (Stop at left 0)
                case 'a':
                case 'A':
                case 'ArrowLeft':
                    leftPos = Math.max(0, leftPos - speed);
                    break;
                
                // Move Right (Stop at window width minus box width)
                case 'd':
                case 'D':
                case 'ArrowRight':
                    leftPos = Math.min(windowWidth - boxWidth, leftPos + speed);
                    break;
            }

            // Update the box's position on the screen
            box.style.top = topPos + 'px';
            box.style.left = leftPos + 'px';
        });
    </script>

</body>
</html>
