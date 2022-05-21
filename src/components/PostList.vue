<template>
    <div>
        <h3>Список пользователей</h3>
        <post-item 
            v-for="post in posts" 
            :key="post.id"
            :post="post"
        />
    </div>
</template>

<script>
import PostItem from './PostItem';
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
