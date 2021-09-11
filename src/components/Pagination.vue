<template>
  <div class="overflow-auto">
    <b-table
      id="my-table"
      :items="items"
      :per-page="perPage"
      :current-page="currentPage"
      small
    ></b-table>

    <p class="mt-3">Current Page: {{ currentPage }}</p>

    <b-pagination
      v-model="currentPage"
      :total-rows="rows"
      :per-page="perPage"
      aria-controls="my-table"
    ></b-pagination>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      perPage: 10,
      currentPage: 1,
      items: [],
    };
  },
  computed: {
    rows() {
      return this.items.length;
    },
  },
  mounted() {
    axios.get("https://jsonplaceholder.typicode.com/todos")
      .then(res => {
        res.data.forEach(data => {
            this.items.push({id: data.id, title: data.title, completed: data.completed})
        });
      })
      .catch( error => console.log(error))
  },
};
</script>