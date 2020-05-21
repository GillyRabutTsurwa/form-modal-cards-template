<template>
  <div id="app">
    <Modal v-bind:showModalProp="showModal" v-on:forwardClick="toggleModal" />
    <button @click="toggleModal">Open Modal</button>
    <div class="main">
      <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
      <div class="card" v-for="currentPerson in people" v-bind:key="currentPerson.id">
        <div class="card__info">
          <h3>{{currentPerson.name}} - {{currentPerson.age}}</h3>
          <h5>{{currentPerson.beltColour}}</h5>
          <button class="btn">Delete</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Modal from "./components/Modal";
export default {
  name: "App",
  components: {
    Modal: Modal
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
        { name: "Toad", beltColour: "brown", age: 35, id: 7 }
      ],
      // will be used to close the modal
      showModal: false
    };
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    }
  }
};
</script>

<style>
@import "./App.css";
#app {
  position: fixed;
  top: 0;
  left: 0;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-size: 1.4rem;
  width: 100%;
  height: 100%;
}

.main {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(20rem, 1fr));
  justify-content: center;
  gap: 2rem;
  width: 100%;
  height: 100%;
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
