<template>
  <transition name="message">
    <div v-if="messageActive" id="message-parent">
      <div id="message">
        <b-alert :show="dismissCountDown" v-bind:variant="variant" @dismiss-count-down="countDownChanged">
          {{ message }}
        </b-alert>
      </div>
     </div>
  </transition>
</template>
<script>
export default {
  name: 'Message',
  data() {
    return {
      // message表示用データ
      dismissSecs: 2,
      dismissCountDown: 0,
      message: '',
      variant:'',
      messageActive:false,
    }
  },
  methods: {
    countDownChanged (dismissCountDown) {
      this.dismissCountDown = dismissCountDown
      if (dismissCountDown == 0) {
        this.messageActive = false;
      }
    },
    showMessage: function (success) {
      this.message = success ? "削除しました" : "エラーが発生しました";
      this.variant = success ? "success" : "danger";
      this.dismissCountDown = this.dismissSecs;
      this.messageActive = true;
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.message-enter-active, .message-leave-active {
  transition: opacity 0.5s;
}
.message-enter, .message-leave-to {
  opacity: 0;
}
#message-parent {
  width:100%;
}
#message {
  position: fixed;
  top: 5px;
  right: 0;
  left: 0;
  margin-left: auto;
  margin-right: auto;
  box-sizing:border-box;
  width:95%;
}
</style>
