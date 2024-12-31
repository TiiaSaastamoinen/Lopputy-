<script>
  export let roll = null;
  export let isRolling = false;
</script>

<div class="dice" class:isRolling>
  {#if roll !== null}
    <span class="dice-number">{roll}</span>
  {/if}
</div>

<style>
  .dice {
    width: 100px;
    height: 100px;
    background-color: #f5f5f5;
    border: 2px solid #333;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 32px;
    font-weight: bold;
    margin-top: 20px;
    transition: transform 1s ease;
  }

  .dice.isRolling {
    animation: spinRight 1s linear;
  }

  @keyframes spinRight {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }

  .dice-number {
    color: #333;
  }
</style>
