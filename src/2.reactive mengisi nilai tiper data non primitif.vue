<template>
  <div>
    <div>Name : {{ user.name }} </div>
    <div>age : {{ user.age }} </div>
  </div>
</template>

<script>
import { reactive } from 'vue';

export default {
  setup() {
    const user = reactive({
      name: 'Mahe',
      age: '20'
    }) 

    setTimeout(() => {
      user.name = 'Wayahe'
    }, 2000);

    return {
      user
    }
  }
}
</script>