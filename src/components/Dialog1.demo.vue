<demo>
    常规使用
    </demo>
    <template>
    <div>
      <Button @click="toggle">打开对话框</Button>
      <Dialog v-model:visible="x" :closeOnClickOverlay="f3" :ok="f1" :cancel="f2">
        <template v-slot:content>
          <strong>hi</strong>
          <div>hi2</div>
        </template>
        <template v-slot:title>
          <strong>加粗的标题 (点击周围可关闭)</strong>
        </template>
      </Dialog>
    </div>
    </template>
    
    <script lang="ts">
    import {Dialog} from '../lib/index'
    import {Button} from '../lib/index'
    import {
      ref
    } from 'vue'
    import {
      openDialog
    } from '../lib/openDialog'
    export default {
      components: {
        Dialog,
        Button
      },
      setup() {
        const x = ref(false)
        const toggle = () => {
          x.value = !x.value
        }
        const f1 = () => {
          return true
        }
          const f2 = () => { }
          const f3 = () => {return true}
        return {
          x,
          toggle,
          f1,
            f2,
          f3
        }
      }
    }
    </script>