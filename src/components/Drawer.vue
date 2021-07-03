<template>
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
</template>

<script>
export default {
  name: "Drawer",
};
</script>

<style scoped>
.mdc-drawer {
  margin-top: 64px;
  height: calc(100vh - 64px);
}
.mdc-drawer__header {
  min-height: 45px;
}
</style>
