---
toc: true
comments: true
layout: post
title: VSCode, JS ...
description: Simple Calculator in JS.
courses: { csse: {week: 0}, csp: {week: 0}, csa: {week: 0} }
type: hacks
---

# Simple Calculator

```html
<!DOCTYPE html>
<html>
<head>
    <title>Simple Calculator</title>
</head>
<body>
    <h2>Calculator</h2>
    <input type="text" id="result" readonly>
    <br>
    <button onclick="appendToResult('1')">1</button>
    <button onclick="appendToResult('2')">2</button>
    <button onclick="appendToResult('3')">3</button>
    <button onclick="appendToResult('+')">+</button>
    <br>
    <button onclick="appendToResult('4')">4</button>
    <button onclick="appendToResult('5')">5</button>
    <button onclick="appendToResult('6')">6</button>
    <button onclick="appendToResult('-')">-</button>
    <br>
    <button onclick="appendToResult('7')">7</button>
    <button onclick="appendToResult('8')">8</button>
    <button onclick="appendToResult('9')">9</button>
    <button onclick="appendToResult('*')">*</button>
    <br>
    <button onclick="appendToResult('0')">0</button>
    <button onclick="calculateResult()">=</button>
    <button onclick="clearResult()">C</button>
    <button onclick="appendToResult('/')">/</button>
    <script>
        function appendToResult(value) {
            document.getElementById("result").value += value;
        }

        function calculateResult() {
            let resultField = document.getElementById("result");
            let result = eval(resultField.value);
            resultField.value = result;
        }

        function clearResult() {
            document.getElementById("result").value = "";
        }
    </script>
</body>
</html>
