<template>
    <div class="navigation">
      <button
        v-if="loggedIn"
        :class="{ active: activeTab === 'home' }"
        @click="selectTab('home')"
      >
        HOME
      </button>
      <button
        v-if="loggedIn"
        :class="{ active: activeTab === 'about' }"
        @click="selectTab('about')"
      >
        ABOUT ME
      </button>
    </div>
  </template>
  
  <script>
  export default {
    props: ['activeTab', 'loggedIn'],
    methods: {
      selectTab(tab) {
        if (this.loggedIn) {
          this.$emit('tab-selected', tab);
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .navigation {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  button {
    v-if: loggedIn;
    background: none;
    border: none;
    padding: 5px 10px;
    cursor: pointer;
    font-size: 16px;
  }
  
  button.active {
    font-weight: bold;
  }
  </style>
  