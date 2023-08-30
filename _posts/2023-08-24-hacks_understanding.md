---
title: Hacks (Calculator)
layout: default
description: Hackcs 
permalink: /student/calcu
categories: []
tags: [javascript, fetch, dom, getElementID, appendChild]
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

____________________

## Notes
- Take note and describe the type of shell commands that you are using through Terminal in this installation procedure.
- - wsl, cd, git, apt, brew, …
Terminal commands used: wsl - to access Windows Subsystem for Linux, cd - change directory, git - version control, apt - package manager for Linux, brew - package manager for macOS.

- In the Development process, developers use Version control. Annotate in notes what you have learned about Version Control while doing this setup process.
Version control allows developers to track and manage changes to their codebase over time, facilitating collaboration and maintaining a history of modifications.

- Where are the files from GitHub placed on your local machine. How do you navigate to those files.
Files from GitHub are placed in the local directory you specify during cloning. Navigate using 'cd' command to the directory path.

- Where are the files placed in the GitHub Cloud, how do you navigate to those files.
Files on GitHub cloud are stored in the repository you cloned from. Navigate using the GitHub website or a Git client.

- How would you update your Template or Fork of student repository if teacher wanted you to pick up an update?
To update a Template or Fork, pull changes from the upstream repository into your local repository using Git commands.

- Put into words the difference between viewing GitHub Pages running on localhost machine versus running on a deployed server.
Viewing GitHub Pages on localhost shows the website on your local machine, while on a deployed server, it's accessible globally through the internet.

- What is the localhost URL for your distribution? Can anyone else see it?
No one else can see it, http://127.0.0.1:4000/student/student/calc

- What is the GitHub Pages URL for your distribution? Can anyone else see it?
Yes others can see it, aaron-rubstudent.com

- DNS is the address manager for the internet. Put into your own words how you changed the domain name of your student repository. Did you change the address?