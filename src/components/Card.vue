<template>
  <div>
    <div class="card__front" ref="frontCard">
      <div class="card__front-container">
        <h3>{{nameProp}} - {{ageProp}}</h3>
        <h5>{{beltColourProp}}</h5>
        <button @click="emitDelete" class="btn">Delete</button>
        <button @click="flipToBack" ref="flipButton">Flip</button>
      </div>
    </div>
    <div class="card__back" ref="backCard">
      <ul class="skills__list">
        <li
          class="skills__list--item"
          v-for="(currentSkill, index) in skillsCSSProp"
          v-bind:key="index"
        >{{currentSkill}}</li>
      </ul>
      <ul class="skills__list">
        <li
          class="skills__list--item"
          v-for="(currentSkill, index) in skillsJSProp"
          v-bind:key="index"
        >{{currentSkill}}</li>
      </ul>
      <button @click="flipToFront" ref="flipButton">Flip</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    nameProp: {
      type: String
    },
    ageProp: {
      type: Number
    },
    beltColourProp: {
      type: String
    },
    idProp: {
      type: Number
    },
    skillsCSSProp: {
      type: Array
    },
    skillsJSProp: {
      type: Array
    }
  },
  methods: {
    emitDelete() {
      this.$emit("deleteCard");
    },
    flipToBack() {
      console.log(this.$refs);
      this.$refs.frontCard.style.transform = "rotateY(-180deg)";
      this.$refs.backCard.style.transform = "rotateY(0)";
    },
    flipToFront() {
      console.log(this.$refs);
      this.$refs.frontCard.style.transform = "rotateY(0)";
      this.$refs.backCard.style.transform = "rotateY(180deg)";
    }
  }
};
</script>

<style>
</style>