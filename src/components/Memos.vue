<template>
  <div class="container">
    <b-list-group>
      <b-list-group-item v-for="memo,i in memos"><b>{{ memo.title }}</b>{{ memo.text }}<b-button variant="danger" @click="deleteComfirm(i)">削除</b-button></b-list-group-item>
    </b-list-group>
  </div>
</template>

<script>
export default {
  name: 'Memos',
  data() {
    return {
      memos: [
        {"title": "title1", "text": "memomemoemomeo"},
        {"title": "title2", "text": "memomemomemomemo"},
        {"title": "title3", "text": "memomemomemomemo"},
        {"title": "title4", "text": "memomemomemomemo"},
        {"title": "title5", "text": "memomemomemomemo"},
        {"title": "title6", "text": "memomemomemomemo"},
        {"title": "title7", "text": "memomemomemomemo"},
        {"title": "title8", "text": "memomemomemomemo"},
        {"title": "title9", "text": "memomemomemomemo"},
      ]
    }
  },
  methods: {
    deleteComfirm(i) {
      this.$emit('confirm', i);
    },
    deleteMemo(i) {
      this.memos.splice(i, 1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
