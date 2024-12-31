<script>
  import Noppa from './Noppa.svelte';
  import Pelihistoria from './Pelihistoria.svelte';

  let pelaaja = '';
  let roll = null;
  let isRolling = false;
  let history = [];

  const rollDice = () => {
    if (!pelaaja) {
      alert('Anna nimesi ennen pyöräytystä!');
      return;
    }

    isRolling = true;
    let intervalId = setInterval(() => {
      roll = Math.floor(Math.random() * 6) + 1;
    }, 100);

    setTimeout(() => {
      clearInterval(intervalId);
      history = [...history, { name: pelaaja, roll }];

      isRolling = false;
    }, 1000);
  };
</script>

<h1 class="title">Noppapeli</h1>
<hr class="divider" />

<div class="game-area">
  <div class="dice-container">
    <Noppa {roll} {isRolling} />
  </div>

  <div class="controls">
    <input
      type="text"
      bind:value={pelaaja}
      placeholder="Syötä nimesi"
      class="input"
    />
    <button on:click={rollDice} disabled={isRolling} class="button">
      Pyöräytä
    </button>
  </div>
</div>
<div class="container">
  <div class="sidebar">
    <Pelihistoria {history} />
  </div>
</div>

<style>
  h1 {
    text-align: center;
    font-size: 80px;
    margin: 0;
    padding: 10px 0;
    color: #000000;
  }
  .divider {
    width: 100%;
    border: none;
    border-top: 2px solid black;
    margin: 20px 0;
  }

  .container {
    display: flex;

    align-items: flex-start;
    justify-content: center;
    padding: 10px;
    gap: 900px;
  }

  .game-area {
    flex: 2;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
  }

  .dice-container {
    margin-top: 30px;
    align-items: center;
  }

  .controls {
    margin-top: 20px;
    display: flex;
    flex-direction: row;
    gap: 10px;
    align-items: center;
    background-color: #ccc;
  }

  .input {
    padding: 10px;
    font-size: 1.1em;
    width: 200px;
  }

  .button {
    padding: 10px 20px;
    font-size: 1.1em;
    background-color: #6e6e6e;
    border: none;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  .button:disabled {
    background-color: #ddd;
    cursor: not-allowed;
  }

  .button:hover:not(:disabled) {
    background-color: #ccc;
  }
</style>
