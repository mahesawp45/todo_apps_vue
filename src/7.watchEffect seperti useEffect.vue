<template>
  <div>
    <div>Counter : {{ nilai }} </div>
    <button @click="add">Add</button>
    <div>foo : {{ foo }} </div>
  </div>
</template>

<script>
import { reactive, toRefs, watchEffect } from 'vue'

export default {
  setup() {
    const counter = reactive({
      nilai: 0,
      foo: 'bar'
    })

    const add = () => {
      counter.nilai++
      if (counter.nilai % 2 == 0) {
        counter.foo = 'buzuzima'
      } else {
        counter.foo = 'bar'
      }

    }

    // sama kek useEffect
    watchEffect(() => {
      console.log(counter.nilai) // ini yang di watch
    },
      {
        // flush: 'post', //defaultnya pre, post dilakukan setelah component di mount

        // setiap ada perubahan dalam watch
        // onTrigger(e) {
        //   console.log(e)
        // }

        // ini pertama kali aja dan langsung
        onTrack(e) {
          console.log(e)
        }
      },
    )

    return {
      ...toRefs(counter), add
    }
  }

}
</script>