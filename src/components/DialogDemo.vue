<template>
    <Demo :component="Dialog1Demo" />
<Demo :component="Dialog2Demo" />
    <!-- 示例2中的ok等交由传给openDialog的ok自己控制 -->
    <!-- 示例1、2的ok等都是由Dialog组件判断 -->
</template>
<script lang="ts">
import Demo from './Demo.vue';
import Dialog1Demo from './Dialog1.demo.vue';
import Dialog2Demo from './Dialog2.demo.vue';
export default {
    components: {
        Demo
    },
    setup() {
       
        // const showDialog = () => {
        //     openDialog({
        //         title: '标题',
        //         content: '内容',
        //         ok() {
        //             console.log('ok')
        //             return false
        //         },
        //         cancel() {
        //             console.log('cancel')
        //         },
        //         closeOnClickOverlay() {
        //             console.log('123')
        //             return false
        //         }
        //     })
        // }
            return { Dialog1Demo,
      Dialog2Demo}
        }
    }
</script>