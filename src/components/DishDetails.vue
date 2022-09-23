<template>
  <li>
    <!-- <h2>{{ name }} {{ dishIsFavourite ? "(Favourite)" : "" }}</h2> -->
    <h2>{{ name }} {{ isFavourite ? "(Favourite)" : "" }}</h2>
    <button @click="toggleFavorite" style="background-color: aqua">
      Toggle Favorite
    </button>
    <button @click="toggleDetails" style="background-color: gold">
      {{ displayDetails ? "Hide" : "Show" }} Details
    </button>

    <ul v-if="displayDetails">
      <div style="border: 2px solid greenyellow">
        <img :src="img" width="150" height="150" />
        <li>
          <strong>Description</strong>
          {{ description }}
        </li>
        <li>
          <strong>Price</strong>
          {{ price }}
        </li>
      </div>
    </ul>
  </li>
</template>

<script>
export default {
  emits: ["toggleFavouriteStatus"],
  //   props: ["name", "description", "price", "isFavourite"],

  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    img: {
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    price: {
      type: String,
      required: true,
    },
    isFavourite: {
      type: Boolean,
      required: false,
    },
  },
  data() {
    return {
      // dishIsFavourite: this.isFavourite,
      displayDetails: false,
    };
  },
  methods: {
    toggleFavorite() {
      // if (this.dishIsFavourite) {
      //   this.dishIsFavourite = false;
      // } else {
      //   this.dishIsFavourite = true;
      // }
      // this.dishIsFavourite = !this.dishIsFavourite;
      //or
      this.$emit("toggleFavouriteStatus", this.id);
    },
    toggleDetails() {
      this.displayDetails = !this.displayDetails;
    },
  },
};
</script>

<style>
li {
  list-style-type: none;
}
</style>
