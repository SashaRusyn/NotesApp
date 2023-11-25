<template>
    <button class="btn">
        <slot></slot>
    </button>
</template>

<script>
export default {
    name: 'my-button',
}
</script>

<style scoped>
.btn {
    color: white;
    background-color: #00b0ff;
    padding: .5rem;
    border-radius: 5px;
    outline: none;
    border: none;
    cursor: pointer;
}
</style>