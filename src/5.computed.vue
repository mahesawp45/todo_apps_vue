<template>
  <div>
    <div>Counter : {{ nilai }} </div>
    <button @click="add" >Add</button>
    <div>Result dari Computed : {{ result }} </div>

  </div>
</template>

<script>
import { reactive, ref, computed, toRefs } from 'vue';

export default {
  setup() {
    const counter = reactive({
      nilai: 0
    })

    const addNum = ref(1)

    // method
    const add = () => counter.nilai++

    // computed
    const result = computed(() => counter.nilai + addNum.value)

    return {
      ...toRefs(counter), add, result
    }

  }
}
</script>