<template>
  <div class="demo-container">
    <ui-top-app-bar
      class="demo-app-bar"
      content-selector=".demo-app-content"
      nav-id="demo-menu"
      >Marvell API Vue</ui-top-app-bar
    >

    <!-- Drawer -->
    <ui-drawer type="dismissible" viewport-height nav-id="demo-menu" open>
      <ui-drawer-header>
        <ui-drawer-title>Choose section:</ui-drawer-title>
        <!-- <ui-drawer-subtitle>Subtitle</ui-drawer-subtitle> -->
      </ui-drawer-header>
      <ui-drawer-content>
        <ui-nav>
          <ui-nav-item href="javascript:void(0)" active>Characters</ui-nav-item>
          <ui-nav-item href="javascript:void(0)">Comics</ui-nav-item>
          <ui-nav-item href="javascript:void(0)">Creators</ui-nav-item>
          <ui-nav-item href="javascript:void(0)">Events</ui-nav-item>
        </ui-nav>
      </ui-drawer-content>
    </ui-drawer>
    <!-- Content -->
    <ui-drawer-app-content class="demo-app-content">
      <!-- App content -->
      <button v-on:click="getMarvellData">getData</button>
      <!-- <p v-for="i in 24" :key="i">Main Content {{ i }}</p> -->
    </ui-drawer-app-content>
  </div>
</template>

<script>
export default {
  name: "NavBar",
  methods: {
    async getMarvellData() {
      await fetch(
        "http://gateway.marvel.com/v1/public/comics?apikey=3fbf47c3e0738e63b5531ab50039e824"
      );
    },
  },
};
</script>

<style scoped>
.mdc-drawer {
  margin-top: 64px;
}
.mdc-drawer__header {
  min-height: 45px;
}
.demo-app-bar {
  z-index: 7;
}

.demo-app-content {
  width: 100%;
  height: 100%;
  overflow: auto;
}
</style>
