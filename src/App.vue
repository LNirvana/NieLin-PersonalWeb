<template>
  <div id="app">
    <Header></Header>
    <Profile></Profile>
    <info-list></info-list>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Header from "./components/Header.vue";
import InfoList from "./components/InfoList.vue";
import Profile from "./components/Profile.vue";

@Component({
  components: {
    Header,
    Profile,
    InfoList,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss"></style>
