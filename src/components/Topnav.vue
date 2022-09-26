<template>
    <div class="topnav">
        <router-link to="/" class="logo">
            <svg class="icon">
    <use xlink:href="#icon-leaf"></use>
</svg>
</router-link>
        
        <ul class="menu">
            <li>
      <router-link to="/doc">文档</router-link>
    </li>
        </ul>
        <svg v-if="toggleMenuButtonVisible" class="toggleAside" @click="toggleAside">
        <use xlink:href="#icon-menu"></use></svg>
    </div>

</template>
<script lang="ts">
import { inject, Ref } from 'vue';
export default {
    props: {
        toggleMenuButtonVisible: {
            type: Boolean,
            default:false
        }
    },
    setup(){
        const asideVisible = inject<Ref<boolean>>('asideVisible')
        const toggleAside = () => {
            asideVisible!.value=!asideVisible!.value
            
        }
    return{asideVisible,toggleAside}
   }
}
</script>

<style lang="scss" scoped>
    $color:#5d4b5f;
    @media screen and (max-width:800px){
    .topnav{
        position: fixed;
      background: rgb(240, 245, 236);
      height: 42px;
      box-shadow: 0 0 3px rgb(0 0 0 / 25%);
    }
  }
    .topnav{
        color:$color;
        display: flex;
        padding: 16px;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        justify-content: center;
        align-items: center;
        z-index: 20;
        >.logo{
            max-width: 6em;
            margin-right: auto;
            :hover{
                animation: shanY-shake 1s infinite linear;
            }
            >svg{
                width: 32px;
                height: 32px;
            }
        }
        >.menu {
            display: flex;
            white-space: nowrap;
            flex-wrap: nowrap;
            >li{
                margin: 0 1em;
            }
        }
        >.toggleAside{
            display: inline-block;
            width: 24px;
            height: 24px;
            position: absolute;
            left:16px;
            top:50%;
            transform: translateY(-50%);
            display: none;
        }
        @media (max-width:500px){
            >.menu{display: none;}
            >.logo{
                margin: 0 auto;
            }
            >.toggleAside{
                display: inline-block;
            }
        }
        @keyframes shanY-shake{
            0%   {
                transform:rotate(0deg);
            }
            25%  {
                transform:rotate(8deg);}
            38%  {
                transform:rotate(-6deg);}
            50%  {
                transform:rotate(6deg);}
            62%  {
                transform:rotate(-4deg);}
            75%  {
                transform:rotate(2deg);}
            100% {
                transform:rotate(0deg);}
    }
    }
</style>