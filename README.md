<!-- HTML Markup for the game interface -->
<div id="game">
  <div id="score">Score: <span id="score-value">0</span></div>
  <button id="click-button">Click</button>
  <div id="upgrades">
    <!-- Add an upgrade button for each upgrade -->
    <button class="upgrade-button" data-cost="100" data-multiplier="2">Upgrade 1</button>
    <button class="upgrade-button" data-cost="1000" data-multiplier="5">Upgrade 2</button>
    <!-- Add additional upgrade buttons as needed -->
  </div>
</div>

<!-- Style the game interface using CSS -->
<style>
  #game {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  #score {
    font-size: 24px;
  }

  #click-button {
    width: 150px;
    height: 75px;
    font-size: 24px;
    background-color: lightblue;
    border: none;
    border-radius: 10px;
  }

  .upgrade-button {
    width: 200px;
    height: 50px;
    margin: 10px 0;
    font-size: 18px;
    background-color: lightgreen;
    border: none;
    border-radius: 10px;
  }

  .upgrade-button[disabled] {
    background-color: gray;
  }
</style>

<!-- Add the JavaScript to handle the game logic -->
<script>
  // Get the game elements
  const clickButton = document.getElementById('click-button');
  const scoreValue = document.getElementById('score-value');
  const upgrades = document.querySelectorAll('.upgrade-button');

  // Initialize the game state
  let score = 0;
  let multiplier = 1;

  // Add a click event listener to the click button
  clickButton.addEventListener('click', () => {
    // Increment the score by the multiplier
    score += multiplier;

    // Update the score display
    scoreValue.textContent = score;
  });

  // Add a click event listener to the upgrade buttons
  upgrades.forEach(upgradeButton => {
    upgradeButton.addEventListener('click', () => {
      // Get the cost and multiplier for the upgrade
      const cost = Number(upgradeButton.dataset.cost);
      const newMultiplier = Number(upgradeButton.dataset.multiplier);

      // Check if the player has enough points to purchase the upgrade
      if (score >= cost) {
        // Decrement the score by the cost
        score -= cost;

        // Update the multiplier and score display
        multiplier = newMultiplier;
        scoreValue.textContent = score;

        // Enable the next upgrade button
        const nextUpgradeButton = upgradeButton.nextElementSibling;
        if (nextUpgradeButton) {
          nextUpgradeButton.disabled = false;
        }
      }
    });
  });
</script>
