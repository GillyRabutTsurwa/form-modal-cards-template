<template>
  <div>
    <!-- NOTE: Moved all this code from the app component to its own child component. All the info needed to be displayed were passed down as props. Lastly I can display them as they are, and not store them in new variables, because I'm not changing them. -->
    <div class="card__info">
      <h3>{{nameProp}} - {{ageProp}}</h3>
      <h5>{{beltColourProp}}</h5>
      <button @click="emitDelete" class="btn">Delete</button>
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
    }
  },
  methods: {
    // NOTE: Function that will be passed up to the parent that will eventually delete a card upon the click of the button
    emitDelete() {
      this.$emit("deleteCard");
    }
  }
};
</script>

<style>
</style>