<template>
  <div class="w-full max-w-screen-sm">
    <h1
      class="text-center text-3xl pb-4"
      :class="{
        'text-white': !darkMode,
        'text-black': darkMode,
      }"
    >
      IP Addrss Tracker
    </h1>
    <div class="flex">
      <input
        class="flex-1 py-3 px-2 rounded-tl-md rounded-bl-md focus:outline-none"
        :class="{
          'text-white bg-black placeholder-white': darkMode,
          'text-black bg-white placeholder-gray': !darkMode,
        }"
        type="text"
        placeholder="Search for any IP Adress or leave empty to get your ip info"
        v-model="input"
        @input="$emit('update:modelValue', $event.target.value)"
      />
      <i
        class="
          cursor-pointer
          px-4
          rounded-tr-md rounded-br-md
          flex
          items-center
          fas
          fa-chevron-right
        "
        :class="{
          'text-white bg-black': !darkMode,
          'text-black bg-white': darkMode,
        }"
        @click="getIpInfo"
      />
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
export default {
  props: ["getIpInfo", "darkMode"],
  setup(props, context) {
    const input = ref("");
    onMounted(async () => {
      try {
        const res = await fetch("https://api.ipify.org?format=json");
        const { ip } = await res.json();
        input.value = ip;
        context.emit("update:modelValue", ip);
        props.getIpInfo();
      } catch (err) {
        console.log({ err });
      }
    });
    return {
      input,
    };
  },
};
</script>
