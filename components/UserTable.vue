<template>
  <div class="container mx-auto">
    <table
      class="min-w-full bg-white border border-gray-300"
      aria-describedby="User Table"
    >
      <thead>
        <tr>
          <th class="py-2 px-4 border-b">ID</th>
          <th class="py-2 px-4 border-b">Username</th>
          <th class="py-2 px-4 border-b">Email</th>
          <th class="py-2 px-4 border-b">Phone</th>
          <th class="py-2 px-4 border-b">Creation Date</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="user in users"
          :key="user.id"
          @click="openDialog(user)"
          class="hover:bg-blue-200 cursor-pointer"
        >
          <td class="py-2 px-4 border-b">{{ user.id }}</td>
          <td class="py-2 px-4 border-b">{{ user.username }}</td>
          <td class="py-2 px-4 border-b">{{ user.email }}</td>
          <td class="py-2 px-4 border-b">{{ user.phone }}</td>
          <td class="py-2 px-4 border-b">{{ user["creation-date"] }}</td>
        </tr>
      </tbody>
      <!-- Dialog -->
      <dialog ref="userDialog">
        <user-dialog :selected-user="selectedUser" :closeDialog="closeDialog" />
      </dialog>
    </table>
  </div>
</template>

<script>
import UserDialogVue from "./UserDialog.vue";

export default {
  props: {
    users: Array,
  },
  components: {
    "user-dialog": UserDialogVue,
  },
  data() {
    return {
      selectedUser: null,
    };
  },
  methods: {
    openDialog(user) {
      this.selectedUser = user;
      this.$refs.userDialog.showModal();
    },
    closeDialog() {
      this.selectedUser = null;
      console.log("closeDialog");
      this.$refs.userDialog.close();
    },
  },
};
</script>

<style scoped>
th,
td {
  text-align: left;
}

dialog[open] {
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  top: 0;
  left: 0;
  width: 420px;
  height: 300px;
}

.dialog-content {
  background-color: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  text-align: left;
  max-width: 400px;
  width: 100%;
  z-index: 2;
  position: absolute;
}

.dialog-content h2 {
  color: #333;
  margin-bottom: 20px;
}

.details {
  margin-bottom: 20px;
}

.details div {
  margin-bottom: 10px;
}
</style>
