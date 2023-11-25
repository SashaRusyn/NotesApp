<template>
  <div class="app">
    <div class="wrapper">
      <transition name="dialog">
        <add-note-form v-model:show="addDialogVisible" @create="createNote"
          @click="this.ddDialogVisible = true"></add-note-form>
      </transition>
      <transition name="dialog">
        <edit-note-form v-model:show="editDialogVisible" v-model:editId="updatedId" v-model:editTitle="updatedTitle"
          v-model:editBody="updatedBody" v-model:editDate="updatedDate" @updateNote="updateNote"></edit-note-form>
      </transition>
      <li>
        <add-box @click="this.addDialogVisible = true"></add-box>
      </li>
      <transition-group name="note-list">
        <li v-for="note in notes">
          <note-item @remove="removeNote" @edit="editNote" :note="note" :key="note.id"></note-item>
        </li>
      </transition-group>
    </div>
  </div>
</template>

<script>
import AddNoteForm from '@/components/AddNoteForm.vue';
import EditNoteForm from '@/components/EditNoteForm.vue';
import AddBox from '@/components/AddBox.vue';
import NoteItem from '@/components/NoteItem.vue';
export default {
  components: {
    AddNoteForm,
    EditNoteForm,
    AddBox,
    NoteItem,
  },
  data() {
    return {
      updatedId: 0,
      updatedTitle: '',
      updatedBody: '',
      updatedDate: new Date(),
      notes: [{ id: 1, title: 'The first note', body: 'Its first note of my app', date: 1 }, { id: 2, title: 'The second note', body: 'Ooooh, its a second note of the day', date: 1 }, { id: 3, title: 'the third note', body: 'Yeah, great, its third', date: 1 }],
      addDialogVisible: false,
      editDialogVisible: false,
    }
  },
  methods: {
    createNote(note) {
      this.notes.push(note);
    },
    removeNote(note) {
      this.notes = this.notes.filter(p => p.id !== note.id);
    },
    editNote(note) {
      this.editDialogVisible = true;
      this.updatedId = note.id;
      this.updatedTitle = note.title;
      this.updatedBody = note.body;
      this.updatedDate = note.date;
    },
    updateNote(updatedNote) {
      this.editDialogVisible = false;
      this.notes.forEach(note => {
        if (note.id === updatedNote.id) {
          note.title = updatedNote.title;
          note.body = updatedNote.body;
          note.date = updatedNote.date;
        }
      });
    },
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Archivo&family=Poppins:wght@300;400;500;600&family=Montserrat:wght@400;700&family=Poppins:wght@300&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', Arial, Helvetica, sans-serif;
}

body {
  background: #88ABFF;
}

.wrapper {
  margin: 20px;
  display: grid;
  gap: 15px;
  grid-template-columns: repeat(auto-fill, 265px);
}

.wrapper li {
  height: 250px;
  list-style: none;
  background: #fff;
  border-radius: 5px;
  padding: 15px 20px 20px;
  display: flex;
}

.note-list-item {
  display: inline-block;
  margin-right: 10px;
}

.note-list-enter-active,
.note-list-leave-active {
  transition: all 0.5s ease;
}

.note-list-enter-from,
.note-list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}

.dialog-enter-active,
.dialog-leave-active {
  transition: opacity 0.5s ease;
}

.dialog-enter-from,
.dialog-leave-to {
  opacity: 0;
}
</style>
