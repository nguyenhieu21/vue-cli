<template>
    <li>
      {{ title }}
      <button v-on:click="$emit('remove')">X</button>
    </li>
</template>

<script>
export default {
    props: ['title'],
    data(){
        return {
            todos: [
                {
                    id: 1,
                    title: 'luộc khoai'
                },
                {
                    id: 2,
                    title: 'thổi cơm'
                },
                {
                    id: 3,
                    title: 'lau nhà'
                },
                {
                    id: 4,
                    title: 'quét nhà'
                },
            ],
            newTodoId: 5
        }
    },

    methods: {
        addNewTodo(){
            this.todos.push({
                id: this.nextTodoId++,
                title: this.newTodoText
            })
            this.newTodoId = ''
        }
    }
}
</script>

<style>

</style>