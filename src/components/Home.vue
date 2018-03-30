<template>
  <div>
    <div class="columns">
      <div class="column is-one-third is-offset-one-third">
        You must be authenticated to access this page.
      </div>
    </div>
    <div class="columns">
      <div class="column is-one-third is-offset-one-third">
        <div class="control">
          <button
            class="button is-fullwidth"
            @click="signOut">Logout</button>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
import firebase from 'firebase';

export default {
  name: 'home',
  methods: {
    signOut() {
      firebase.auth().signOut().then(() => {
        this.$router.replace('login');
      });
    },
  },
};
</script>
