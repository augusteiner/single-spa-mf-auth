<template>
  <div class="h-100 d-flex align-items-center">
    <form class="m-auto" style="min-width: 400px" @submit.prevent="login()">
      <h1 class="h3 mb-3 fw-normal">
        <svg
          class="logo"
          viewBox="0 0 128 128"
          width="24"
          height="24"
          data-v-35dc6318=""
          style="width: 36px"
        >
          <path
            fill="#42b883"
            d="M78.8,10L64,35.4L49.2,10H0l64,110l64-110C128,10,78.8,10,78.8,10z"
            data-v-35dc6318=""
          ></path>
          <path
            fill="#35495e"
            d="M78.8,10L64,35.4L49.2,10H25.6L64,76l38.4-66H78.8z"
            data-v-35dc6318=""
          ></path>
        </svg>
        Please sign in
      </h1>

      <div class="form-floating">
        <input
          type="email"
          class="form-control"
          id="floatingInput"
          placeholder="name@example.com"
        />
        <label for="floatingInput">Email address</label>
      </div>
      <div class="form-floating">
        <input
          type="password"
          class="form-control"
          id="floatingPassword"
          placeholder="Password"
        />
        <label for="floatingPassword">Password</label>
      </div>

      <div class="form-check text-start my-3">
        <input
          class="form-check-input"
          type="checkbox"
          value="remember-me"
          id="flexCheckDefault"
        />
        <label class="form-check-label" for="flexCheckDefault">
          Remember me
        </label>
      </div>
      <button class="btn btn-primary w-100 py-2" type="submit">Sign in</button>
      <p class="mt-5 mb-3 text-body-secondary">© 2017–2023</p>
    </form>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  methods: {
    login() {
      const key = "single-spa-mf:user";
      const newValue = JSON.stringify({
        token: `token-${new Date().getTime()}`,
      });
      const oldValue = window.localStorage.getItem(key);

      window.localStorage.setItem(key, newValue);

      const event = new StorageEvent("storage", {
        key,
        oldValue,
        newValue,
      });

      window.dispatchEvent(event);

      history.pushState("", "", "/");
    },
  },
};
</script>

<style>
.form-signin {
  max-width: 330px;
}
</style>
