<template>
  <div>

    <div class="columns">
      <div class="column is-one-third is-offset-one-third">
        Welcome, {{ currentUser.email }}!
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

    <div class="columns">
      <div class="column is-one-third is-offset-one-third">
        <div class="field has-addons">
          <div class="control">
            <input
              class="input is-fullwidth"
              type="text"
              placeholder="What's happening?"
              v-model="post"
              @keyup.enter="postIt">
          </div>
          <div class="control">
            <a class="button is-info"
               @click="postIt">
              vuueeeet!
            </a>
          </div>
        </div>
      </div>
    </div>

    <div class="columns">
      <div class="column is-one-third is-offset-one-third">
        <div
          class="box"
          v-for="post in posts"
          :key="post.id">
          <article class="media">
            <div class="media-content">
              <div class="content">
                <p>
                  {{ post.post }}
                  <br>
                  <small>/{{ post.email }}</small>
                </p>
              </div>
            </div>
          </article>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
import firebase from 'firebase';

export default {
  name: 'home',
  data() {
    return {
      post: '',
      posts: [],
    };
  },
  methods: {
    signOut() {
      firebase.auth().signOut().then(() => {
        this.$router.replace('login');
      });
    },
    postIt() {
      const newPostReference = firebase.database().ref('posts/').push();
      newPostReference.set({
        post: this.post,
        email: this.currentUser.email,
      });
      this.refreshFeed();
    },
    refreshFeed() {
      this.post = '';
      const reference = firebase.database().ref('posts/');
      reference.once('value').then(
      (data) => {
        this.posts = data.val();
      });
    },
  },
  computed: {
    currentUser() {
      return firebase.auth().currentUser;
    },
  },
  created() {
    const reference = firebase.database().ref('posts/');
    reference.once('value').then(
      (data) => {
        this.posts = data.val();
      });
  },
};
</script>
