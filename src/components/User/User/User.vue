<template>
  <div :class="`user ${isSubUser ? 'sub-user' : ''}`">
    <div class="user_name">{{ formattedName }}</div>
    <div class="user_phone">{{ user.phone }}</div>
  </div>
</template>

<script>
export default {
  name: 'user',
  data () {
    return {

    }
  },
  props: {
    user: Object,
    isSubUser: Boolean,
    isBossUser: Boolean
  },
  computed: {
    formattedName () {
      const name = this.user.name
      if (this.isSubUser || this.isBossUser) {
        return `+ ${name}`
      }
      return name
    }
  }
}
</script>

<style src="./User.css"></style>
