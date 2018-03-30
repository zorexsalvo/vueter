<template>
  <div>
    <div class="columns">
      <div class="column is-one-third is-offset-one-third">
        <h6 class="title">Sign Up</h6>

        <div class="field">
          <div class="control">
            <input class="input" type="text" placeholder="Email">
          </div>
        </div>

        <div class="field">
          <div class="control">
            <input class="input" type="password" placeholder="Password">
          </div>
        </div>

        <div class="field is-grouped">
          <div class="control">
            <button class="button is-link">Register</button>
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
