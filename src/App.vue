<template>
  <img alt="Vue logo"  src="./assets/logo.png">
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <teleport to='body'> 
    <Modal 
    v-if="isShowModal"
    title="Modal title" 
    content="Woohoo, you're reading this text in a modal!"
    theme="contact"
    v-on:close="onToggleModal"
    >
      <template v-slot:header>
        <div>
            <h2>this is header</h2>
            <button>
              <span aria-hidden="true" @click="onToggleModal">×</span>
            </button>
        </div>
      </template>
      <label for="">name</label>
      <input type="text">
    </Modal>
  </teleport>
  <button @click="onToggleModal">Toggle Modal</button>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Modal from './components/ModalComponent.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    Modal
    //baseModal:Modal
  },
  data() {
    return {
      isShowModal: false,

    }
  }, 
  methods: {
    onToggleModal() {
      this.isShowModal = !this.isShowModal
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
