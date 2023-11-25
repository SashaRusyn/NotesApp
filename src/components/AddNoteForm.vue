<template>
    <div class="dialog" @click="hideDialog" v-if="show">
        <div class="dialog__content" @click.stop>
            <form class="form" @submit.prevent>
                <div class="form__header">
                    <p>Add a new Note</p>
                    <i class="fa-solid fa-xmark" @click="hideDialog"></i>
                </div>
                <input type="text" v-bind:value="note.title" @input="note.title = $event.target.value" placeholder="Title">
                <textarea cols="30" rows="10" v-bind:value="note.body" @input="note.body = $event.target.value"
                    placeholder="Body"></textarea>
                <my-button @click="createNote">Add Note</my-button>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        show: {
            type: Boolean,
            default: false,
        }
    },
    data() {
        return {
            note: {
                title: '',
                body: '',
            },
        }
    },
    methods: {
        createNote() {
            this.note.date = Date.now();
            this.note.id = this.note.date;
            if (this.note.title.trim().length != 0 && this.note.body.trim().length != 0) {
                this.$emit('create', this.note);
                this.note = {
                    title: '',
                    body: '',
                }
            }
        },
        hideDialog() {
            this.note = {
                title: '',
                body: '',
            }
            this.$emit('update:show', false);
        }
    }
}
</script>

<style scoped>
.dialog {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background: rgba(0, 0, 0, 0.4);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 10;
}

.dialog__content {
    border-radius: 8px;
    background: #fff;
}

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
</style>