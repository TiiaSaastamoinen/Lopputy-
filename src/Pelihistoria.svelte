<script>
  export let history = [];
</script>

<div class="history-container">
  <h3 class="history-title">Pelihistoria:</h3>
  <table>
    <thead>
      <tr>
        <th>Pelaajan nimi</th>
        <th>Heitetty numero</th>
      </tr>
    </thead>
    <tbody>
      {#each history as game (game.name + game.roll)}
        <tr>
          <td>{game.name}</td>
          <td>{game.roll}</td>
        </tr>
        <tr>
          <td colspan="2"><hr class="history-divider" /></td>
        </tr>
      {/each}
    </tbody>
  </table>
</div>

<style>
  .history-container {
    border: 2px solid red;
    padding: 10px;
    width: 300px;
  }

  .history-title {
    margin-bottom: 10px;
    font-weight: bold;
  }

  table {
    width: 100%;
    margin-top: 20px;
    border-collapse: collapse;
  }

  th,
  td {
    padding: 8px;
    text-align: center;
  }

  th {
    background-color: #f2f2f2;
  }

  .history-divider {
    border-top: 1px solid black;
    margin-top: 10px;
  }
</style>
