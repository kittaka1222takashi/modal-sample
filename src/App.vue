<template>
  <div id="app">
    <Modal @delete="deleteMemo" ref="childModal"/>
    <Memos @confirm="deleteConfirm" ref="childMemos"/>
    <Message ref="childMessage"/>
  </div>
</template>

<script>
import Modal from './components/Modal.vue'
import Message from './components/Message.vue'
import Memos from './components/Memos.vue'

export default {
  name: 'app',
  components: {
    Modal,
    Memos,
    Message
  },
  methods: {
    deleteConfirm(i) {
      this.$refs.childModal.showModal(i)
    },
    deleteMemo(i) {
      this.$refs.childMemos.deleteMemo(i)
      this.$refs.childModal.hideModal(i)
      this.$refs.childMessage.showMessage(true)
    },
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
