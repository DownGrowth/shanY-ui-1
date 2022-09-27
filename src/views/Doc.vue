<template>

  <div class="layout">
    <Topnav :toggleMenuButtonVisible="true" class="nav"/>
    <div class="content" >
    <transition name="slide">
      <Aside  v-if="asideVisible" />
    </transition>
   
      <main @click="toggleAsideVisible">
        <div class="darken" v-if="asideVisible"></div>
        <router-view/>
      </main>

    </div>
  </div>
  <Mountain />
</template>
<script lang="ts">
import { inject, reactive, Ref, watchEffect, onMounted, onUnmounted } from 'vue';
import Topnav from '../components/Topnav.vue'
import Mountain from './Mountain.vue';
import Aside from './Aside.vue';
import {
    debounce
} from '../utils/debounce';
export default {
 
components: { Topnav, Mountain, Aside },
  setup() {
    const asideVisible = inject<Ref<boolean>>('asideVisible')
      const data = reactive({
            listenerPageWidthFn: () => {},
            pageWidth: document.documentElement.clientWidth
      })
      const watchPageWidth = () => {
            const listenerPageWidth = debounce(() => {
                data.pageWidth = document.documentElement.clientWidth;
            }, 300);
            window.addEventListener("resize", listenerPageWidth);
            return listenerPageWidth;
        };
    const toggleAsideVisible = () => {
      if (data.pageWidth <= 500){ asideVisible!.value=false}
    }
    watchEffect(() => {
            if (data.pageWidth >= 500) {
              asideVisible!.value = true;
            }
        })
        onMounted(() => {
            data.listenerPageWidthFn = watchPageWidth();
        })
        onUnmounted(() => {
            window.removeEventListener("resize", data.listenerPageWidthFn);
        })
  return {data,asideVisible,toggleAsideVisible,watchPageWidth}
 }     
  }
</script>
<style lang="scss" scoped>
  @media screen and (max-width:500px){
    .slide-enter-active{
      animation: shanY-slide 0.15s linear;
    }
    .slide-leave-active{
      animation: shanY-slide 0.15s reverse linear;
    }
    .darken{
  position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: fade_out(black, 0.5);
  }


}
.layout {
display: flex;
flex-direction: column;
height: 100vh;
> .content {
  flex-grow: 1;
  padding-top: 60px;
  padding-left: 156px;
  @media (max-width: 500px) {
    padding-left: 0; 
  }
}
}
.content {
display: flex;

> aside {
  flex-shrink: 0;
  z-index: 6;
}
> main {
  flex-grow: 1;
  padding: 16px;
  background: rgba(239, 248, 238, 0.4);
  z-index: 5;
}
}
main {
overflow: auto;
}
@keyframes shanY-slide{
    from{
transform: translateX(-100px);
}
to{
transform: translateX(0px);
}
    }
</style>