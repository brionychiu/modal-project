<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <!-- <input type="text" ref="name"/>
  <button @click="handleClick">Click me</button> -->
  <teleport to=".modals" v-if="showModal">
    <!-- <Modal :header="header" :text="text" theme="sale" @click="toggleModal"/> -->
    <Modal theme="" @close="toggleModal">
      <template v-slot:links>
        <a href="#">signup now!</a>
        <a href="#">more info</a>
      </template>
      <h1>Ninga Giveaway</h1>
      <p>Grab your ninga swag for half price!</p>
    </Modal>
  </teleport>
  <div v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>sign up to the newsletter</h1>
      <p>For updates and promo codes!</p>
    </Modal>
  </div>
  <button @click.alt="toggleModal">Open modal (alt)</button>
  <button @click="toggleModalTwo">Open modal</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'my first vue app!',
      header: 'Sign up for the Giveaway!',
      text: 'Grab your ninga swag for half price!',
      showModal: false,
      showModalTwo: false
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refsx.name.focus()
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
#app , .modals{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
