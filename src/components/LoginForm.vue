<template>
    <form @submit.prevent="submitForm">
      <label for="name">Name:</label>
      <input v-model="formData.name" type="text" id="name" required />
  
      <label for="surname">Surname:</label>
      <input v-model="formData.surname" type="text" id="surname" required />
  
      <label for="code">ViA Code:</label>
      <input v-model="formData.code" type="text" id="code" required />
  
      <button type="submit">Submit</button>
    </form>
  </template>
  
  <script>
  export default {
    data() {
      return {
        formData: {
          name: '',
          surname: '',
          code: '',
        },
      };
    },
    methods: {
      submitForm() {
        this.$emit('login-success', this.formData);
      },
    },
  };
  </script>
  
  <style scoped>
  .login-form {
    background: #f9f9f9;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    max-width: 300px;
    margin: 0 auto;
  }
  
  .form-group {
    margin-bottom: 10px;
  }
  
  label {
    display: block;
    font-weight: bold;
  }
  
  input {
    width: 100%;
    padding: 5px;
    border: 1px solid #ccc;
    border-radius: 3px;
  }
  </style>
  