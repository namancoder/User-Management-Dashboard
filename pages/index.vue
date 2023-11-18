<template>
  <div>
    <div class="relative z-10">
      <div class="fixed top-0 left-0 right-0 bg-gray-800 text-white p-4">
        <button
          @click="activeTab = 1"
          :class="{ 'bg-gray-600': activeTab === 1 }"
          class="px-4 py-2 mr-2 rounded cursor-pointer"
        >
          User Details
        </button>
        <button
          @click="activeTab = 2"
          :class="{ 'bg-gray-600': activeTab === 2 }"
          class="px-4 py-2 rounded cursor-pointer"
        >
          Account Creation
        </button>
      </div>
    </div>

    <div class="mt-16">
      <div v-if="activeTab === 1">
        <Tab1 />
      </div>
      <div v-else-if="activeTab === 2">
        <Tab2 />
      </div>
    </div>
  </div>
</template>

<script>
import Tab1 from "~/components/Tab1.vue";
import Tab2 from "~/components/Tab2.vue";

export default {
  setup() {
    useHead({
      title: "Dashboard",
    });
  },
  components: {
    Tab1,
    Tab2,
  },
  data() {
    return {
      activeTab: 1,
    };
  },
};
</script>
