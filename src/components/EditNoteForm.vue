<template>
    <div class="dialog" @click="hideDialog" v-if="show">
        <div class="dialog__content" @click.stop>
            <form class="form" @submit.prevent>
                <div class="form__header">
                    <p>Edit this Note</p>
                    <i class="fa-solid fa-xmark" @click="hideDialog"></i>
                </div>
                <input type="text" v-bind:value="updateNote.title" value="updateNote.title"
                    @input="updateNote.title = $event.target.value" placeholder="Title">
                <textarea cols="30" rows="10" v-bind:value="updateNote.body" value="updateNote.body"
                    @input="updateNote.body = $event.target.value" placeholder="Body"></textarea>
                <my-button @click="editNote">Edit this Note</my-button>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        editId: {
            type: Number,
            require: true,
        },
        editTitle: {
            type: String,
            require: true,
        },
        editBody: {
            type: String,
            require: true,
        },
        editDate: {
            type: Date,
            require: true,
        },
        show: {
            type: Boolean,
            default: false,
        }
    },
    data() {
        return {
            updateNote: {
                id: 0,
                title: '',
                body: '',
                date: new Date(),
            }
        }
    },
    methods: {
        editNote() {
            if (this.editTitle !== this.updateNote.title || this.editBody !== this.updateNote.body) {
                this.updateNote.date = new Date();
            }
            if (this.updateNote.title.trim().length !== 0 && this.updateNote.body.trim().length !== 0) {
                this.$emit('updateNote', this.updateNote);
            }
        },
        hideDialog() {
            this.$emit('update:show', false);
        }
    },
    watch: {
        show(newValue) {
            if (newValue) {
                this.updateNote.id = this.editId;
                this.updateNote.title = this.editTitle;
                this.updateNote.body = this.editBody;
                this.updateNote.date = this.editDate;
            }
        }
    }
}
</script>

<style>
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

/* .form__button {
    color: white;
    background-color: #00b0ff;
    padding: .5rem;
    border-radius: 5px;
    outline: none;
    border: none;
    cursor: pointer;
} */
</style>