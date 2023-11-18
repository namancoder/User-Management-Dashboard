<template>
  <div class="dialog-content">
    <button class="close-dialog" @click="closeDialog">×</button>
    <h2>User Details</h2>
    <div class="details">
      <p><strong>Username:</strong> {{ selectedUser?.username }}</p>
      <p><strong>Email:</strong> {{ selectedUser?.email }}</p>
      <p><strong>Phone:</strong> {{ selectedUser?.phone }}</p>
      <p>
        <strong>Creation Date:</strong>
        {{ selectedUser?.["creation-date"] }}
      </p>
      <p><strong>ID:</strong> {{ selectedUser?.id }}</p>
    </div>
    <button
      class="mt-3 text-xs rounded-md bg-blue-500 hover:bg-red-700 p-1.5 text-white font-bold"
      @click="generateReport"
    >
      Generate Report
    </button>
  </div>
</template>

<script>
export default {
  props: {
    selectedUser: Object,
    closeDialog: {
      type: Function,
      required: true,
    },
  },
  methods: {
    generateReport() {
      alert("Report generated");
    },
  },
};
</script>

<style scoped>
.close-dialog {
  position: absolute;
  top: 10px;
  right: 10px;
  font-size: 26px;
  cursor: pointer;
  background: none;
  border: none;
  outline: none;
  color: #333;
}
.dialog-content h2 {
  color: #333;
  margin-bottom: 20px;
  font-size: 25px !important;
  font-weight: bold;
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

.details {
  margin-bottom: 20px;
}

.details div {
  margin-bottom: 10px;
}
</style>
