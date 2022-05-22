<template>
    <div class="app">
        <h1>Страница с постами</h1>
        <my-input      
            v-model="searchQuery"
            placeholder="Search"/>
        <div class="app__btns">
            <my-button @click="showDialog">Создать пост</my-button>
            <my-select 
                v-model="selectedSort"
                :options="sortOptions"
            >

            </my-select>
        </div>
        
        <my-dialog v-model:show="dialogVisible">
            <post-form 
            @create="createPost"
        />
        </my-dialog>
        
        <post-list 
            :posts="sortedAndSearchedPosts"
            @remove="removePost"
            v-if="!isLoading"
        />
        <div v-else>Loading</div>
        <div class="page__list">
            <div
                class="page"
                v-for="pageN in totalPages"
                :key="pageN"
                :class="{
                    'current-page': page === pageN
                }"
                @click="changePage(pageN)">
                {{ pageN }}
            </div>
        </div>
    </div>
</template>

<script>
import PostForm from './components/PostForm';
import PostList from '@/components/PostList';
import axios from 'axios';

export default {
    components: {
        PostForm, PostList
    },
    data() {
        return {
            posts: [],
            dialogVisible: false,
            isLoading: false,
            selectedSort: '',
            searchQuery: '',
            page: 1,
            limit: 10,
            totalPages: 0,
            sortOptions: [
                {value: 'title', name: 'По названию'},
                {value: 'body', name: 'По описанию'}
            ]
        }
    },
    methods: {
        createPost (post) {
            this.posts.push(post);
            this.dialogVisible = false;
        },
        removePost(post) {
            this.posts = this.posts.filter(p => p.id !== post.id);
        },
        showDialog() {
            this.dialogVisible = true;
        },
        changePage(pageN) {
            this.page = pageN;
            // this.fetchPosts();
        },
        async fetchPosts() {
            try {
                this.isLoading = true;
                const response = await axios.get('https://jsonplaceholder.typicode.com/posts', {
                    params: {
                        _page: this.page,
                        _limit: this.limit,

                    }
                });
                this.totalPages = Math.ceil(response.headers['x-total-count'] / this.limit);
                this.posts = response.data;
                this.isLoading = false;
                
            } catch(e) {
                alert('ERROR')
            }
        }
    },
    mounted() {
        this.fetchPosts();
    },
    computed: {
        sortedPosts() {
            return [...this.posts].sort((a,b) =>a[this.selectedSort]?.localeCompare(b[this.selectedSort])
            )
        },
        sortedAndSearchedPosts() {
            return this.sortedPosts.filter(post => post.title.toLowerCase().includes(this.searchQuery.toLowerCase()))
        }
    },
    watch: {
        page() {
            this.fetchPosts();
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
    .app__btns {
        display: flex;
    }
    .page__list {
        display: flex;
    }
    .page {
        padding: 8px;
        border: 1px solid fuchsia;
        margin-right: 8px;
    }
    .current-page {
        background: darkcyan;
    }
</style>