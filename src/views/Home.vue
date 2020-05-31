<template>
  <div>
    <HelloWorld msg="The Library" />
    <input v-model="message" placeholder="Search by Description or Name" />
    <p>Filter: {{ message }}</p>

    <div :key="item.name" v-for="item in filteredList">
      <p>Name: {{ item.name }}</p>
      <p>Description: {{ item.description }}</p>
    </div>
    <input type="radio" id="books" value="Books" v-model="picked" />
    <label for="books">Books</label>
    <input type="radio" id="magazines" value="Magazines" v-model="picked" />
    <label for="magazines">Magazines</label>
    <input type="radio" id="newspapers" value="Newspapers" v-model="picked" />
    <label for="newspapers">Newspapers</label>
    <input type="radio" id="others" value="Others" v-model="picked" />
    <label for="others">Others</label>
    <input type="radio" id="all" value="ALL" v-model="picked" />
    <label for="all">ALL</label>
    <p>
      <span>Picked: {{ picked }}</span>
    </p>

    <div :key="item.name" v-for="item in radiobuttonfilteredList">
      <p>Name: {{ item.name }}</p>
      <p>Description: {{ item.description }}</p>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  components: {
    HelloWorld
  },

  data() {
    return {
      message: "",
      picked: "",
      list: [
        {
          code: "0001",
          name: "Hunger Games",
          description:
            "The Hunger Games is an annual event in which one boy and one girl aged 12–18 from each of the twelve districts surrounding the Capitol are selected by lottery to compete in a televised battle royale to the death.",
          category: "Books"
        },
        {
          code: "0002",
          name: "Wild Life",
          description:
            "The most savage animals in Africa, shows how predators hant their pray",
          category: "Magazines"
        },
        {
          code: "0003",
          name: "Harry Potter and the Philosopher's Stone",
          description:
            "Harry Potter, a lonely orphan who discovers that he is actually a wizard and enrolls in the Hogwarts School of Witchcraft and Wizardry.",
          category: "Books"
        },
        {
          code: "0004",
          name: "Amazing Fantasy",
          description:
            "Spider-Man #15th comic book published in 1962, written by Stan Lee",
          category: "Others"
        },
        {
          code: "0005",
          name: "New York Times",
          description: "The latest news of US and the rest fo the world",
          category: "Newspapers"
        }
      ]
    };
  },
  computed: {
    filteredList() {
      return this.list.filter(
        item => item.name === this.message || item.description == this.message
      );
    },
    radiobuttonfilteredList() {
      if (this.picked === "Books") {
        return this.list.filter(item => item.category === this.picked);
      } else if (this.picked == "Magazines") {
        return this.list.filter(item => item.category === this.picked);
      } else if (this.picked === "Newspapers") {
        return this.list.filter(item => item.category === this.picked);
      } else if (this.picked == "Others") {
        return this.list.filter(item => item.category === this.picked);
      } else if (this.picked === "ALL") {
        return this.list;
      } else {
        return null;
      }
    }
  }
};
</script>
