<template>
  <div class="app">
    <my-dialog v-model:show="isDialogVisible">
      <add-note-form @create="createNote"></add-note-form>
    </my-dialog>
    <add-box @click="isDialogVisible = true"></add-box>
    <note-item v-for="note in notes" :note="note"></note-item>
  </div>
</template>

<script>
import AddNoteForm from '@/components/AddNoteForm.vue';
import AddBox from '@/components/AddBox.vue';
import NoteItem from '@/components/NoteItem.vue';
export default {
  components: {
    AddNoteForm,
    AddBox,
    NoteItem,
  },
  data() {
    return {
      title: '',
      notes: [],
      isDialogVisible: false,
    }
  },
  methods: {
    createNote(note) {
      this.notes.push(note);
    }
  }
}
</script>

<style>
/* @import url('https://fonts.googleapis.com/css2?family=Archivo&family=Inter:wght@300;400&family=Montserrat:wght@400;700&family=Poppins:wght@300&display=swap'); */

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Inter', Arial, Helvetica, sans-serif;
}

.app {
  padding: 20px;
  box-sizing: border-box;
  display: grid;
  gap: 15px;
  grid-template-columns: repeat(auto-fill, 365px);
  grid-template-rows: repeat(auto-fill, 265px);
  background-color: #00b0ff;
  height: 100vh;
}

/* li {
  padding: 15px 20px 20px;
  list-style: none;
} */
</style>
