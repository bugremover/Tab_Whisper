<template>
  <div class="flex items-center justify-center min-h-screen bg-gray-100">
    <form @submit.prevent="handleLogin" class="bg-white p-8 rounded-2xl shadow-md w-full max-w-sm">
      <h1 class="text-2xl font-semibold mb-6 text-center text-gray-800">Login</h1>

      <div class="mb-4">
        <label for="email" class="block text-sm font-medium text-gray-700 mb-1">Email</label>
        <input
          id="email"
          v-model="email"
          type="email"
          placeholder="Enter your email"
          class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-blue-200"
          required
        />
      </div>

      <div class="mb-6">
        <label for="password" class="block text-sm font-medium text-gray-700 mb-1">Password</label>
        <input
          id="password"
          v-model="password"
          type="password"
          placeholder="Enter your password"
          class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-blue-200"
          required
        />
      </div>

      <button
        type="submit"
        class="w-full bg-blue-600 text-white py-2 rounded-md hover:bg-blue-700 transition"
      >
        Login
      </button>

      <p v-if="message" class="mt-4 text-center text-sm text-gray-700">{{ message }}</p>
    </form>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue'

const email = ref('')
const password = ref('')
const message = ref('')

function handleLogin() {
  if (!email.value || !password.value) {
    message.value = 'Please fill in both fields'
    return
  }

  if (email.value === 'test@example.com' && password.value === '1234') {
    message.value = '✅ Login successful!'
  } else {
    message.value = '❌ Invalid email or password'
  }
}
</script>

<style scoped>
body {
  font-family: system-ui, sans-serif;
}
</style>
