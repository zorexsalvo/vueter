<template>
  <div>
    <div class="columns">
      <div class="column is-one-third is-offset-one-third">
        <h6 class="title">Sign In</h6>

        <div class="field">
          <div class="control">
            <input
              class="input"
              type="text"
              placeholder="Email"
              v-model="email">
          </div>
        </div>

        <div class="field">
          <div class="control">
            <input
              class="input"
              type="password"
              placeholder="Password"
              v-model="password">
          </div>
        </div>

        <div class="field is-grouped">
          <div class="control">
            <button
              class="button is-link"
              @click="logIn">
              Login
            </button>
          </div>
          <div class="control">
            <router-link
              class="button is-text"
              :to="{ name: 'SignUp' }">
              Don't have an account yet? Sign Up
            </router-link>
          </div>
        </div>

      </div>
    </div>

  </div>
</template>

<script>
import firebase from 'firebase';

export default {
  name: 'login',
  data() {
    return {
      email: '',
      password: '',
    };
  },
  methods: {
    logIn() {
      firebase.auth().signInWithEmailAndPassword(this.email, this.password).then(
        () => {
          // eslint-disable-next-line
          alert('Login succesful!');
        },
        (err) => {
          // eslint-disable-next-line
          alert('Oops.' + err.message);
        },
      );
    },
  },
};
</script>
