<script>
  import Timer from './Timer.svelte'
  import Howto from './Howto.svelte'
  let audio

  function handleHabis() {
    console.log('abeehh')
    audio.play()
  }
</script>

<style>
  h1,
  h3 {
    text-align: center;
  }
</style>

<h1>Basuh Tangan</h1>

<Timer on:habis={handleHabis} />

<Howto />

<h3>
  <a href="https://www.who.int/gpsc/clean_hands_protection/en/">Punca gambar</a>
  <a href="https://freesound.org/people/metrostock99/sounds/345086/">
    Punca bunyi
  </a>
</h3>

<audio src="bunyiohyeah.wav" bind:this={audio} />
