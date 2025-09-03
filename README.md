# stop-watch-
## program

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Stopwatch</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: #f4f4f9;
      font-family: Arial, sans-serif;
    }

    .stopwatch {
      background: #fff;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
      text-align: center;
    }

    .time {
      font-size: 2.5rem;
      font-weight: bold;
      margin-bottom: 20px;
    }

    .buttons button {
      padding: 10px 20px;
      margin: 5px;
      font-size: 1rem;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: 0.3s;
    }

    .buttons button:hover {
      opacity: 0.8;
    }

    .start { background: #28a745; color: white; }
    .pause { background: #ffc107; color: white; }
    .reset { background: #dc3545; color: white; }
  </style>
</head>
<body>
  <div class="stopwatch">
    <div class="time" id="display">00 : 00 : 000</div>
    <div class="buttons">
      <button class="start" onclick="start()">Start</button>
      <button class="pause" onclick="pause()">Pause</button>
      <button class="reset" onclick="reset()">Reset</button>
    </div>
  </div>

  <script>
    let startTime, updatedTime, difference, tInterval;
    let running = false;

    function start() {
      if (!running) {
        startTime = new Date().getTime() - (difference || 0);
        tInterval = setInterval(getShowTime, 10); // update every 10ms
        running = true;
      }
    }

    function pause() {
      if (running) {
        clearInterval(tInterval);
        difference = new Date().getTime() - startTime;
        running = false;
      }
    }

    function reset() {
      clearInterval(tInterval);
      running = false;
      difference = 0;
      document.getElementById("display").innerHTML = "00 : 00 : 000";
    }

    function getShowTime() {
      updatedTime = new Date().getTime() - startTime;

      let minutes = Math.floor((updatedTime / (1000 * 60)) % 60);
      let seconds = Math.floor((updatedTime / 1000) % 60);
      let milliseconds = updatedTime % 1000;

      minutes = (minutes < 10) ? "0" + minutes : minutes;
      seconds = (seconds < 10) ? "0" + seconds : seconds;
      milliseconds = ("00" + milliseconds).slice(-3);

      document.getElementById("display").innerHTML =
        minutes + " : " + seconds + " : " + milliseconds;
    }
  </script>
</body>
</html>

```


## output

![WhatsApp Image 2025-09-03 at 11 11 18_8c3f3076](https://github.com/user-attachments/assets/3be454c4-b88a-4d01-bc09-3e204ea3c811)


![WhatsApp Image 2025-09-03 at 11 11 40_3ab4dbb8](https://github.com/user-attachments/assets/0fdfe313-0e55-4e94-9ffd-eb2b3b09c575)

