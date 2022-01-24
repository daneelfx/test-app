<script>
  let mainText = ''

  const setMainText = evt => {
    mainText = evt.target.value
  }

  const randomColor = () => {
    const R = Math.ceil(Math.random() * 255)
    const G = Math.ceil(Math.random() * 255)
    const B = Math.ceil(Math.random() * 255)

    return `rgb(${R}, ${G}, ${B})`
  }

  $: mainTextUppercase = mainText.toUpperCase()
  $: mainColor = (mainText.length && randomColor()) || 'rgb(51, 51, 51)'
</script>

<main style="background-color: {mainColor}">
  {#if mainTextUppercase !== 'UNAL'}
    <p>{mainTextUppercase}</p>
  {:else}
    <p>❤️ {mainTextUppercase} ❤️</p>
  {/if}
</main>
<aside>
  <input style="border: 4px solid {mainColor}" type="text" bind:value={mainText} />
</aside>

<style>
  main,
  aside {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  main {
    height: 70%;
  }

  aside {
    height: 30%;
  }

  p {
    font-size: 8rem;
    text-align: center;
    color: #333;
    text-shadow: -4px 0 #fff, 0 4px #fff, 4px 0 #fff, 0 -4px #fff;
  }

  input {
    width: 30%;
    height: 20%;
    text-align: center;
    font-family: inherit;
    outline: none;
    border-radius: 6px;
  }
</style>
