<template>
    <div>
       <h1>示例1</h1>
       <div>
        <Button>你好</Button>
        <Button theme="button">你好</Button>
        <Button theme="link">你好</Button>
        <Button theme="text">你好</Button>
       </div>
       <h1>示例2</h1>
       <div>
        <Button size="big">大大</Button>
        <Button>普通</Button>
        <Button size="small">小小</Button>
       </div>
       <div>
        <Button size="big" theme="link">大大</Button>
        <Button theme="link">普通</Button>
        <Button size="small" theme="link">小小</Button>
       </div>
       <div>
        <Button size="big" theme="text">大大</Button>
        <Button theme="text">普通</Button>
        <Button size="small" theme="text">小小</Button>
       </div>
       <h1>示例3</h1>
       <div>
        <Button level="main">主要</Button>
        <Button >正常</Button>
        <Button level="danger">危险</Button>
    </div>
    <div>
        <Button theme="link" level="main">主要</Button>
        <Button theme="link">正常</Button>
        <Button theme="link" level="danger" >危险</Button>
       </div>
       <div>
        <Button theme="text" level="main" >主要</Button>
        <Button theme="text">正常</Button>
        <Button theme="text" level="danger" >危险</Button>
       </div>
       <h1>示例4</h1>
       <div>
        <Button disabled>禁用按钮</Button>
    <Button theme="link" disabled>禁用链接按钮</Button>
    <Button theme="text" disabled>禁用按钮</Button>
       </div>
       <h1>示例5</h1>
       <div>
        <Button loading>加载中</Button>
        <Button>加载完毕</Button>
       </div>
    </div>
</template>

<script lang="ts">
import  Button  from "../lib/Button.vue";
export default {
    components: { Button },
    setup() {
        const onClick = () => {
                console.log('hi')
        }
            return{onClick}
        }
    }
</script>
<style lang="scss">
    h1{
        margin-top: 20px;
        margin-bottom: 20px;
    }
</style>