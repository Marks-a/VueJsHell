<template>
    <div class="about-me">
      <h1>ABOUT ME</h1>
      <h3>Name: {{ user.name }}</h3>
      <h3>Surname: {{ user.surname }}</h3>
      <h3>Code: {{ user.code }}</h3>
    </div>
  </template>
  
  <script>
  export default {
    props: ['user'],
  };
  </script>
  
  <style scoped>
  .about-me {
    text-align: left;
    margin-top: 20px;
    font-size: 20px;
    
  }
  </style>
  