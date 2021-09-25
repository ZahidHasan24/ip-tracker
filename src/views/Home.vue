<template>
  <!-- Header -->
  <Header
    :darkMode="darkMode"
    :toggleDarkMode="toggleDarkMode"
    :darkModeButtonText="darkModeButtonText"
  />

  <div class="flex flex-col h-screen max-h-screen">
    <!-- Search Component -->
    <div
      class="
        flex
        justify-center
        relative
        px-4
        pt-8
        pb-32
        bg-hero-pattern bg-cover
        z-20
      "
    >
      <!-- Search Input -->
      <Search v-model="queryIp" :getIpInfo="getIpInfo" :darkMode="darkMode" />
      <!-- IPInfo -->
      <IPInfo v-if="ipInfo" :ipInfo="ipInfo" :darkMode="darkMode" />
    </div>
    <!-- Map -->
    <div id="mapid" class="h-full z-10"></div>
  </div>
</template>

<script>
// @ is an alias to /src
import leaflet from "leaflet";
import { onMounted, ref, computed } from "vue";
import IPInfo from "@/components/IPInfo.vue";
import Search from "@/components/Search.vue";
import Header from "@/components/Header.vue";
import useDarkMode from "@/hooks/useDarkMode";

export default {
  name: "Home",
  components: {
    IPInfo,
    Search,
    Header,
  },
  setup() {
    let mymap;
    const { darkMode, toggleDarkMode } = useDarkMode();
    const map_token = process.env.VUE_APP_MAPBOX_TOKEN;
    const geo_token = process.env.VUE_APP_GEO_API_TOKEN;
    const queryIp = ref("");
    const ipInfo = ref(null);

    const darkModeButtonText = computed(() => {
      return darkMode.value ? "Light" : "Dark";
    });

    onMounted(async () => {
      mymap = leaflet.map("mapid").setView([51.505, -0.99], 13);

      leaflet
        .tileLayer(
          `https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token=${map_token}`,
          {
            attribution:
              'Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
            maxZoom: 18,
            id: "mapbox/streets-v11",
            tileSize: 512,
            zoomOffset: -1,
            accessToken: map_token,
          }
        )
        .addTo(mymap);
    });

    const getIpInfo = async () => {
      try {
        const res = await fetch(
          `https://geo.ipify.org/api/v1?apiKey=${geo_token}&ipAddress=${queryIp.value}`
        );
        const data = await res.json();
        ipInfo.value = {
          address: data.ip,
          state: data.location.region,
          timezone: data.location.timezone,
          isp: data.isp,
          lat: data.location.lat,
          lng: data.location.lng,
        };
        leaflet.marker([ipInfo.value.lat, ipInfo.value.lng]).addTo(mymap);
        mymap.setView([ipInfo.value.lat, ipInfo.value.lng], 13);
      } catch (err) {
        console.log({ err });
      }
    };
    return {
      queryIp,
      ipInfo,
      getIpInfo,
      toggleDarkMode,
      darkModeButtonText,
      darkMode,
    };
  },
};
</script>
