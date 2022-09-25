
<template>
    <button class="shanY-switch" @click="toggle" :class="{'shanY-checked':value}">
        <span></span>
    </button>
</template>
<script lang="ts">

export default {
    props: {
        value:Boolean
    },
    setup(props,context) {
        const toggle = () => {
            context.emit('update:value',!props.value)//通过input事件把当前值取反
        }
            return{toggle}
        }
        
    }
</script>
<style lang="scss">
$h:22px;
$h2:$h - 4px;
.shanY-switch{
    height: $h;
    width: $h*2;
    border:none;
    background: #bfbfbf;
    border-radius: $h/2;
    position: relative;
    margin-top: 24px;
    > span{
    position: absolute;
    top: 2px;
    left: 2px;
    height: $h2;
    width: $h2;
    background: white;
    border-radius: $h2/2;
    transition: all 250ms;
}
&.shanY-checked{
    background: #86bd6d;
    > span{
        left:calc(100% - #{$h2} - 2px)
    }
}
&:focus{
    outline: none;
}
&:active{
    > span{
        width: $h2+4px;
    }
}
&.shanY-checked:active{
    > span{
        width: $h2 +4px;
        margin-left: -4px;
    }
}
}


</style>