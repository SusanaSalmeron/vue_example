<script setup>
import NoteToShow from './components/NoteToShow.vue';
import NoteInput from './components/NoteInput.vue';
import { ref } from 'vue';

let initialNotes = ref([
  { id: 1, note: "1" },
  { id: 2, note: "2" }
])

const note = ref('')
let id = 3
const deleteItem = (noteId) => {
  for (let i = 0; i < initialNotes.value.length; i++) {
    if (initialNotes.value[i].id === noteId) {
      const notesUpdated = initialNotes.value.filter(note => initialNotes.value[i] !== note)
      initialNotes.value = notesUpdated
    }
  }
}

const addItem = () => {
  const newNote = { id: id++, note: note.value }
  initialNotes.value.push(newNote)
  note.value = ""
}
</script >

<template>
  <h1 class="title">Notas</h1>
  <NoteInput v-model="note" @addNote="addItem" @submit="addItem" />
  <div class="notes">
    <NoteToShow v-for="initialNote in initialNotes" :key="initialNote.id" :notes="initialNote.note"
      @deleteItem="deleteItem(initialNote.id)" class="note" />
  </div>
</template>

<style>
.title {
  text-transform: uppercase;
  text-align: center;
  margin-top: 2em;
}

.notes {
  display: flex;
  width: 100%;
  gap: 1em;
  flex-wrap: wrap;
}
</style>

















<!-- <script setup>
import { ref } from 'vue'
import ButtonCounter from './components/ButtonCounter.vue';
import RollTheDice from './components/RollTheDice.vue';
import BlogPost from './components/BlogPost.vue';
import AlertBox from './components/AlertBox.vue';
import HomePage from './components/HomePage.vue';
import PostsPage from './components/PostsPage.vue';
import Archive from './components/ArchivePage.vue';


const posts = ref([
  { id: 1, title: 'My journey with Vue' },
  { id: 2, title: 'Blogging with Vue' },
  { id: 3, title: 'Why Vue is so fun' }
])

const postFontSize = ref(1)

const currentTab = ref('HomePage')

const tabs = {
  HomePage,
  PostsPage,
  Archive
}

</script>

<template>
  <RollTheDice />
  <ButtonCounter />
  <div :style="{ fontSize: postFontSize + 'em' }">
    <BlogPost @enlarge-text="postFontSize += 0.1" v-for="post in posts" :key="post.id" :title="post.title"></BlogPost>
  </div>
  <AlertBox>
    Something bad happened
  </AlertBox>
  <div class="demo">
    <button v-for="(_, tab) in tabs" :key="tab" :class="['tab-button', { active: currentTab === tab }]"
      @click="currentTab = tab">
      {{ tab }}
    </button>
    <component :is="tabs[currentTab]" class="tab"></component>
  </div>
</template>


<style>
.demo {
  font-family: sans-serif;
  border: 1px solid #eee;
  border-radius: 2px;
  padding: 20px 30px;
  margin-top: 1em;
  margin-bottom: 40px;
  user-select: none;
  overflow-x: auto;
}

.tab-button {
  padding: 6px 10px;
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
  border: 1px solid #ccc;
  cursor: pointer;
  background: #f0f0f0;
  margin-bottom: -1px;
  margin-right: -1px;
}

.tab-button:hover {
  background: #e0e0e0;
}

.tab-button.active {
  background: #e0e0e0;
}

.tab {
  border: 1px solid #ccc;
  padding: 10px;
}
</style> -->