<template>
  <div class="app">
    <div class="wrapper">
      <add-note-form v-model:show="isDialogVisible" @create="createNote"></add-note-form>
      <li>
        <add-box @click="showDialog"></add-box>
      </li>
      <li v-for="note in notes" :key="note.id">
        <note-item @remove="removeNote" :note="note"></note-item>
      </li>
    </div>
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
      notes: [{ id: 1, title: 'svssvd', body: 'Lorem hj  f hgk ckkhcgkh ', date: 1 }, { id: 2, title: 'svssvd', body: 'aa', date: 1 }, { id: 3, title: 'svssvd', body: 'aa', date: 1 }],
      isDialogVisible: false,
    }
  },
  methods: {
    createNote(note) {
      this.notes.push(note);
    },
    removeNote(note) {
      this.notes = this.notes.filter(p => p.id !== note.id);
    },
    showDialog() {
      this.isDialogVisible = true;
    }
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
  margin: 50px;
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
</style>
