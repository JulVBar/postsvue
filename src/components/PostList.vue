<template>
    <div class="post" v-for="post in posts" :key="post.id">
        <div>Название: {{ post.title }}</div>
        <div>Название: {{ post.body }}</div>
    </div>
</template>

<script>
</script>

<style scoped>
    .post {
        padding: 15px;
        border: 2px solid darkolivegreen;
        margin-top: 15px;
    }
</style> 
