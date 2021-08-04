<template>
  <ui-drawer-app-content class="demo-app-content">
    <ui-pagination
      :model-value="page"
      @update:modelValue="
        changePagination($event);
        getData(($event - 1) * 20);
      "
      :total="total"
      show-total
      position="right"
      pageSize="20"
    ></ui-pagination>
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
import { onMounted, onUpdated } from "@vue/runtime-core";
import CryptoJS from "crypto-js";
export default {
  name: "MainContent",
  data() {
    return {
      characters: [],
      page: 1,
      total: 0,
    };
  },
  methods: {
    getData: async function getMarvellData(offset = 0) {
      const timeStamp = new Date().getTime();
      const publicKey = "3fbf47c3e0738e63b5531ab50039e824";
      const privateKey = "fef27312db649a04f7968f1b5a5277b7d7abff83";
      const hash = CryptoJS.MD5(timeStamp + privateKey + publicKey);
      const response = await fetch(
        `http://gateway.marvel.com/v1/public/characters?offset=${offset}&ts=${timeStamp}&apikey=${publicKey}&hash=${hash}`
      ).then((response) => response.json());
      this.characters = [...response.data.results];
      this.total = response.data.total;
    },
    changePagination: function (pageNumber) {
      this.page = pageNumber;
    },
  },

  mounted() {
    // console.log("mounted!");
    // console.log(this.page);
    this.getData();
  },
  updated() {
    // console.log(this.page);
    // console.log(this.total);
    // console.log("213123");
  },
  setup() {
    onMounted(() => {
      // console.log(page);
      // console.log(total);
    });
    onUpdated(() => {
      // console.log(page);
      // console.log(total);
    });
  },
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
