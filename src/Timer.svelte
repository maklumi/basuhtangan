<script>
  import { createEventDispatcher } from 'svelte'
  import Progressbar from './Progressbar.svelte'
  const totalmasa = 10
  let masatinggal = totalmasa
  let isrunning = false

  $: progress = ((totalmasa - masatinggal) / totalmasa) * 100

  const dispatch = createEventDispatcher()

  function handleClick() {
    isrunning = true
    const pemasa = setInterval(() => {
      masatinggal -= 1
      if (masatinggal == 0) {
        isrunning = false
        masatinggal = totalmasa
        dispatch('habis', 'masa habis')
        clearInterval(pemasa)
      }
    }, 1000)
  }
</script>

<style>
  h2 {
    margin: 0;
  }
  .start {
    background-color: rgb(154, 73, 73);
    width: 100%;
    margin: 10px 0;
  }
  button:disabled {
    background-color: yellow;
    cursor: not-allowed;
  }
</style>

<div bp="grid">
  <h2 bp="offset-5@md 4@md 12@sm">Saat lagi: {masatinggal}</h2>
</div>

<Progressbar {progress} />
<div bp="grid">
  <button
    disabled={isrunning}
    vbp="offset-5@md 4@md 12@sm"
    class="start"
    on:click={handleClick}>
    Mulakan
  </button>
</div>
