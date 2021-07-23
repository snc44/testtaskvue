<template>
  <div class="users-page">

    <div class="users-archive">
      <user-list :users="users"></user-list>
    </div>

    <modal></modal>

  </div>
</template>

<script>
import UserList from '../../components/User/UserList/UserList.vue'
import Modal from '../../components/Modal/Modal.vue'

// для теста
const users = [
  {
    id: 1,
    name: 'Ivan',
    phone: '245124',
    bossId: 3
  },
  {
    id: 2,
    name: 'Valeriy',
    phone: '321489'
    // bossId: 1
  },
  {
    id: 3,
    name: 'Petua',
    phone: '21124'
  }
]

export default {
  name: 'Users',
  components: {
    UserList,
    Modal
  },
  data () {
    return {
      users: users
    }
  }
}
</script>

<style src="./Users.css"></style>
