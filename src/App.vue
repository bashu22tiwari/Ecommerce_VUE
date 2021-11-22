<template>
  <div>
    <NavBar />
    <div>
      <button
        v-for="entry in languages"
        :key="entry.title"
        @click="changeLocale(entry.language)"
      >
        <flag :iso="entry.flag" v-bind:squared="false" /> {{ entry.title }}
      </button>
    </div>
    <router-view />
    <Footer />
  </div>
</template>

<script>
import NavBar from "./layouts/NavBar.vue";
import Footer from "./layouts/Footer.vue";
import i18n from "@/plugins/i18n";

export default {
  name: "App",
  components: { NavBar, Footer },
  data() {
    return {
      languages: [
        { flag: "us", language: "en", title: "English" },
        { flag: "in", language: "hi", title: "Hindi" },
      ],
    };
  },
  methods: {
    changeLocale(locale) {
      i18n.setLocale(locale);
    },
  },
};
</script>
<style scoped>
button {
  padding: 5px;
  border: 1px solid green;
  font-size: 10px;
  margin: 10px;
}
</style>