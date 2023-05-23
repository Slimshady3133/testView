<template>
  <div class="app">
    <NavBar />
    <Sidebar />
    <MainPage />
  </div>
</template>

<script>
import MainPage from './components/MainPage.vue';
import NavBar from './components/NavBar.vue';
import Sidebar from './components/SideBar.vue';

export default {
  components: {
    MainPage,
    NavBar,
    Sidebar,
  },
};
</script>

<style scoped>
.app {
  position: relative;
  width: 1920px;
  height: 1200px;
  background: #f5f7fb;
  border-radius: 16px;
}
</style>
