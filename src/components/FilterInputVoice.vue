<template>
  <div>
    <div class="relative">
      <div
        class="absolute inset-y-0 left-0 flex items-center pl-1 pointer-events-none"
      >
        <img src="@/assets/search.svg" />
      </div>
      <input
        v-model="filterInput"
        class="w-full py-2 pl-12 pr-3 text-gray-400 bg-black rounded-full shadow appearance-none focus:outline-none"
        type="text"
        placeholder="Search"
      />
      <button
        @click="filterInput = ''"
        v-if="displayClose"
        class="absolute inset-y-0 right-0 flex items-center pl-1 cursor-pointer close-button focus:outline-none"
      >
        <img src="@/assets/search-close.svg" />
      </button>
    </div>
  </div>
</template>

<script>
import { ref, computed, watch } from 'vue'

export default {
  setup(props, { emit }) {
    const filterInput = ref('')
    const displayClose = computed(() => filterInput.value.trim() !== '')

    watch(filterInput, (newValue) => {
      emit('inputChange', newValue)
    })

    return {
      filterInput,
      displayClose
    }
  }
}
</script>

<style scoped>
.close-button {
  width: 36px;
  height: 36px;
}
</style>
