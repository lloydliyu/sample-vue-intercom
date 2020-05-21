<template>
  <div>
    <label for="user_id">User ID:
      <input id="user_id" name="user_id" type="text" placeholder="User ID" v-model="user.user_id" />
    </label>
    <label for="email">Email:
      <input id="email" name="email" type="email" placeholder="Email" v-model="user.email" />
    </label>
    <button @click="login(user)">Login</button>
    <button @click="logout()">Logout</button>
    <button @click="trackEvent('won-the-lottery')">Win the lottery</button>
  </div>
</template>

<script>
export default {
  name: 'Panel',
  data: () => ({
    user: {},
  }),
  methods: {
    logout: () => {
      window.Intercom('shutdown');
    },
    login: (user) => {
      window.Intercom('update', user);
    },
    trackEvent: (eventName) => {
      window.Intercom('trackEvent', eventName);
    },
  },
};
</script>

<style scoped>
  label {
    display: block;
  }
</style>
