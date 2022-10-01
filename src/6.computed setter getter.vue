<template>
  <div>
    <div>Counter : {{ nilai }} </div>

    <button @click="add">Add</button>

    <div> Result yg dari computed yg isi setter getter : {{ result }} </div>

  </div>
</template>

<script>
import { reactive, ref, computed, toRefs } from 'vue'

export default {

  setup() {

    // reactive data
    const counter = reactive({
      nilai: 0
    })

    // ref data
    const addNum = ref(1)

    // method
    const add = () => {
      result.value = 5
      counter.nilai++
    }

    // computed dengan getter dan setter
    const result = computed({
      get: () => counter.nilai + addNum.value,
      set: (val) => addNum.value = val
    })

    return {
      ...toRefs(counter), add, result
    }

  }

}
</script>