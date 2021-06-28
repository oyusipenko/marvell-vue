<template>
  <ui-drawer-app-content class="demo-app-content">
    <button @click="getMarvellData">getData</button>

    <ui-grid class="demo-grid">
      <ui-grid-cell
        v-for="character in characters"
        v-bind:key="character"
        class="demo-cell"
        :columns="{ default: 2, desktop: 3, tablet: 4, phone: 4 }"
      >
        <ui-card class="demo-card demo-card--photo">
          <ui-card-content class="demo-card__primary-action">
            <ui-card-media
              square
              class="demo-card__media"
              v-bind:style="{
                backgroundImage:
                  `url(` +
                  character.thumbnail.path +
                  `/portrait_uncanny.` +
                  character.thumbnail.extension +
                  `)`,
              }"
            >
            </ui-card-media>
            <ui-card-text> {{ character.name }}</ui-card-text>
            <ui-card-text>
              {{
                character.description.length > 1
                  ? character.description
                  : "No description provided by Marvel API..."
              }}
            </ui-card-text>
          </ui-card-content>
          <ui-card-actions>
            <ui-button class="demo-card-action"> Comics </ui-button>
            <ui-button class="demo-card-action"> Events </ui-button>

            <ui-button class="demo-card-action"> Series </ui-button>
            <ui-button class="demo-card-action"> Stories </ui-button>
          </ui-card-actions>
        </ui-card>
      </ui-grid-cell>
    </ui-grid>
  </ui-drawer-app-content>
</template>

<script>
export default {
  name: "MainContent",
  setup() {
    async function getMarvellData() {
      const response = await fetch(
        "http://gateway.marvel.com/v1/public/characters?apikey=3fbf47c3e0738e63b5531ab50039e824"
      ).then((response) => response.json());
      console.log(response.data.results);
      console.log(response.data);
      this.characters = [...this.characters, ...response.data.results];
    }
    // mounted
    onMounted(() => {
      console.log("Component is mounted!");
      getMarvellData();
    });
  },
  data() {
    return {
      characters: [],
    };
  },
  methods: {},
};
</script>

<style scoped>
.demo-app-content {
  width: 100%;
}
.mdc-card {
  height: 100%;
  justify-content: space-between;
}
.mdc-card__actions {
  flex-wrap: wrap;
  justify-content: space-around;
  text-align: center;
}
.mdc-button.mdc-ripple-upgraded {
  margin-right: 0;
  width: 80px;
}
</style>
