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
      <div class="card" v-for="currentPerson in people" v-bind:key="currentPerson.id">
        <!-- NOTE: Remove all the HTML code that makes a card and put it in a child component (Card).  -->
        <!-- NOTE: I passed down all the information needed for the card info to be rendered to the UI down to that child component as props: nameProp, ageProp, and idProp -->
        <!-- NOTE: Lastly I am listening a click from the delete button in the child component and emitting it up here in the parent where the child component is registered. We are not passing any data with that emit. Just the event: deleteCard, which calls on the deletePerson function that deletes the card -->
        <!-- NOTE: J'ai bien joué ici. J'en suis fier. -->
        <Card
          v-bind:nameProp="currentPerson.name"
          v-bind:ageProp="currentPerson.age"
          v-bind:beltColourProp="currentPerson.beltColour"
          v-bind:idProp="currentPerson.id"
          v-on:deleteCard="deletePerson(currentPerson.id)"
        />
      </div>
    </div>
    <p v-else style="font-size: 4em;">¯\_(ツ)_/¯</p>
    <h3>Sucess&check;</h3>
    <h4>Managed to do it the second time around. Niceee</h4>
  </div>
</template>

<script>
import Modal from "./components/Modal";
import PersonForm from "./components/AddPersonForm";
import Card from "./components/Card";
export default {
  name: "App",
  components: {
    Modal: Modal,
    PersonForm: PersonForm,
    Card: Card
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