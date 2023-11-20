<template>
    <div v-if="show" class="dialog" @click="hideDialog">
        <div @click.stop class="dialog__content">
            <slot @update="hideDialog"></slot>
        </div>
    </div>
</template>

<script>
export default {
    name: 'my-dialog',
    props: {
        show: {
            type: Boolean,
            default: false,
        }
    },
    methods: {
        hideDialog() {
            this.$emit('update:show', false);
        }
    },
}
</script>

<style scoped>
.dialog {
    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    display: flex;
    background-color: rgba(0, 0, 0, 0.5);
}

.dialog__content {
    margin: auto;
    background: #fff;
    min-height: 50px;
    border-radius: 12px;
    min-width: 300px;
}
</style>