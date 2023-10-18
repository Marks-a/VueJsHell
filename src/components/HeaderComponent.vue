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
    font-family: 'Arial', sans-serif;
    background-color: #1b1f38;

  }
  
  .logo-section {
  display: flex;
  align-items: center;
}

.logo {
  width: 50px;
  margin-right: 20px;
}
  
.page-title {
  font-size: 24px;
  font-weight: bold;
}
  
  .menu-section {
    display: flex;
    align-items: center;
  }
  
  .login-logout-button {
    font-size: 1rem;
    color: white;
    border: none;
    border-radius: 5px;
    padding: 5px 10px;
    cursor: pointer;
    transition: background-color 0.3s ease;
    background-color: rgba(128, 0, 128, 0.5);
  }
  .login-logout-button:hover {
  background-color: rgba(128, 0, 128, 0.5);
}
.user-section {
  display: flex;
  align-items: center;
}
  </style>
  