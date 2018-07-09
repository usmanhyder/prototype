<template>
  <div class="hello">
    <h2 v-if="!this.$parent.activeUser">Please Login</h2>
    <h2 v-else>Welcome {{this.$parent.user.email}}</h2>
  </div>
</template>

<script>
  export default {
    name: 'home',
    data() {
      return {
        msg: 'Welcome '
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  h1, h2 {
    font-weight: normal;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #35495E;
  }
</style>
