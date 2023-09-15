---
title: Classic Pong Game
layout: base
description: Pong
permalink: /frontend/pong
categories: [C4.9]
tags: [javascript]
---

<canvas id="pong" width="800" height="400"></canvas>

```html
<script>
    const canvas = document.getElementById("pong");
    const context = canvas.getContext("2d");

    // Create paddles
    const paddleWidth = 10;
    const paddleHeight = 100;
    let leftPaddleY = canvas.height / 2 - paddleHeight / 2;
    let rightPaddleY = canvas.height / 2 - paddleHeight / 2;
    const paddleSpeed = 5;

    // Create the ball
    let ballX = canvas.width / 2;
    let ballY = canvas.height / 2;
    let ballSpeedX = 5;
    let ballSpeedY = 5;
    const ballSize = 10;

    // Initialize score
    let leftPlayerScore = 0;
    let rightPlayerScore = 0;

    // Control paddles
    function movePaddles() {
        document.addEventListener("keydown", (event) => {
            if (event.key === "ArrowUp" && rightPaddleY > 0) {
                rightPaddleY -= paddleSpeed;
            }
            if (event.key === "ArrowDown" && rightPaddleY < canvas.height - paddleHeight) {
                rightPaddleY += paddleSpeed;
            }
            if (event.key === "w" && leftPaddleY > 0) {
                leftPaddleY -= paddleSpeed;
            }
            if (event.key === "s" && leftPaddleY < canvas.height - paddleHeight) {
                leftPaddleY += paddleSpeed;
            }
        });
    }

    // Update the game
    function update() {
        // Move the ball
        ballX += ballSpeedX;
        ballY += ballSpeedY;

        // Ball collision with top and bottom walls
        if (ballY < 0 || ballY > canvas.height) {
            ballSpeedY = -ballSpeedY;
        }

        // Ball collision with paddles
        if (
            ballX < paddleWidth &&
            ballY > leftPaddleY &&
            ballY < leftPaddleY + paddleHeight
        ) {
            ballSpeedX = -ballSpeedX;
        }
        if (
            ballX > canvas.width - paddleWidth - ballSize &&
            ballY > rightPaddleY &&
            ballY < rightPaddleY + paddleHeight
        ) {
            ballSpeedX = -ballSpeedX;
        }

        // Ball out of bounds
        if (ballX < 0) {
            rightPlayerScore++;
            resetBall();
        }
        if (ballX > canvas.width) {
            leftPlayerScore++;
            resetBall();
        }
    }

    // Reset the ball to the center
    function resetBall() {
        ballX = canvas.width / 2;
        ballY = canvas.height / 2;
        ballSpeedX = -ballSpeedX;
    }

    // Draw everything
    function draw() {
        // Clear the canvas
        context.fillStyle = "black";
        context.fillRect(0, 0, canvas.width, canvas.height);

        // Draw paddles
        context.fillStyle = "white";
        context.fillRect(0, leftPaddleY, paddleWidth, paddleHeight);
        context.fillRect(
            canvas.width - paddleWidth,
            rightPaddleY,
            paddleWidth,
            paddleHeight
        );

        // Draw the ball
        context.beginPath();
        context.arc(ballX, ballY, ballSize, 0, Math.PI * 2);
        context.fillStyle = "white";
        context.fill();

        // Draw the scores
        context.fillStyle = "white";
        context.font = "30px Arial";
        context.fillText(leftPlayerScore, canvas.width / 4, 30);
        context.fillText(rightPlayerScore, (3 * canvas.width) / 4, 30);
    }

    // Game loop
    function gameLoop() {
        movePaddles();
        update();
        draw();
        requestAnimationFrame(gameLoop);
    }

    // Start the game loop
    gameLoop();
</script>
