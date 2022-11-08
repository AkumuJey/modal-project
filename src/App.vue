<template>
  <div>
    <h1>{{ title }}</h1>
    <input type="text" ref="name">
    <button @click="handleClick">click me</button>
    <teleport to=".modals" v-if="showModal">
      <Modal theme="" @close="toggleModal">
        <h1 contenteditable="true">Write here</h1>
        <template v-slot:links>
          <a href="#">Sign Up Now</a>
          <a href="#">Get Buddies</a>
        </template>
            <p>Modal Content</p>
            <h1>{{ header }}</h1>
            <p>{{ text }}</p>
      </Modal>
    </teleport>
    <teleport to=".modals" v-if="showModalTwo">
      <Modal @close="toggleModalTwo">
        <h1 contenteditable="true">Sign up for chnage</h1>
        <p>For more updates on the change movement</p>
      </Modal>
    </teleport>
    <p>Welcome...</p>
    <button @click="toggleModal">Show Modal</button>
    <button @click="toggleModalTwo">CHANGE</button>
  </div>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: "MY First View App :)",
      showModal: false,
      showModalTwo: false
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name)
      this.$refs.name.classList.add("active")
      this.$refs.name.focus()
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  }
}
</script>

<style>
#app, #modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
