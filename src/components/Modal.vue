<template>
  <div @click.self="$emit('forwardClick')" v-if="showModalProp" class="modal">
    <div class="modal__content">
      <!-- NEWIMPORTANTNOTE: slots can also work for components, not just HTML elements. this is VERY USEFUL. Tried to initialise a component inside a declaration of another component in the App component and it did not work, like you can in Svelte. So we use slots. Very useful -->
      <!-- The nested form has hence been deleted from here. Niceeee -->
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
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
  /* I need this to keep the modal on the top stack when active. For some reason that is no longer the case. Easy fix nonetheless */
  z-index: 100;
}
.modal__content {
  width: 50rem;
  /* height: 30rem; */
  background-color: #fff;
  color: #333;
}
</style>