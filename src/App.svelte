<script lang="ts">
  import { onMount } from "svelte";


  onMount(() => {
    const blur_elem = document.getElementById( "blur-around" );
    document.onmousemove = (evt) => {
      console.log(evt);
      
      blur_elem.style.transform = `translate(${evt.clientX}px, ${evt.clientY}px)`;
    };
  });

</script>

<main>
  <div id="blur-around"></div>

  <div class="full-height full-width flex-row">
    <img src="https://images.unsplash.com/photo-1609947991962-8c5fd8ab05c1?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=928&q=80" alt="random image">
  </div>
  <!-- <div class="overlay"></div>
  <div class="container">

  </div> -->
</main>

<style lang="scss">

  #blur-around {
    position: fixed;
    z-index: 999;
    pointer-events: none;
    /* twice the viewport size so it always covers fully */
    width: 200vw;
    height: 200vh;
    /* negative offset by half so we are sure we cover the full viewport */
    left: -100vw;
    top: -100vh;
    /* we'll use transform translate to move it */
    transform-origin: center;  
    -webkit-backdrop-filter: blur(15px);
    backdrop-filter: blur(15px);
    -webkit-mask-image: radial-gradient(50px at 50% 50%, transparent 100%, black 100%);
    mask-image: radial-gradient(50px at 50% 50% , transparent 100%, black 100%)
  }

  .overlay {
    position: absolute;
    inset: 0;
    height: 100vh;
    width: 100vw;
  }

  .container {
    height: 100vh;
    width: 100vw;

    filter: blur(5px);
  }
</style>