<template>
    <div>
        <div>
            {{ label }} - {{ user.name }}
        </div>

        <div>{{ description }} </div>

        <hr>

        <slot />

        <button @click="submit">Submit</button>
    </div>
</template>


<script>
import {toRefs, computed, onMounted} from 'vue'

export default {
    props: {
        label: {
            type: String,
            default: ''
        },
        user: {
            type: Object,
            default: () => {}
        }
    },
    setup(props, {attrs, slots, emit }) {
        const { label, user } = toRefs(props)

        const description = computed(() => {
            return `${label.value} : ${user.value.name}` 
        })

        onMounted(() => {
          console.log(attrs)  
          console.log(slots)  
        })

        const submit = () => {
            emit('submit', 'Ini Emit dari Child Component')
        }

        return {
            description, submit
        }

    }
}
</script>