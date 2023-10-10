<template>
  <section class="chat">
    <div class="chat-user">
      <ChatTop name="Александр" img="alex" />
      <ChatMain sender="1" :msgs="msgs" />
      <ChatBottom sender="1" @msg="sendMsg" />
    </div>
    <div class="chat-user">
      <ChatTop  name="Евгений" img="jenya" />
      <ChatMain sender="2" :msgs="msgs"  />
      <ChatBottom sender="2" @msg="sendMsg" />
    </div>
  </section>
</template>
<script>
import ChatBottom from './components/ChatBottom.vue'
import ChatMain from './components/ChatMain.vue'
import ChatTop from './components/ChatTop.vue'
export default {
  components: { ChatTop, ChatMain, ChatBottom },
  data() {
    return {
      msgs: localStorage.message ? JSON.parse(localStorage.message) : []
    }
  },
  methods: {
    sendMsg(msg){
      this.msgs.push(msg)
      localStorage.message = JSON.stringify(this.msgs)
    }
  },
}
</script>
<style>
  
</style>