<template>
  <div @click.self="$emit('forwardClick')" v-if="showModalProp" class="modal">
    <div class="modal__content">
      <p>I am a modal</p>
    </div>
  </div>
</template>

<script>
export default {
  // Just a modified way of declaring props using the prop object vue.
  // the name of the prop is an object of itself and it has properties of the type of the value and if the value is required. Nothing too new here
  props: {
    showModalProp: {
      type: Boolean,
      required: true
    }
  }
};
</script>

<style>
.modal {
  position: fixed;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.8);
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal__content {
  width: 50rem;
  height: 30rem;
  background-color: #fff;
  color: #333;
}
</style>