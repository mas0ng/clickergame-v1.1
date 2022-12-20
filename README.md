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
  <div id="save-section">
    <button id="save-button">Save</button>
    <input id="save-code" type="text" placeholder="Save code" />
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

  #save-section {
    display: flex;
    align-items: center;
  }

  #save-button,
  #save-code {
    height: 30px;
    font-size: 18px;
  }

  #save-button {
    margin-right: 10px;
    background-color: lightyellow;
    border: none;
    border-radius: 10px;
  }

  #save-code {
    flex-grow: 1;
    padding: 0 10px;
    border: 1px solid gray;
    border-radius: 10px;
  }
</style>

<!-- Add the JavaScript to handle the game logic -->
<script>
  // Get the game elements
  const clickButton = document.getElementById('click-button');
  const scoreValue = document.getElementById('score-value');
  const upgrades = document.querySelectorAll('.upgrade-button');
  const saveButton = document.getElementById('save-button');
  const saveCode = document.getElementById('save-code');

  // Initialize the game state
  let score = 0;
  let multiplier = 1;

  // Add a click event
