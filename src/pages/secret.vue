<script setup>
  import { onUnmounted, ref } from 'vue'
  import useChat from '../composable/useChat'
  import useAuth from '../composable/useAuth'

  const { messages, unsubscribe, sendMessage } = useChat()
  const { user } = useAuth()

  const newMessage = ref('')

  const send = () => {
    sendMessage(newMessage.value)
    newMessage.value = ''
  }

  onUnmounted(() => {
    unsubscribe()
  })
</script>

<template>
  <div
    class="flex flex-col items-center justify-center space-y-6 "
  >
    <h2 class="font-mono text-6xl font-bold tracking-tighter text-yellow-700">
      Chat
    </h2>
    <img width=250 src="../assets/babyYoda.gif" alt="About" />
  </div>

  <div
    class="
      min-h-[400px]
      w-full
      mt-8
      rounded-lg
      shadow-2xl
      flex flex-col
      justify-between "
  >
    <ul class="p-4 space-y-4">
      <li v-for="message in messages" :key="message.id">
<div
          class="flex justify-between px-4 py-2 font-mono rounded-lg "
          :class="user === message.author ? 'bg-green-200' : 'bg-gray-200'"
        >
          <span>{{ message.text }}</span
          ><span>by {{ message.author }}</span>
        </div>
      </li>
    </ul> 
    <div>
      
      <input
        class="w-full p-4 mb-5 border border-blue-700 border-dotted rounded-lg focus:border-none focus:bg-pink-200"
        type="text"
        placeholder="Type a message..."
        v-model="newMessage"
                @change="send"
      />
    </div>
  </div>
</template>