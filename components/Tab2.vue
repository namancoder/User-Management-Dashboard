<template>
  <div class="max-w-md mx-auto mt-8">
    <form
      @submit.prevent="submitForm"
      class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4"
    >
      <div class="mb-4">
        <label
          class="block text-gray-700 text-sm font-bold mb-2"
          for="username"
        >
          Username
        </label>
        <input
          v-model="username"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          id="username"
          type="text"
          placeholder="Enter your username"
        />
      </div>
      <div class="mb-6">
        <label
          class="block text-gray-700 text-sm font-bold mb-2"
          for="password"
        >
          Password
        </label>
        <input
          v-model="password"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          id="password"
          type="password"
          placeholder="********"
        />
      </div>
      <div class="flex items-center justify-between">
        <button
          type="submit"
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
        >
          Submit
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  setup() {
    useHead({
      title: "Account Creation",
    });
  },
  data() {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    submitForm() {
      if (this.username == "" || this.password == "") {
        alert("Please fill all the fields");
        return;
      }
      // Simulate an asynchronous request
      setTimeout(() => {
        alert(
          `Log in Successful!\nUsername: ${this.username}\nPassword: ${this.password}`
        );
        this.username = "";
        this.password = "";
      }, 1000);
    },
  },
};
</script>
