<template>
    <div class="shanY-bottom">
        <span class="shanY-bottom-big"></span>
    <span class="shanY-bottom-little"></span>
    <span class="shanY-bottom-mid"></span>
    </div>
</template>
<script lang="ts">
export default {
    
}
</script>
<style lang="scss">
    @media screen and (max-width:800px){
    .shanY-bottom{
      display: none;
    }
  }
  .shanY-bottom-big{
    position: fixed;
    right: 26vw;
    bottom: 0px;
    transform: translateY(50%);
    min-width: 1200px;
    min-height: 250px;
    background: rgb(243, 241, 250);
    clip-path: ellipse(40% 80% at 38% 80%);
    z-index: 3;
  }
  .shanY-bottom-little{
      position: fixed;
    bottom: -100px;
    left: 54%;
    width: 300px;
    height: 100px;
    background: #bee6c9;
    clip-path: ellipse(60% 70% at 50% 90%);
    transform: translate(-50%,-50%);
    z-index: 5;
    }
    .shanY-bottom-mid{
      position: fixed;
    bottom: -100px;
    left: 45%;
    width: 600px;
    height: 100px;
    background: rgb(214, 230, 243);
    clip-path: ellipse(50% 70% at 50% 80%);
    transform: translate(-50%,-50%);
    z-index: 4;
    }
</style>