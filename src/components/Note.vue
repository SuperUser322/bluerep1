<template>
  <div>
    <div>
      <input v-model.trim='newNote.text' type='text'/>
      <button @click="createNote">Add</button>
    </div>
    <div v-for='note in notes'>
      <div v-if='note.editMode'>
        <input v-model='note.text' type='text' />
        <button @click='saveNote(note)'>Save</button>
      </div>
      <div v-else>
        <input v-model='note.completed' type='checkbox' />
        <span :class="{ completed: note.completed }">
          {{note.text}}
        </span>
        <button @click="changeNote(note)">Edit</button>
        <button @click="removeNote(note)">delete</button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data: () => ({
      newNote: {
        text: '',
        completed: false,
        editMode: false,
      },
      notes: []
    }),
    methods: {
      createNote () {
        if (this.newNote.text !== '') {
          this.notes.push(this.newNote)
          this.newNote = { text: '', completed: false, editMode: false }
        }
      },
      removeNote (note) {
        this.notes.splice(this.notes.findIndex((el) => el === note), 1)
      },
      changeNote (note) {
        note.editMode = true
      },
      saveNote (note) {
        note.editMode = false
      }
    }
  }
</script>

<style>
.completed {
  text-decoration: line-through;
}
</style>
