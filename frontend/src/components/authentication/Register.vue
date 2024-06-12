<template>
  <div>
    <h1>Register</h1>
    <form @submit.prevent="register">
      <input type="text" v-model="username" placeholder="Username" required />
      <input
        type="password"
        v-model="password"
        placeholder="Password"
        required
      />
      <button type="submit">Register</button>
    </form>
    <router-link to="/login">Already have an account? Login</router-link>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
import { authRegister } from "./../../api";

const username = ref("");
const password = ref("");
const router = useRouter();

const register = async () => {
  try {
    await authRegister(username.value, password.value);
    router.push("/login");
  } catch (error) {
    console.error(error);
  }
};
</script>
