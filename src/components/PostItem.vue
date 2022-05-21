<template>
    <div class="post">
        <div>Название: {{ post.title }}</div>
        <div>Название: {{ post.body }}</div>
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
