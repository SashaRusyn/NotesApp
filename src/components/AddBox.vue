<template>
    <div class="add-box">
        <div class="icon">+</div>
        <p>Add new notes</p>
    </div>
</template>

<script>
export default {
}
</script>

<style scoped>
.add-box {
    border-radius: 10px;
    color: #00b0ff;
    background-color: white;
    display: flex;
    flex-direction: column;
    height: 250px;
    justify-content: center;
    align-items: center;
    gap: 10px;
    cursor: pointer;
    padding: 0 20px;
}

.icon {
    border: 2px dashed #00b0ff;
    border-radius: 50%;
    width: 78px;
    height: 78px;
    display: inherit;
    justify-content: center;
    align-items: center;
    font-size: 45px;
    font-weight: 500;
}
</style>