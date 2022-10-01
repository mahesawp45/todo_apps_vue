<template>
  <div>
    <ChildComponent 
    :label="label" 
    :user="user" 

    class="classHalo"
    atribute-ku

    @submit="submit"
    >
      <div>Ini Slot</div>
    </ChildComponent>


    <button @click="changeName">Change Name</button>
  </div>
</template>


<script>
import { ref, reactive } from 'vue'

import ChildComponent from './components/component_1.vue'

export default {
  components: { ChildComponent },

  setup() {
    const label = ref('biodata')
    const user = reactive({
      name: 'Mahesa',
      age: 20
    })

    const changeName = () => {
      user.name = 'Onik is meng'
    }

    const submit = (val) => {
      console.log(val)
    }

    return { label, user, changeName, submit }
  }
}
</script>