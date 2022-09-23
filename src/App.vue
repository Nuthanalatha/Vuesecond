<template>
  <h1 style="background-color: wheat">Little Indian Restro</h1>
  <ul>
    <dish-details
      v-for="dish in dishes"
      :key="dish.id"
      :id="dish.id"
      :name="dish.name"
      :img="dish.img"
      :description="dish.description"
      :price="dish.price"
      :isFavourite="dish.isFavourite"
      @toggleFavouriteStatus="toggleFavouriteStatus"
    />
  </ul>
</template>

<script>
import DishDetails from "./components/DishDetails.vue";
export default {
  name: "App",
  components: {
    DishDetails,
  },

  data() {
    return {
      dishes: [
        {
          id: "nuthana",
          name: "Veg Pulao",
          img: "https://media.istockphoto.com/photos/veg-pulao-cooked-with-masala-spices-served-over-a-rustic-wooden-picture-id1292633375?b=1&k=20&m=1292633375&s=170667a&w=0&h=TF9JkRR5o2g_LcaBr-DWR8Y55cMluHzGiKbS9wJ87S4=",
          description:
            "Vegetable pulao is very simple recipe and can be made in a jiffy It is cooked with mild spices and tastes well with any north indian gravy.",
          price: "350",
          isFavourite: true,
        },
        {
          id: "viabhav",
          name: "Chole Bhature",
          img: "https://media.istockphoto.com/photos/chole-or-chickpea-curry-and-poori-indian-food-picture-id1406488780?b=1&k=20&m=1406488780&s=170667a&w=0&h=U1Ad-PDDGvuHE15h2INZ-Tn3dM4Zs9z_G48h5WRbr2M=",
          description:
            "It is a combination of chana masala and bhatura/puri, a deep-fried bread made from maida.",
          price: "150",
          isFavourite: false,
        },
        {
          id: "akshatha",
          name: "Masala Dosa",
          img: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTkL4XpQsFtP5MgOD26RZSQitNIGfRUQW9Auw&usqp=CAU",
          description:
            "Masala dosa are crisp rice and lentil crepes stuffed with spiced and savory potato filling. ",
          price: "300",
          isFavourite: false,
        },
      ],
    };
  },
  methods: {
    //to get selected dishDetails from child component
    toggleFavouriteStatus(dishID) {
      // console.log("dishID in parent", dishID);
      let identifiedDish = this.dishes.find((dish) => dish.id === dishID);
      // console.log("identifiedDish", identifiedDish);
      identifiedDish.isFavourite = !identifiedDish.isFavourite;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
