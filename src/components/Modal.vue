<template>
  <div @click.self="$emit('forwardClick')" v-if="showModalProp" class="modal">
    <div class="modal__content">
      <PersonForm />
    </div>
  </div>
</template>

<script>
import PersonForm from "./AddPersonForm";
export default {
  components: {
    PersonForm: PersonForm
  },
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
  /* height: 30rem; */
  background-color: #fff;
  color: #333;
}
</style>