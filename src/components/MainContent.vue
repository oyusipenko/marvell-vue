<template>
  <ui-drawer-app-content class="demo-app-content">
    <button @click="getMarvellData">getData</button>
    <!-- <p v-for="i in 24" :key="i">Main Content {{ i }}</p> -->
    <ui-grid class="demo-grid">
      <ui-grid-cell
        v-for="character in characters"
        v-bind:key="character"
        class="demo-cell"
        columns="4"
      >
        <ui-card class="demo-card demo-card--photo">
          <ui-card-content class="demo-card__primary-action">
            <img
              v-bind:src="
                character.thumbnail.path +
                `/portrait_uncanny.` +
                character.thumbnail.extension
              "
            />
            <ui-card-media square class="demo-card__media">
              <ui-card-media-content
                class="demo-card__media-content--with-title"
              >
                <div :class="[$tt('subtitle2'), 'demo-card__media-title']">
                  {{ character.name }}
                </div>
              </ui-card-media-content>
            </ui-card-media>
          </ui-card-content>
          <ui-card-actions>
            <ui-card-icons>
              <ui-icon-button :toggle="icon1"></ui-icon-button>
              <ui-icon-button :toggle="icon2"></ui-icon-button>
              <ui-icon-button icon="share"></ui-icon-button>
            </ui-card-icons>
          </ui-card-actions>
        </ui-card>
      </ui-grid-cell>
    </ui-grid>
  </ui-drawer-app-content>
</template>

<script>
export default {
  name: "MainContent",
  data() {
    return {
      characters: [],
    };
  },
  methods: {
    async getMarvellData() {
      const response = await fetch(
        "http://gateway.marvel.com/v1/public/characters?apikey=3fbf47c3e0738e63b5531ab50039e824"
      ).then((response) => response.json());
      console.log(response.data.results);
      console.log(response.data);
      this.characters = [...this.characters, ...response.data.results];
      console.log(this.characters);
    },
  },
};
</script>

<style scoped>
.demo-app-content {
  width: 100%;
}
</style>
