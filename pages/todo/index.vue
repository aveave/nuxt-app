<template>
    <section>
        <h1>{{pageTitle}}</h1>

        <ul>
            <li v-for="todo in todos" :key="todo.id">
                <a href="" @click.prevent="showUser(todo.id)">{{todo.title}}</a>
            </li>
        </ul>
    </section>
</template>

<script>
    export default {

        async fetch({store}) {
            if (store.getters['todos/todos'].length === 0) {
                await store.dispatch('todos/uploadTodos')
            }
        },

        data: () => ({
            pageTitle: "Todos page"
        }),

        computed: {
            todos() {
                return this.$store.getters['todos/todos']; 
            }
        },

        methods: {
            showUser(id) {
                this.$router.push('/todo/' + id);
            }
        }
    }
</script>