<template>
  <div>
    {{ message }}
  </div>
</template>


<script>
import { ref } from 'vue';

export default {
  setup() {
    const message = ref('Halo')

    setTimeout(() => {
      message.value = 'hi'
    }, 2000);

    return {
      message
    }
  }
}
</script>