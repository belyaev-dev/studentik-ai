<template>
    <div>
      <p v-if="user == 'bot'">Bot: {{message}}</p>
      <p v-else>User: {{message}}</p>
    </div>
  </template>
  
  <script>
  export default {
    props: ['message', 'user']
  };
  </script>
  