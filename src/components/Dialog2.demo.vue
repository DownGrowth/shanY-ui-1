<demo>
一键打开 Dialog 
</demo>
<template>
<div>
  <Button @click="showDialog">打开对话框</Button>
</div>
</template>

<script lang="ts">
import Button from '../lib/Button.vue'
import {
  ref,
  h
} from 'vue'
import {
  openDialog
} from '../lib/openDialog'
export default {
  components: {
    Button
  },
  setup() {
    const showDialog = () => {
      openDialog({
        title: h('normal', {}, '需输入内容才可关闭'),
        content: '请输入内容',
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
    return {
      showDialog
    }
  }
}
</script>