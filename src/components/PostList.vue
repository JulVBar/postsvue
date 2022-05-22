<template>
    <div v-if="posts.length > 0">
        <h3>Список пользователей</h3>
        <post-item 
            v-for="post in posts" 
            :key="post.id"
            :post="post"
            @remove="$emit('remove', post)"
        />
    </div>
    <h2 style="color: red" v-else>Пусто</h2>
</template>

<script>
import PostItem from './PostItem';
//v-show="posts.length === 0" элемент становится display none, существует в дереве
    export default {
        props: {
            posts: {
                type: Array,
                required: true
            }
        },
        components: {
            PostItem
        },
    }
</script>

<style scoped>
</style> 
