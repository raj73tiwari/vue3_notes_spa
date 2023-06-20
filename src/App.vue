<script setup>
import Card from "./components/Card.vue";
import { ref } from "vue";

const isModal = ref(false)
const trigger = () => {
  newNote.value=''
  if (isModal.value) {
    isModal.value = false
  }
  else {
    isModal.value = true
  }
}

const newNote = ref("")

const notes=ref([])
const addNote=()=>{
  let note={
    text:newNote.value,
    date: new Date()
  }
  notes.value.push(note)
  trigger()
  newNote.value=''

}

</script>


<template>
  <main>

    <div class="overlay" v-if="isModal">
      <div class="modal">
        <textarea name="note-card" id="note-card" cols="60" rows="10" v-model="newNote" placeholder="Enter your text here !"> </textarea>
        <div class="btn-row">
          <button @click="addNote">+</button>
          <button style="background-color: red;" @click="trigger">x</button>
        </div>

      </div>
    </div>
    <div class="container">
      <h1>My Notes</h1>
      <div class="bg">
          <!-- <Card v-for="note in notes" :text="note.text" :color="note.color" />  -->
          <Card v-for="note in notes" v-bind="note"/>
      </div>
      
      <div class="btn">
        <button @click="trigger">+</button>
      </div>
    </div>
  </main>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Bagel+Fat+One');

h1 {
  font-family: 'Bagel Fat One';
  letter-spacing: 2px;
  text-align: center;
  font-size: 40px;
  font-weight: bold;
  padding: 0.5%;

}

main {
  height: 100vh;
  width: 100vw;
  background-color: #010409;
}

.container {
  height: 100%;
  width: 100%;
}

.overlay {
  position: absolute;
  height: 100%;
  width: 100%;
  background-color: rgba(25, 8, 31, 0.8);
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal {
  margin-top: 5%;
}

.bg {
  border: 2px solid #30363D;
  border-radius: 0.5rem;
  margin: 0% 10% 0% 10%;
  background-image: url(./assets/img/bg4.jpg);
  height: 75%;
  overflow-y: auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}

.btn {
  display: flex;
  align-items: center;
  justify-content: center;
}

.btn-row {
  display: flex;
  justify-content: center;
  align-items: center;
}

button:hover {
  box-shadow: 0 0 8px 0 #999;
}

.btn-row button {
  border-radius: 100%;
  height: 35px;
  width: 35px;
  margin: 2% 5% 0% 5%;
  cursor: pointer;
  border: none;
  font-size: 20px;
  color: aliceblue;
  background-color: rgb(9, 114, 35);
}

.btn button {
  border-radius: 100%;
  font-size: 50px;
  height: 50px;
  width: 50px;
  background-color: #1d0575;
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 1%;

}

textarea {
  border: 2px solid yellow;
  border-radius: 1rem;
  background-color: rgb(68, 141, 135);
  padding: 2%;
  font-size: 20px;

}

/* width */
::-webkit-scrollbar {
  width: 10px;
  
}

/* Track */
::-webkit-scrollbar-track {
  background:  #14021a;
  border-radius: 1rem; 
}
 
/* Handle */
::-webkit-scrollbar-thumb {
  background: #888; 
  border-radius: 1rem;

}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #555; 
}

::placeholder { /* Chrome, Firefox, Opera, Safari 10.1+ */
  color: rgb(56, 48, 48);
}
</style>

