<template>
  <b-modal ref="modal" size="xl" hide-footer hide-header>
    <div class="d-block text-center">
      <p>本当に削除しますか？</p>
    </div>
    <b-button class="delete-button" variant="success" block @click="hideModal()">いいえ</b-button>
    <b-button class="delete-button" variant="danger" block @click="deleteMemo()">はい</b-button>
  </b-modal>
</template>

<script>
export default {
  name: 'Modal',
  data() {
    return {
      deleteIndex: ""
    }
  },
  methods: {
    showModal(i){
      this.deleteIndex = i;
      this.$refs.modal.show()
    },
    hideModal(){
      this.deleteIndex = "";
      this.$refs.modal.hide()
    },
    deleteMemo(){
      this.$emit('delete', this.deleteIndex);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
