<template>
  <div id="app">
    <Modal
      v-bind:showModalProp="showModal"
      v-bind:peopleArrayProp="people"
      v-on:forwardClick="toggleModal"
    >
      <PersonForm v-on:addPerson="addNewPerson($event)" />
    </Modal>
    <button @click="toggleModal">Open Modal</button>
    <div class="main" v-if="people.length > 0">
      <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
      <div class="card" v-for="currentPerson in people" v-bind:key="currentPerson.id">
        <div class="card__info">
          <h3>{{currentPerson.name}} - {{currentPerson.age}}</h3>
          <h5>{{currentPerson.beltColour}}</h5>
          <!-- NEW: Kind of, if you want to access the event object (the e or evt or event in vanillajs), pass in the $event directive as an argument in your function call like below. Then access it as your first argument in your function -->
          <!-- <button @click="deletePerson($event, currentPerson.id)" class="btn">Delete</button> -->
          <button @click="deletePerson(currentPerson.id)" class="btn">Delete</button>
        </div>
      </div>
    </div>
    <p v-else>Nobody</p>
  </div>
</template>

<script>
import Modal from "./components/Modal";
import PersonForm from "./components/AddPersonForm";
export default {
  name: "App",
  components: {
    Modal: Modal,
    PersonForm: PersonForm
  },
  data() {
    return {
      people: [
        { name: "Yoshi", beltColour: "black", age: 25, id: 1 },
        { name: "Mario", beltColour: "orange", age: 45, id: 2 },
        { name: "Luigi", beltColour: "brown", age: 35, id: 3 },
        { name: "Peach", beltColour: "brown", age: 35, id: 4 },
        { name: "Daisy", beltColour: "brown", age: 35, id: 5 },
        { name: "Browser", beltColour: "brown", age: 35, id: 6 },
        { name: "Toad", beltColour: "brown", age: 35, id: 8 },
        { name: "Toad", beltColour: "brown", age: 35, id: 9 },
        { name: "Toad", beltColour: "brown", age: 35, id: 10 },
        { name: "Toad", beltColour: "brown", age: 35, id: 11 }
      ],
      // will be used to close the modal
      showModal: false
    };
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    addNewPerson(newPersonData) {
      console.log(newPersonData);
      // render the new Person to the ui by appending the info to the peoples array.
      // il y a beaucoup de moyens pour le faire.
      this.people = [...this.people, newPersonData];
      this.showModal = false;
    },
    deletePerson(id) {
      // console.log(e);
      console.log(id);
      this.people = this.people.filter(
        currentPerson => currentPerson.id !== id
      );
    }
  }
};
</script>

<style>
@import "./App.css";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-size: 1.4rem;
  width: 100%;
  /* height: 100%; */
}
.main {
  display: grid;
  /* the max is 30rem instead of 1fr. Looks way nicer. Especially for the hover effect I'll put in the card */
  grid-template-columns: repeat(auto-fit, minmax(20rem, 30rem));
  justify-content: center;
  gap: 2rem;
  width: 100%;
  /* height: 100%; */
}
.card__info {
  height: 30rem;
  box-shadow: 0 1rem 1rem 0.5rem rgba(0, 0, 0, 0.2);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>