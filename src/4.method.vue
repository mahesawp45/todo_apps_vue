<template>
  <div>
    <div>Counter : {{ value }} </div>
    <button @click="add" >Add</button>
  </div>
</template>

<script>
import { reactive, toRefs } from "vue";

export default {

  setup() {
    const counter = reactive({
      value: 0
    })

    // Method
    const add = () => {
      counter.value++
    }

    return {
      ...toRefs(counter), add
    }
  }
  
}
</script>