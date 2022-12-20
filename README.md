<!-- HTML Markup for the prize wheel -->
<div id="prize-wheel">
  <div class="outer-circle">
    <div class="inner-circle">
      <!-- Add a div element for each prize section -->
      <div class="prize-section">Prize 1</div>
      <div class="prize-section">Prize 2</div>
      <div class="prize-section">Prize 3</div>
      <!-- Add additional prize sections as needed -->
    </div>
  </div>
</div>

<!-- Add a button to spin the wheel -->
<button id="spin-button">Spin the wheel</button>

<!-- Style the prize wheel using CSS -->
<style>
  #prize-wheel {
    position: relative;
    width: 300px;
    height: 300px;
  }

  .outer-circle {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border: 2px solid black;
    border-radius: 50%;
    overflow: hidden;
  }

  .inner-circle {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 90%;
    height: 90%;
    border: 2px solid black;
    border-radius: 50%;
  }

  .prize-section {
    position: absolute;
    top: 0;
    left: 0;
    width: 50%;
    height: 50%;
    text-align: center;
    line-height: 150px;
    font-size: 24px;
  }
</style>

<!-- Add the JavaScript to spin the wheel -->
<script>
  // Get the spin button and prize wheel elements
  const spinButton = document.getElementById('spin-button');
  const prizeWheel = document.getElementById('prize-wheel');

  // Add a click event listener to the spin button
  spinButton.addEventListener('click', spinWheel);

  function spinWheel() {
    // Generate a random number between 0 and 360
    const spinAngle = Math.floor(Math.random() * 360);

    // Set the prize wheel's transform to the random angle
    prizeWheel.style.transform = `rotate(${spinAngle}deg)`;
  }
</script>
