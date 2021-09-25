<template>
  <div
    class="relative"
    :class="{ 'bg-black': darkMode, 'bg-white': !darkMode }"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6">
      <div
        class="
          flex
          justify-between
          items-center
          py-3
          md:justify-start
          md:space-x-10
        "
      >
        <div class="flex justify-start lg:w-0 lg:flex-1">
          <a href="#">
            <span class="sr-only">Ip Tracker</span>
            <svg
              version="1.1"
              id="Capa_1"
              xmlns="http://www.w3.org/2000/svg"
              xmlns:xlink="http://www.w3.org/1999/xlink"
              x="0px"
              y="0px"
              viewBox="0 0 20.234 20.234"
              style="enable-background: new 0 0 20.234 20.234"
              xml:space="preserve"
              class="h-8 w-auto sm:h-10"
            >
              <g>
                <path
                  :style="[!darkMode ? { fill: '#030104' } : { fill: '#fff' }]"
                  d="M6.776,4.72h1.549v6.827H6.776V4.72z M11.751,4.669c-0.942,0-1.61,0.061-2.087,0.143v6.735h1.53
		V9.106c0.143,0.02,0.324,0.031,0.527,0.031c0.911,0,1.691-0.224,2.218-0.721c0.405-0.386,0.628-0.952,0.628-1.621
		c0-0.668-0.295-1.234-0.729-1.579C13.382,4.851,12.702,4.669,11.751,4.669z M11.709,7.95c-0.222,0-0.385-0.01-0.516-0.041V5.895
		c0.111-0.03,0.324-0.061,0.639-0.061c0.769,0,1.205,0.375,1.205,1.002C13.037,7.535,12.53,7.95,11.709,7.95z M10.117,0
		C5.523,0,1.8,3.723,1.8,8.316s8.317,11.918,8.317,11.918s8.317-7.324,8.317-11.917S14.711,0,10.117,0z M10.138,13.373
		c-3.05,0-5.522-2.473-5.522-5.524c0-3.05,2.473-5.522,5.522-5.522c3.051,0,5.522,2.473,5.522,5.522
		C15.66,10.899,13.188,13.373,10.138,13.373z"
                />
              </g>
            </svg>
          </a>
        </div>
        <div class="-mr-2 -my-2 md:hidden">
          <button
            type="button"
            class="
              bg-white
              rounded-md
              p-2
              inline-flex
              items-center
              justify-center
              text-gray-400
              hover:text-gray-500
              hover:bg-gray-100
              focus:outline-none
              focus:ring-2 focus:ring-inset focus:ring-indigo-500
            "
            aria-expanded="false"
          >
            <span class="sr-only">Open menu</span>
            <!-- Heroicon name: outline/menu -->
            <svg
              class="h-6 w-6"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              aria-hidden="true"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16"
              />
            </svg>
          </button>
        </div>
        <div class="hidden md:flex items-center justify-end md:flex-1 lg:w-0">
          <a
            href="#"
            class="
              ml-8
              whitespace-nowrap
              inline-flex
              items-center
              justify-center
              px-4
              py-2
              border border-transparent
              rounded-md
              shadow-sm
              text-base
              font-medium
            "
            :class="{
              'bg-black text-white': !darkMode,
              'bg-white text-black': darkMode,
            }"
            @click="toggleDarkMode"
          >
            {{ darkModeButtonText }}
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  props: ["darkMode", "toggleDarkMode", "darkModeButtonText"],
};
</script>
