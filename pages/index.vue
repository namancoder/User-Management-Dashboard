<template>
  <div>
    <div class="bg-gray-800 text-white p-4">
      <div class="flex">
        <button
          @click="activeTab = 1"
          :class="{ 'bg-gray-600': activeTab === 1 }"
          class="px-4 py-2 mr-2 rounded cursor-pointer"
        >
          Tab 1
        </button>
        <button
          @click="activeTab = 2"
          :class="{ 'bg-gray-600': activeTab === 2 }"
          class="px-4 py-2 rounded cursor-pointer"
        >
          Tab 2
        </button>
      </div>
    </div>
    <div v-if="activeTab === 1">
      <Tab1 />
    </div>
    <div v-else-if="activeTab === 2">
      <Tab2 />
    </div>
  </div>
</template>

<script>
import Tab1 from '~/components/Tab1.vue'
import Tab2 from '~/components/Tab2.vue'

export default {
  components: {
    Tab1,
    Tab2,
  },
  data() {
    return {
      activeTab: 1,
    }
  },
}
</script>
