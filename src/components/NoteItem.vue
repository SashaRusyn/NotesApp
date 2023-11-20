<template>
    <div class="note">
        <div class="note__head">
            <h2 class="title">{{ note.title }}</h2>
            <p class="body">{{ note.body }}</p>
        </div>
        <div class="note__foot">
            <hr>
            <p class="date">note.id</p>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        note: {
            type: Object,
            require: true,
        }
    }
}
</script>

<style scoped>
.note {
    background-color: white;
    padding: 20px;
    height: 250px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    border-radius: 10px;
}

.note__head,
.note__foot {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.title {
    font-size: 24px;
}

.body {
    font-size: 16px;
}
</style>