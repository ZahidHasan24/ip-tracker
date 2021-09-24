<template>
  <div class="flex flex-col h-screen max-h-screen">
    <!-- Search Component -->
    <div class="flex justify-center relative px-4 pt-8 pb-32 bg-hero-pattern bg-cover">
      <!-- Search Input -->
      <div class="w-full max-w-screen-sm">
        <h1 class="text-white text-center text-3xl pb-4">IP Addrss Tracker</h1>
        <div class="flex">
          <input
            class="flex-1 py-3 px-2 rounded-tl-md rounded-bl-md focus:outline-none"
            type="text"
            placeholder="Search for any IP Adress or leave empty to get your ip info"
          />
          <i class="cursor-pointer bg-black text-white px-4 rounded-tr-md rounded-br-md flex items-center fas fa-chevron-right" />
        </div>
      </div>
      <!-- IPInfo -->
      <IPInfo />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import IPInfo from '@/components/IPInfo.vue'

export default {
  name: 'Home',
  components: {
    IPInfo,
  }
}
</script>
