<template>
    <div class="container">
        <div>
            <Message
            v-for="{ id, text, userPhotoURL, userName, userId } in messages"
            :key="id"
            :name="userName"
            :photo-url="userPhotoURL"
            :sender="userId === user?.uid" 
        >     
        {{ text }}       
            </Message>
            
        </div>
    </div>
    <div ref="bottom" />

  <div class="bottom">
     <form v-if="isLogin" @submit.prevent="send">
      <input v-model="message" placeholder="Message" required />
      <button type="submit"><SendIcon/>Enviar</button>
    </form>

  </div>
</template>

<script>
import { ref, watch, nextTick } from 'vue'
import { useAuth, useChat } from '@/firebase'
import SendIcon from './SendIcon.vue'
import Message from './MessageC.vue'
export default {
  components: { Message, SendIcon },
  setup() {
    const { user, isLogin } = useAuth()
    const { messages, sendMessage } = useChat()
    const bottom = ref(null)
    watch(
      messages,
      () => {
        nextTick(() => {
          bottom.value?.scrollIntoView({ behavior: 'smooth' })
        })
      },
      { deep: true }
    )
    const message = ref('')
    const send = () => {
      sendMessage(message.value)
      message.value = ''
    }
    return { user, isLogin, messages, bottom, message, send }
  }
}
</script>

<style>
.container {
  width: 90%;
 
  background-color: brown;
}
</style>