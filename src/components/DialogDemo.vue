<template>
    <div>Dialog 示例</div>
    <h1>示例1</h1>
    <Button @click="toggle">toggle</Button>
    <Dialog v-model:visible="x" 
    :closeOnClickOverlay="f3" :ok="f1" :cancel="f2"> 
    <!-- 示例1中的ok等函数由传入的f1控制 -->
        <template v-slot:content>
            <strong>hi</strong>
            <div>1</div> 
        </template>
         <template v-slot:title>
            <strong>加粗的标题</strong>
        </template>
    </Dialog>
    <h1>示例2</h1>
    <Button @click="showDialog">show</Button>
    <!-- 示例2中的ok等交由传给openDialog的ok自己控制 -->
    <!-- 示例1、2的ok等都是由Dialog组件判断 -->
</template>
<script lang="ts">
import Dialog from '../lib/Dialog.vue'
import Button from '../lib/Button.vue'
import { ref } from 'vue';
import { openDialog } from '../lib/openDialog';
export default {
    components: {
        Dialog,
            Button
    },
    setup() {
        const x = ref(false)
        const toggle = () => {
            x.value=!x.value
        }
        const f1 = () => {
            return false
        }
        const f2 = () => {
        }
        const f3 = () => {
            return true
        }      
        const showDialog = () => {
            openDialog({
                title: '标题',
                content: '内容',
                ok() {
                    console.log('ok')
                    return false
                },
                cancel() {
                    console.log('cancel')
                },
                closeOnClickOverlay() {
                    console.log('123')
                    return false
                }
            })
        }
            return {x,toggle,f1,f2,f3,showDialog}
        }
    }
</script>