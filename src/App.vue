<!-- <script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>


<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />
    <h1></h1>
    <div class="wrapper">
      <HelloWorld msg="Hello !" />
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style> -->

<template>
  <div class="app">
    <HeaderComponent :loggedIn="loggedIn" @user-logged-in="userLoggedIn" @user-logged-out="userLoggedOut" :user="submittedUser" />
    <div class="content">
      <NavigationComponent :activeTab="activeTab" @tab-selected="tabSelected" :loggedIn="loggedIn" />
      <div class="main-content">
        <div v-if="loggedIn">
          <HomeComponent v-if="activeTab === 'home'" />
          <AboutMeComponent v-if="activeTab === 'about'" :user="submittedUser" />
        </div>
        <LoginForm v-if="showLogin" @login-success="onLoginSuccess" />
      </div>
    </div>
  </div>
</template>


<script>
import HeaderComponent from './components/HeaderComponent.vue';
import NavigationComponent from './components/NavigationComponent.vue';
import HomeComponent from './components/HomeComponent.vue';
import AboutMeComponent from './components/AboutMeComponent.vue';
import LoginForm from './components/LoginForm.vue'; // Import the new LoginForm component

export default {
  components: {
    HeaderComponent,
    NavigationComponent,
    HomeComponent,
    AboutMeComponent,
    LoginForm,
  },
  data() {
    return {
      activeTab: 'home',
      loggedIn: false,
      showLogin: false,
      user: {
        name: 'Your Name',
        surname: 'Your Surname',
        code: 'Your ViA code',
      },
      submittedUser: null,
    };
  },
  methods: {
    tabSelected(tab) {
      this.activeTab = tab;
    },
    userLoggedIn() {
      this.showLogin = true;
    },
    userLoggedOut() {
      this.loggedIn = false;
      this.showLogin = false;
      this.submittedUser = null;
    },
    onLoginSuccess(submittedUser) {
      this.loggedIn = true;
      this.showLogin = false;
      this.submittedUser = submittedUser;
    },
  },
};
</script>



<style scoped>
.app {
  background-color: grey;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  color: aqua;
}

.content {
  display: flex;
  align-items: left;
  justify-content: center;
  height: 100vh;
  width: 100%;
}

.main-content {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  
}
</style>