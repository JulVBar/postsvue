<template>
    <div class="app">
        <post-form 
            @create="createPost"
        />
        <post-list 
            :posts="posts"
        />
    </div>
</template>

<script>
import PostForm from './components/PostForm';
import PostList from '@/components/PostList';

export default {
    components: {
        PostForm, PostList
    },
    data() {
        return {
            posts: [
                {id: 1, title: 'title 1', body: 'description 1'},
                {id: 2, title: 'title 2', body: 'description 2'},
                {id: 3, title: 'title 3', body: 'description 3'},
            ],
        }
    },
    methods: {
        createPost (post) {
            this.posts.push(post)
        }
    }
}
</script>

<style>
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }
</style>