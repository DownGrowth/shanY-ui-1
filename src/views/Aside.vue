<template>

    <aside v-if="asideVisible"  >
      <h2>文档</h2>
      <ol>
        <li>
          <router-link to="/doc/intro">介绍</router-link>
        </li>
      
        <li>
          <router-link to="/doc/install">安装</router-link>
        </li>
        <li>
          <router-link to="/doc/get-started">开始使用</router-link>
        </li>
      </ol>
      <h2>组件列表</h2>
      <ol>
        <li>
          <router-link to="/doc/switch">Switch 组件</router-link>
        </li>
        <li>
          <router-link to="/doc/button">Button 组件</router-link>
        </li>
        <li>
          <router-link to="/doc/dialog">Dialog 组件</router-link>
        </li>
        <li>
          <router-link to="/doc/tabs">Tabs 组件</router-link>
        </li>
      </ol>
    </aside>

</template>

<script lang="ts">
    import { inject, Ref} from 'vue';
export default {
   
    setup() {
        const asideVisible = inject<Ref<boolean>>('asideVisible')
            
        return { asideVisible}   
          
            }
    }
</script>

<style lang="scss">
   
@media screen and (max-width:800px){
  .layout>.content>aside{
      background:rgb(246,246,237);
    }
  }
aside{
  background: rgba(209, 209, 164,0.2);
  width:150px;
  padding:16px 0;
  position: fixed;
top: 0;
left: 0;
padding-top: 70px;
height: 100%;
  
  >h2{
    margin-bottom:4px;
    padding:0 12px;
  }
  >ol{
    >li{
      >a{
        display: block;
        text-decoration: none;
         padding: 4px 20px;

      }
      .router-link-active{
        background:  #e4f5e8;
        
  }
    }
  }
  /* @keyframes shanY-slide{
    from{
transform: translateX(-100px);
}
to{
transform: translateX(0px);
}
    } */
}
</style>