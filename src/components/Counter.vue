<script setup lang="ts">
import { ref, onMounted } from 'vue'
import fetchCount from '../fetchCount'

// defineProps is a Compiler Macro which can be used with TypeScript and setup annotation, it allows us to declare props without importing it, it's executed in the compile-time.
/*const props = defineProps<{ 
  limit: number;
  alertMessage: string;
 }>()
*/
interface Props {
  limit: number;
  alertMessageOnLimit?: string;
}

// withDefaults is another Compiler Macro which allows you to set default values to props
const props = withDefaults(defineProps<Props>(), {
  alertMessageOnLimit: 'Cannot go any higher!'
})

// We must define the type here since we're getting the inital count from an external source
const count = ref<number>(0)

onMounted(() => {
  fetchCount((initialCount) => {
    count.value = initialCount
  })
})

function addCount(num: number){ 
  if (count.value !== null){
    if (count.value >= props.limit) {
      alert(props.alertMessageOnLimit)
    } else {
      count.value += num
    }
  }
}

</script>

<template>
  <div>
    <p>Count: {{ count }}</p>
    <button type="button" @click="addCount(1)">Add</button>
  </div>
</template>

<style scoped>
</style>
