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
        <Card
          v-bind:nameProp="currentPerson.name"
          v-bind:ageProp="currentPerson.age"
          v-bind:beltColourProp="currentPerson.beltColour"
          v-bind:idProp="currentPerson.id"
          v-bind:skillsCSSProp="currentPerson.skillsCSS"
          v-bind:skillsJSProp="currentPerson.skillsJS"
          v-on:deleteCard="deletePerson(currentPerson.id)"
        />
      </div>
    </div>
    <p v-else style="font-size: 4em;">¯\_(ツ)_/¯</p>
    <p>Come back, polish and take notes. Oh and nice use of refs on this one.</p>
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
      showModal: false,
      //NEW:
      skillsCSS: []
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
      // //NEW:
      // this.skillsCSS = newPersonData.skillsCSS;
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

.card {
  position: relative;
  height: 30rem;
  perspective: 170rem;
}

.card__front,
.card__back {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
  box-shadow: 0 1rem 1rem 0.5rem rgba(0, 0, 0, 0.2);
  transition: all 0.5s ease;
}

.card__back {
  transform: rotateY(180deg);
}

.card:focus .card__front {
  transform: rotateY(-180deg);
}

.card:focus .card__back {
  transform: rotateY(0);
}
</style>