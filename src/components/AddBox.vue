<template>
    <div class="add-box">
        <div class="icon"><i class="uil uil-plus"></i></div>
        <p>Add new notes</p>
    </div>
</template>

<script>
export default {
}
</script>

<style scoped>
.add-box {
    width: 100%;
}

.add-box,
.icon {
    display: flex;
    align-items: center;
    flex-direction: column;
    justify-content: center;
    cursor: pointer;
}

.add-box .icon {
    height: 78px;
    width: 78px;
    color: #88ABFF;
    font-size: 40px;
    border-radius: 50%;
    border: 2px dashed #88ABFF;
}

.add-box p {
    color: #88ABFF;
    font-weight: 500;
    margin-top: 20px;
}
</style>