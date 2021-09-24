<template>
  <div class="w-full max-w-screen-sm">
    <h1 class="text-white text-center text-3xl pb-4">IP Addrss Tracker</h1>
    <div class="flex">
      <input
        class="flex-1 py-3 px-2 rounded-tl-md rounded-bl-md focus:outline-none"
        type="text"
        placeholder="Search for any IP Adress or leave empty to get your ip info"
        v-model="input"
        @input="$emit('update:modelValue', $event.target.value)"
      />
      <i
        class="
          cursor-pointer
          bg-black
          text-white
          px-4
          rounded-tr-md rounded-br-md
          flex
          items-center
          fas
          fa-chevron-right
        "
        @click="getIpInfo"
      />
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  props: ["getIpInfo"],
  setup() {
    const input = ref("");
    return {
      input,
    };
  },
};
</script>
