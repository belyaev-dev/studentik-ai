<template>
  <div>
    <chat-message v-for="(message,index) in messages" 
      :key="index" 
      :message="message.text" 
      :user="message.user"></chat-message>
    <input type="text" v-model="currentMessage" @keyup.enter="send"/>
  </div>
</template>


<script>
import axios from 'axios'; 
import ChatMessage from './ChatMessage.vue'; 

export default {
  data() {
    return {
      messages: [],
      currentMessage: '',
      apiUrl: "https://api.easyvuz.ru/v1/studentik/message/:id"
    };
  },
  methods: {
    send() {
      this.messages.push({text: this.currentMessage, user:'user'});
      axios.post(this.apiUrl, { "message": this.currentMessage }).then(response => {
        this.messages.push({text: response.data.response, user:'bot'});
        response.data.buttons.forEach(button =>
          this.messages.push({text: button, user: 'bot'})
        );
        this.currentMessage = '';
      });
    }
  },
  components: {
    'chat-message': ChatMessage
  }
};
</script>
