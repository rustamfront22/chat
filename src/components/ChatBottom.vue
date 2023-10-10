<template>
  <div class="chat-bottom">
    <input
      placeholder="Написать сообщение..."
      v-model="msg"
      @keyup.enter="sendMsg"
    >
    <button v-show="msg.length">
      <img src="@/assets/img/send.svg" alt="" @click="sendMsg" />
    </button>
    <button v-show="!msg.length" @click="window = true">
      <img src="@/assets/img/photo.svg" alt="" />
    </button>
    <div class="window" v-show="window" >
        <div class="window-body">
            <h3>Отправить картинку</h3>
            <div class="window-body-form">
                <label>
                    <span>URL</span>
                    <input type="text" placeholder="URL">
                </label>
                <label>
                    <span>Комментарий</span>
                    <input type="text" placeholder="Комментарий">
                </label>
            </div>
            <div class="window-btns">
                <button class="btn red">ОТМЕНА</button>
                <button class="btn purple">ОТПРАВИТЬ</button>
            </div>
        </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      msg: "",
      window: false
    };
  },
  props: ["sender"],
  methods: {
    sendMsg() {
      let hour = new Date().getHours();
      let min = new Date().getMinutes();
      const time = `${hour < 10 ? "0" + hour : hour}:${
        min < 10 ? "0" + min : min
      }`;
      if (this.msg.length) {
        const message = {
          body: this.msg.trim(),
          sendId: this.sender,
          time: time,
        };
        if (this.msg.trim() != "") {
          this.$emit("msg", message);
          this.msg = "";
        }
      }
    },
    // sendImg() {
    //   let hour = new Date().getHours();
    //   let min = new Date().getMinutes();
    //   const time = `${hour < 10 ? "0" + hour : hour}:${
    //     min < 10 ? "0" + min : min
    //   }`;
    //   if (this.msg.length) {
    //     const message = {
    //       body: this.msg.trim(),
    //       sendId: this.sender,
    //       time: time,
    //     };
    //     if (this.msg.trim() != "") {
    //       this.$emit("msg", message);
    //       this.msg = "";
    //     }
    //   }
    // },
  },
};
</script>
<style>
</style>