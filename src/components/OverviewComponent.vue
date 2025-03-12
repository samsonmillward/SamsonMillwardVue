<script setup lang="ts">
import { ref, watch } from 'vue'

const firstName = ref('Samson')
const surname = ref('Millward')
const showInput = ref(false)
const newName = ref('')
const messages = ref({
  0: 'Well, I guess enter a new name here:',
  1: 'Alright, I\'ll give you another chance',
  2: 'Last chance...'
})
function clicked(letter: string) {
  const letterToRemove = letter.slice(-1)
  if (letter.includes('first')) {
    firstName.value = firstName.value.replace(letterToRemove, '')
    console.log(firstName.value, 'firstname')
  }
  if (letter.includes('last')) {
    surname.value = surname.value.replace(letterToRemove, '')
    console.log(surname.value, 'surname')
  }
}
watch(firstName, async (newName) => {
  if (newName.length === 0) {
    triggerEmptyName();
  }
});
watch(surname, async (newName) => {
  if (newName.length === 0) {
    triggerEmptyName();
  }
});
function triggerEmptyName() {
  if (firstName.value.length == 0 && surname.value.length == 0) {
    showInput.value = true;
  }
}
function submitNewName() {
  firstName.value = newName.value;
  showInput.value = false;
}
</script>

<template>

  <div class="container-fluid">
    <div class="name-destroy">
      <div v-show="showInput">

        <label for="newNameInput">
          <p>{{ messages['0'] }}</p>
        </label>
        <input
          name="newNameInput"
          class="newNameInput"
          v-model="newName"
        />
        <button @click="submitNewName">Confirm New Name</button>
      </div>
      <h1
        class="name-title"
        @click="clicked(`first-${letter}`)"
        v-for="letter in firstName"
        :key="`first-${letter}`"
      >{{ letter }}</h1>
      <span>&nbsp;&nbsp;</span> <!-- Add this line to insert a space -->
      <h1
        class="name-title"
        @click="clicked(`last-${letter}`)"
        v-for="letter in surname"
        :key="`last-${letter}`"
      >{{ letter }}</h1>
    </div>

    <p>Full Stack Software Engineer (Vue/Python)</p>
    <div class="links">

      <a
        class="email-link"
        href="mailto:samsonmillward@gmail.com"
      ><span class="material-symbols-outlined icons">mail</span>
        samsonmillward@gmail.com</a>
      <a href="https://www.linkedin.com/in/samson-millward/"><svg
          xmlns="http://www.w3.org/2000/svg"
          width="30"
          height="30"
          fill="currentColor"
          class="bi bi-linkedin"
          viewBox="0 0 16 16"
        >
          <path d="M0 1.146C0 .513.526 0 1.175 0h13.65C15.474 0 16 .513 16 1.146v13.708c0 .633-.526 1.146-1.175 1.146H1.175C.526 16 0 15.487 0 14.854zm4.943 12.248V6.169H2.542v7.225zm-1.2-8.212c.837 0 1.358-.554 1.358-1.248-.015-.709-.52-1.248-1.342-1.248S2.4 3.226 2.4 3.934c0 .694.521 1.248 1.327 1.248zm4.908 8.212V9.359c0-.216.016-.432.08-.586.173-.431.568-.878 1.232-.878.869 0 1.216.662 1.216 1.634v3.865h2.401V9.25c0-2.22-1.184-3.252-2.764-3.252-1.274 0-1.845.7-2.165 1.193v.025h-.016l.016-.025V6.169h-2.4c.03.678 0 7.225 0 7.225z" />
        </svg>
      </a>
    </div>

  </div>
</template>

<style lang="sass" scoped>

</style>
