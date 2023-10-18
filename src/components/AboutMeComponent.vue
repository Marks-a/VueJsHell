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
    position: absolute;
  top: 90px;
  left: 200px;
  color: white; 
}
h1 {
  font-weight: bold;
}
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}
  </style>
  