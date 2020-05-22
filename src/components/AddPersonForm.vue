<template>
  <div>
    <form @submit.prevent="logSkills">
      <label for="name">Name</label>
      <input type="text" v-model="name" id="name" class="input__name" />
      <label for="age">Age</label>
      <input type="number" v-model="age" id="age" class="input__age" placeholder="Enter Your Age" />
      <div class="css-stuff">
        <label>CSS Favourites</label>
        <input type="checkbox" v-model="skillsCSS" value="bootstrap" />
        Bootstrap
        <br />
        <input type="checkbox" v-model="skillsCSS" value="bulma" />
        Bulma
        <br />
        <input type="checkbox" v-model="skillsCSS" value="full-stack" />
        Tailwind CSS
        <br />
        <input type="checkbox" v-model="skillsCSS" value="materialize" />Materialize CSS
        <br />
        <input type="checkbox" v-model="skillsCSS" value="ui-kit" />UI Kit
        <br />
        <input type="checkbox" v-model="skillsCSS" value="semantic-ui" />Semantic UI
        <br />
      </div>
      <div class="js-stuff">
        JS Favourites
        <input type="checkbox" v-model="skillsJS" value="angular" />
        Angular
        <br />
        <input type="checkbox" v-model="skillsJS" value="react" />
        React
        <br />
        <input type="checkbox" v-model="skillsJS" value="vue" />
        Vue
        <br />
        <input type="checkbox" v-model="skillsJS" value="svelte" />
        Svelte
        <br />
        <input type="checkbox" v-model="skillsJS" value="jquery" />
        jQuery
        <br />
        <input type="checkbox" v-model="skillsJS" value="ember" />
        Ember
        <br />
        <input type="checkbox" v-model="skillsJS" value="backbone" />
        Backbone
        <br />
      </div>

      <p>I specialise in</p>
      <select v-model="currentBeltColour">
        <option v-for="(current, index) in beltColours" v-bind:key="index">{{current}}</option>
      </select>
      <input type="submit" value="Add Person" />
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      age: 0,
      skillsCSS: [],
      skillsJS: [],
      currentBeltColour: "",
      beltColours: [
        "Front-End",
        "Back-End",
        "Dev Ops",
        "Data Structures",
        "Web-Design"
      ]
    };
  },
  methods: {
    logSkills() {
      console.log(this.name, Number(this.age), this.currentBeltColour);
      console.log(this.skillsCSS);
      console.log(this.skillsJS);
    }
  }
};
</script>

<style>
</style>