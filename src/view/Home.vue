<template>
  <div>
    <div class="topnavAndBanner">
        <Topnav/>
        <div class="banner">
            <h1>shanY UI</h1>
            <h2>一个好用的UI框架</h2>
            <p class="actions">
               <a href="https://github.com">Github</a> 
               <router-link to="/doc">开始</router-link> 
            </p>
        </div>
        </div>
        <div class="features">
          <ul>
      <li>
        <svg>
          <use xlink:href="#icon-vue"></use>
        </svg>
        <h3>基于 Vue 3</h3>
        <p>骄傲地使用了 Vue 3 Composition API</p>
      </li>
      <li>
        <svg>
          <use xlink:href="#icon-ts"></use>
        </svg>
        <h3>基于 TypeScript </h3>
        <p>源代码采用 TypeScript 书写（非严格检查）</p>
      </li>
      <li>
        <svg>
          <use xlink:href="#icon-light"></use>
        </svg>
        <h3>代码易读</h3>
        <p>每个组件的源代码都极其简洁</p>
      </li>
    </ul>
</div>
    </div>
    <div class="shanY-bottom">
    <span class="shanY-bottom-big"></span>
    <span class="shanY-bottom-little"></span>
    <span class="shanY-bottom-mid"></span>
  </div>
</template>
<script lang="ts">
import Topnav from '../components/Topnav.vue'
export default {
        components:{Topnav}
    }
</script>
<style lang="scss" scoped>
  $green:#9bcfb1;
  $border-radius:4px;
  $color:#6a5f72;

  @media screen and (max-width:800px){
    .shanY-bottom{
      display: none;
    }
  }
  .shanY-bottom-big{
    position: fixed;
    right: 26vw;
    bottom: 0;
    transform: translateY(50%);
    min-width: 1200px;
    min-height: 250px;
    background: rgb(243, 241, 250);
    clip-path: ellipse(50% 80% at 38% 80%);
    z-index: -1;
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
    z-index: 10;
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
    }
  .topnavAndBanner{
    background: linear-gradient(145deg, rgba(2,0,36,1) 0%, rgba(249,255,239,1) 0%, rgba(231,238,237,1) 100%);
    clip-path: ellipse(80% 60% at 50% 40%);
  }
.features{
  margin: 32px auto 100px;
  width: 400px;
  @media (min-width: 800px) {
    width: 800px;
  }
  @media (min-width: 1200px) {
    width: 1200px;
  }
  >ul {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin-block-start: 0em;
    margin-block-end: 1em;
    margin-inline-start: 8px;
    >li {
      margin: 8px;
    display: flex;
    width: 300px;
    padding: 0 40px;
    flex-direction: column;
    align-items: center;
    justify-content: center;

      >svg {
        width: 64px;
        height: 64px;
      }
      >h3 {
        display: block;
        margin-block-start: 0.2em;
    margin-block-end: 1em;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
      }
      >p {
    display: block;
    margin-block-start: -1em;
    margin-block-end: 0em;
    margin-inline-start:0px;
    margin-inline-end: 0px;
    font-size: 12px;
    text-align: center;
      }
    }
  }
}
.banner {
  color:$color;
  padding: 64px 0;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  > .actions{
    padding: 8px 0;
    a {
      margin:0 8px;
      background: $green;
      color:#e6fac0;
      display: inline-block;
      padding: 8px 24px;
      border-radius: $border-radius;
      &:hover{
        text-decoration: none;
      }
    }
  }
}
</style>