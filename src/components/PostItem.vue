<template>
    <div class="post">
        <div>
            <div>ID: {{ post.id }}</div>
            <div>Название: {{ post.title }}</div>
            <div>Название: {{ post.body }}</div>
        </div>
        <div>
            <my-button @click="$emit('remove', post)">Удалить</my-button>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            post: {
                type: Object,
                required: true
            }
        }
    }
</script>

<style scoped>
    .post {
        padding: 15px;
        border: 2px solid darkolivegreen;
        margin-top: 15px;
    }
</style> 
