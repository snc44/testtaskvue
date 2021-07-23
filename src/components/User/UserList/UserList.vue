<template>
  <div class="user_table">
    <div class="userlist" v-for="user in usrs" :key="user.id">
      <user :user="user" :isBossUser="isBossUser(user)"></user>
      <div class="sub-user-list" v-for="subuser in getSubUsers(user)" :key="subuser.id">
        <user :user="subuser" isSubUser></user>
      </div>
    </div>
  </div>
</template>

<script>
import User from '../User/User.vue'

export default {
  name: 'UserList',
  components: {
    User
  },
  data () {
    return {

    }
  },
  props: {
    users: Array
  },
  computed: {
    usrs () {
      return this.users.filter(user => user.bossId === undefined)
    }
  },
  methods: {
    isBossUser (user) {
      return !!this.users.find(u => u.bossId === user.id)
    },
    getSubUsers (user) {
      return this.users.filter(u => u.bossId === user.id)
    }
  }
}
</script>

<style src="./UserList.css"></style>
