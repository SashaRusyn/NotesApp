<template>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <form class="form" @submit.prevent>
        <div class="form__header">
            <p>Add a new Note</p>
            <!-- <i class="fa-solid fa-xmark" :click="hideDialog"></i> -->
        </div>
        <input type="text" v-bind:value="note.title" @input="note.title = $event.target.value" placeholder="Title">
        <textarea cols="30" rows="10" v-bind:value="note.body" @input="note.body = $event.target.value"
            placeholder="Body"></textarea>
        <button class="form__button" @click="createNote">Add Note</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            note: {
                title: '',
                body: '',
            }
        }
    },
    methods: {
        createNote() {
            this.note.id = Date.now();
            this.$emit('create', this.note);
            this.note = {
                title: '',
                body: '',
            }
        },
    }
}
</script>

<style scoped>
textarea {
    resize: none;
}

.form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    padding: 20px;
}

.form__header {
    font-weight: 600;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}

input,
textarea {
    outline: none;
    border: 1px solid #a0a0a0;
    border-radius: 5px;
    padding: .5rem;
}

.form__button {
    color: white;
    background-color: #00b0ff;
    padding: .5rem;
    border-radius: 5px;
    outline: none;
    border: none;
    cursor: pointer;
}
</style>