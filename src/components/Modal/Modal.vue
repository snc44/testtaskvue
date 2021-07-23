<template>
  <div class="modal-wrapper">

    <div class="modal">
      <user-form></user-form>
    </div>

  </div>
</template>

<script>
import UserForm from '../User/UserForm/UserForm.vue'

export default {
  name: 'Modal',
  components: {
    UserForm
  },
  data () {
    return {

    }
  }
}
</script>

<style src="./Modal.css"></style>
