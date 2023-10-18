<!-- <template>
    <div class="header">
      <div class="logo-section">
        <img src="@/assets/logo.svg" alt="Logo" class="logo" />
        <span class="page-title">KRAKEN.FM</span>
      </div>
      <div class="menu-section">
        <span v-if="loggedIn" class="user-name">Marks</span>
        <button @click="handleLoginLogout" class="login-logout-button">{{ loggedIn ? 'LOGOUT' : 'LOGIN' }}</button>
      </div>
    </div>
  </template>
  <script>
  export default {
    props: ['loggedIn'],
    methods: {
      handleLoginLogout() {
        if (this.loggedIn) {
          this.$emit('user-logged-out');
        } else {
          const userConfirmation = confirm('Would you like to log in?');
          if (userConfirmation) {
            this.$emit('user-logged-in');
          }
        }
      }
    }
  };
  </script>
   -->



   <template>
    <div class="header" :style="headerStyle">
      <div class="logo-section">
        <img src="@/assets/logo.svg" alt="Logo" class="logo" />
        <span class="page-title">KRAKEN.FM</span>
      </div>
      <div class="menu-section">
        <span v-if="loggedIn">{{ user.name }} {{ user.surname }} </span>
        <button @click="handleLoginLogout" class="login-logout-button">
          {{ loggedIn ? 'LOGOUT' : 'LOGIN' }}
        </button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ['loggedIn', 'user'],
    computed: {
      headerStyle() {
        return {
          backgroundColor: this.loggedIn ? 'your-chosen-color' : '',
        };
      },
    },
    methods: {
      handleLoginLogout() {
        if (this.loggedIn) {
          if (confirm('Do you want to log out?')) {
            this.$emit('user-logged-out');
          }
        } else {
          if (confirm('Do you want to log in?')) {
            this.$emit('user-logged-in');
          }
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .header {
    display: flex;
    justify-content: space-between;
    padding: 10px 20px;
    background-color: #333; /* Default background color */
    color: white;
  }
  
  .logo-section {
    display: flex;
    align-items: center;
  }
  
  .page-title {
    margin-left: 10px;
  }
  
  .menu-section {
    display: flex;
    align-items: center;
  }
  
  .login-logout-button {
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    padding: 5px 10px;
    cursor: pointer;
  }
  
  .user-name {
    margin-right: 10px;
    font-weight: bold;
    font-size: 16px;
  }
  </style>
  