<template>
    <button class="btn">
        <slot></slot>
    </button>
</template>

<script>
    export default {
        name: 'my-button'
    }
</script>

<style scoped>
    .btn {
        color: green;
        border: 1px solid greenyellow;
        padding: 10px 15px;
    }
</style>