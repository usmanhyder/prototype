<template>
  <div id="app">
    <header>
      <b-navbar toggleable="md" type="dark">
        <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
        <b-navbar-brand to="/">EIT Prototype</b-navbar-brand>
        <b-collapse is-nav id="nav_collapse">
          <b-navbar-nav class="ml-auto">
            <b-nav-item to="/login" v-if="!activeUser">Login</b-nav-item>
            <b-nav-item href="/" v-on:click="logout" v-else>Logout</b-nav-item>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </header>
    <main>
      <router-view></router-view>
    </main>
  </div>
</template>

<script>
  /*  import Home from '@/components/Home';
    import Login from '@/components/Login';*/

  export default {
    name: 'app',
    /*    components: {
          Home,
          Login
        },*/
    data() {
      return {
        activeUser: null,
        user: {}
      }
    },
    methods: {
      logout: function () {
        this.activeUser = null;
      }
    }
  }
</script>

<style>
  body {
    margin: 0;
  }

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
  }

  main {
    text-align: center;
    margin-top: 40px;
  }

  header {
    margin: 0;
    height: 56px;
    padding: 0 16px 0 24px;
    background-color: #35495E;
    color: #ffffff;
  }

  header span {
    display: block;
    position: relative;
    font-size: 20px;
    line-height: 1;
    letter-spacing: .02em;
    font-weight: 400;
    box-sizing: border-box;
    padding-top: 16px;
  }
</style>
