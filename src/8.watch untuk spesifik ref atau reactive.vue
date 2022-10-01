<template>
  <div>
    <div>Counter : {{ nilai }} </div>
    <button  @click="add" >Add</button>
  </div>
</template>


<script>
import {reactive, ref, toRefs, watch} from "vue"

export default {

  setup() {

    const counter = reactive({
      nilai: 0
    })

    const num1 = ref(1)
    const num2 = ref(2)

    const add = () => {
      counter.nilai++
      // num1.value++
      // num2.value++
    }

    // watch(counter, (current, before) => {
    //   console.log(`Ini counter => ${counter.nilai} `)
    //   console.log(`Ini current => ${current.nilai} `)
    //   console.log(`Ini before => ${before.nilai} `)
    // })

    // ini watcher buat ref
    // watch([num1, num2], (current, before) => {
    //     console.log(`ini num1 => ${num1.value}`)
    //     console.log(`ini num1 current => ${current[0]}`)
    //     console.log(`ini num1 before => ${before[0]}`)
    // })


    // watcher buat reactive
    watch(() => counter.nilai, (current, before) => {
      console.log(`ini counter => ${counter.nilai}`)
      console.log(`ini counter current => ${current}`)
      console.log(`ini counter before => ${before}`)
    })
      

    return {
      ...toRefs(counter), add
    }
    
  }

  
}
</script>