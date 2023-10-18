<template>
    <div class="navigation">
      <button
        v-if="loggedIn"
        :class="{ active: activeTab === 'home' }"
        @click="selectTab('home')"
        class="navigation-button"
      >
        HOME
      </button>
      <button
        v-if="loggedIn"
        :class="{ active: activeTab === 'about' }"
        @click="selectTab('about')"
        class="navigation-button"
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
  .navigation-button {
  padding: 10px 20px;
  background-color: transparent;
  border: none;
  font-size: 1rem;
  color: white;
  cursor: pointer;
  transition: background-color 0.3s ease;
}
.navigation-button.active {
  background-color: purple;
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.2);
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
  