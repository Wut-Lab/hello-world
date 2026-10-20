<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hello World & Moving Box</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            overflow: hidden; /* Prevents scrollbars when the box moves off-screen */
        }

        /* Styling for the moving box */
        #movingBox {
            width: 50px;
            height: 50px;
            background-color: red;
            position: absolute;
            top: 150px;
            left: 50px;
            transition: 0.1s ease; /* Makes the movement smoother */
        }
    </style>
</head>
<body>

    <h1>Hello World</h1>
    <p>Use <b>WASD</b> or the <b>Arrow Keys</b> to move the red box.</p>

    <!-- The Box -->
    <div id="movingBox"></div>

    <script>
        // Get the box element
        const box = document.getElementById('movingBox');
        
        // Set initial positions and movement speed
        let topPos = 150;
        let leftPos = 50;
        const speed = 15; 

        // Listen for keydown events
        window.addEventListener('keydown', (event) => {
            switch (event.key) {
                // Move Up
                case 'w':
                case 'W':
                case 'ArrowUp':
                    topPos -= speed;
                    break;
                
                // Move Down
                case 's':
                case 'S':
                case 'ArrowDown':
                    topPos += speed;
                    break;
                
                // Move Left
                case 'a':
                case 'A':
                case 'ArrowLeft':
                    leftPos -= speed;
                    break;
                
                // Move Right
                case 'd':
                case 'D':
                case 'ArrowRight':
                    leftPos += speed;
                    break;
            }

            // Update the box's position on the screen
            box.style.top = topPos + 'px';
            box.style.left = leftPos + 'px';
        });
    </script>

</body>
</html>
