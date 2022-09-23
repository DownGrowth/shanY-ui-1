<template>
 <div class="shanY-tabs">
  <div class="shanY-tabs-nav" ref="container">
    <div class="shanY-tabs-nav-item" :class="{selected:t===selected}" @click="select(t)"
     v-for="(t,index) in titles" :ref="el=>{if(t===selected)selectedItem=el}" :key="index">{{t}}</div>
  <div class="shanY-tabs-nav-indicator" ref="indicator"></div>
</div>
  <div class="shanY-tabs-content">
    <component :is="current" :key="current.props.title"/>
  </div>
</div>
</template>
<script lang="ts">
    import Tab from '../lib/Tab.vue'
import { onMounted, ref, watchEffect, computed } from 'vue';
export default {
    props: {
        selected:{
           type:String
        }
    },
    setup(props, context) {
    const selectedItem=ref<HTMLDivElement>(null)
    const indicator = ref < HTMLDivElement > (null)
    const container = ref<HTMLDivElement>(null)
    onMounted(() => {
      watchEffect(() => {
        const {width} = selectedItem.value.getBoundingClientRect() //获取当前selected的宽度
      indicator.value.style.width = width + 'px'
      const {
        left: left1
      } = container.value.getBoundingClientRect()
      const {
        left: left2
      } = selectedItem.value.getBoundingClientRect()
      const left = left2 - left1
      indicator.value.style.left = left + 'px'
      })
    })
        const defaults = context.slots.default()//获取插槽slot内容
        defaults.forEach((tag) => {
            if(tag.type !== Tab) {
                throw new Error('Tabs 子标签必须是Tab')
            }
        })
        const current = computed(() => {
            return defaults.find(tag=>tag.props.title===props.selected) //找到selected对应的title
        }
        )
      const titles= defaults.map((tag) => {
            return tag.props.title  //遍历defaults，找出title
      })
      const select = (title: string) => {
      context.emit('update:selected', title)//选中后通知外部组件update:selected,值是title
    }
        return {defaults,titles,select,selectedItem,indicator,container,current}
    } 
    }

</script>
<style lang="scss">
    $blue:#86bd6d;
$color: #333;
$border-color: #d9d9d9;
.shanY-tabs {
  &-nav {
    display: flex;
    color: $color;
    border-bottom: 1px solid $border-color;
    position: relative;
    &-item {
      padding: 8px 0;
      margin: 0 16px;
      cursor: pointer;
      &:first-child {
        margin-left: 0;
      }
      &.selected {
        color: $blue;
      }
    }
    &-indicator{
      position: absolute;
      height: 3px;
      background: $blue;
      left:0px;
      bottom: -1px;
      width: 100px;
      transition: left 250ms;

}
  }
  &-content {
    padding: 8px 0;
  }
}
</style>