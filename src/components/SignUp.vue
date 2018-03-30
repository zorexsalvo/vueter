<template>
  <div>
    <div class="columns">
      <div class="column is-one-third is-offset-one-third">
        <h6 class="title">Sign Up</h6>

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
              @click="signUp">
              Register
            </button>
          </div>
          <div class="control">
            <router-link
              :to='{ name: "Login" }'
              class="button is-text">
              Already Have an Account? Login
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
  name: 'signup',
  data() {
    return {
      email: '',
      password: '',
    };
  },
  methods: {
    signUp() {
      firebase.auth().createUserWithEmailAndPassword(this.email, this.password).then(
        () => {
          // eslint-disable-next-line
          alert('Your account has been created');
        },
        (err) => {
          // eslint-disable-next-line
          alert('Oops. ' + err.message);
        },
      );
    },
  },
};
</script>
