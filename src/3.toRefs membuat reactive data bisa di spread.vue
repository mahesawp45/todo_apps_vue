<template>
  <div>
    <div>nama: {{ name }}</div>
    <div>umur: {{ age }}</div>
  </div>
</template>

<script>
import { reactive, toRefs } from "vue";
export default {

  setup() {
    const user = reactive({
      name: 'Mahesa',
      age: 20
    })

    setTimeout(() => {
      user.name = 'Onik'
      user.age = 6
    }, 2000);

    return {
      ...toRefs(user)
    }
  }
}
</script>