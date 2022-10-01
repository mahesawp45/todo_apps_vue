<template>
    <div>
        <div class="row mt-4">
            <div class="col-md-10">
                <ul class="list-group">
                    <li class="list-group-item" v-for="(todo, index) in todos.list">
                        <div class="row">
                            <div class="col">
                                <span v-if="todo.isDone == true">
                              <del>{{ todo.activity }} </del>
                            </span>
                                <span v-else>{{ todo.activity }} </span>
                            </div>
        
                            <div class="col-auto">
                                <button :class="todo.isDone ? 'btn-warning btn btn-sm' : 'btn-success btn btn-sm'" @click="doneTodo(index)">✅</button>
                            </div>
                            <div class="col-auto">
                                <button class="btn btn-danger btn-sm" @click="deleteTodo(index)">❎</button>
                            </div>
                        </div>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>

export default {

    props: {
        todos: {
            type: Object,
            default: () => {}
        }
    },

    setup(props, { emit }) {
        
        const doneTodo = (index) => {
            emit('done-todo', index)
        }

        const deleteTodo = (index) => {
            emit('delete-todo', index)
        }

        return {
            doneTodo, deleteTodo
        }
    },

    // emits: ['done-todo', 'delete-todo'],

    // props: {
    //     todos: {
    //         type: Array,
    //         default: []
    //     }
    // },

    // methods: {
    //     doneTodo(index) {
    //         return this.$emit('done-todo', index)
    //     },

    //     deleteTodo(index) {
    //         return this.$emit('delete-todo', index)
    //     }
    // }

    

    
}
</script>