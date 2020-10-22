<template>
    <div>
        <h1>Todo info </h1>

        <p>{{todo.title}}</p>
        <p>Todo status: {{todo.completed ? 'completed' : 'not completed'}}</p>

    </div>
</template>

<script>
    export default {

        validate({params}) {
            return /^\d+$/.test(params.id);
        },

        async asyncData({$axios, params}) {
            const todo = await $axios.$get(`https://jsonplaceholder.typicode.com/todos/${params.id}`);
            return {todo};
        }
    }
</script>