<template>
  <div class="user-form">
    <form>
      <label for="name">Name</label>
      <input v-model="newUser.name" type="text">

      <label for="phone">Phone</label>
      <input v-model="newUser.phone" type="text">

      <label for="boss">Boss</label>
      <select v-model="newUser.bossId">
        <option>NO</option>
        <option v-for="boss in users" :key="boss.id" :value="boss.id">{{ boss.name }}</option>
      </select>

      <button @click="save">Save</button>
    </form>
  </div>
</template>

<script>
// generates random id; https://learnersbucket.com/examples/javascript/unique-id-generator-in-javascript/
const guid = () => {
  const s4 = () => {
    return Math.floor((1 + Math.random()) * 0x10000)
      .toString(16)
      .substring(1)
  }
  // return id of format 'aaaaaaaa'-'aaaa'-'aaaa'-'aaaa'-'aaaaaaaaaaaa'
  return s4() + s4() + '-' + s4() + '-' + s4() + '-' + s4() + '-' + s4() + s4() + s4()
}

export default {
  name: 'UserForm',
  components: {

  },
  data () {
    return {
      newUser: {
        id: '',
        name: '',
        phone: '',
        bossId: ''
      },
      users: []
    }
  },
  methods: {
    save () {
      this.newUser.id = guid()
      this.users.push(this.newUser)
      localStorage.setItem('users', JSON.stringify(this.users))
      this.clear()
      this.fetchLocalStorage()
    },
    clear () {
      this.newUser.id = ''
      this.newUser.name = ''
      this.newUser.phone = ''
      this.newUser.bossId = undefined
    },
    // todo, локалсторадж вынести в миксин
    fetchLocalStorage () {
      if (localStorage.getItem('users')) {
        this.users = JSON.parse(localStorage.getItem('users'))
      }
    }
  },
  mounted () {
    this.fetchLocalStorage()
  }
}
</script>

<style src="./UserForm.css"></style>
