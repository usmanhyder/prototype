<template>
  <div class="login">
    <h2>{{ msg }}</h2>
    <b-row>
      <b-col></b-col>
      <b-col>
        <div>
          <b-card bg-variant="light">
            <b-form v-on:submit.prevent="loginUser" v-if="show">
              <b-form-group id="emailInputGroup">
                <b-form-input id="emailInput"
                              type="text"
                              v-model="user.email"
                              required
                              placeholder="Email">
                </b-form-input>
              </b-form-group>
              <b-form-group id="passwordInputGroup">
                <b-form-input id="passwordInput"
                              type="password"
                              v-model="user.password"
                              required
                              placeholder="Password">
                </b-form-input>
              </b-form-group>
              <b-button type="submit" variant="primary">Submit</b-button>
            </b-form>
          </b-card>
        </div>
      </b-col>
      <b-col></b-col>
    </b-row>

  </div>
</template>

<script>
  import {APIENDPOINT} from "../app.config";
  import axios from 'axios';

  export default {
    name: 'login',
    data() {
      return {
        msg: 'Login Form',
        user: {
          email: 'admin',
          password: 'admin'
        },
        show: true,
        users: [],
        errors: []
      }
    },
    methods: {
      loginUser: function () {
        var app = this;
        console.log("Form Submited", this.form);
        console.log({email: app.user.email, password: app.user.password});
        var http = axios.create({
          baseURL: APIENDPOINT,
          auth: {
            username: app.user.email,
            password: app.user.password
          }
        })
        http.get('users').then(response => {
          this.users = response.data;
          app.$parent.activeUser = true;
          app.$parent.user = app.user;
          app.$router.push('/');
        }).catch(e => {
          this.errors.push(e);
          alert("Wrong Credentials");
        });
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
