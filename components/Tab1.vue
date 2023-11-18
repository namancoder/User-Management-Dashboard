<template>
  <div>
    <div class="flex justify-center my-4">
      <div class="relative w-1/4">
        <input
          v-model="searchTerm"
          type="search"
          id="search"
          name="search"
          placeholder="Search Users..."
          class="mt-3 !-mb-3 p-2 border border-gray-300 rounded-md focus:outline-none focus:ring focus:border-blue-300 w-full"
        />
      </div>
    </div>
    <user-table :users="filteredUsers" />
  </div>
</template>

<script>
import TableComponent from "./UserTable.vue";
import userData from "./../data/data.json";

export default {
  components: {
    "user-table": TableComponent,
  },
  data() {
    return {
      searchTerm: "",
      users: userData,
    };
  },
  computed: {
    filteredUsers() {
      const term = this.searchTerm.toLowerCase().trim();
      if (!term) {
        return this.users;
      }
      console.log("abcdefgh");
      return this.users.filter((user) => {
        for (const key in user) {
          if (Object.prototype.hasOwnProperty.call(user, key)) {
            const value = user[key].toString().toLowerCase();
            if (value.includes(term)) {
              return true;
            }
          }
        }
        return false;
      });
    },
  },
  setup() {
    useHead({
      title: "User Details",
    });
  },
};
</script>

<style scoped>
input[type="search"]::-webkit-search-cancel-button {
  -webkit-filter: grayscale(100%);
  filter: grayscale(100%);
}
</style>
