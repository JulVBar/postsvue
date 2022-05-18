<template>
    <form @submit.prevent>
        <h4>Название поста</h4>
        <input 
            v-bind:value="title" 
            @input="title = $event.target.value" 
            type="text"
            placeholder="Название">
        <input 
            v-bind:value="body" 
            @input="body = $event.target.value" 
            type="text"
            placeholder="Описание">
        <button @click="createPost">Создать</button>
    </form>
</template>

<script>
</script>

<style scoped>
</style> 