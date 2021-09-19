<template>
  <div>
    <b-container class="d-flex flex-wrap justify-content-center">
      <Card
        class="ms-5 mb-5"
        v-for="item in displayData"
        :key="item.id"
        :item="item"
      />
    </b-container>

    <b-container>
      <p class="mt-3">Current Page: {{ currentPage }}</p>
      <b-pagination
        v-model="currentPage"
        :total-rows="rows"
        :per-page="perPage"
        @input="paginate(currentPage)"
      ></b-pagination>
    </b-container>
  </div>
</template>

<script>
import axios from "axios";
import Card from "../components/Card.vue";
export default {
  data() {
    return {
      allData: [],
      displayData: [],
      currentPage: 1,
      rows: 1,
      perPage: 2,
    };
  },
  components: {
    Card,
  },
  mounted() {
    axios.get("img.json").then((res) => {
      res.data.forEach((data) => {
        this.allData.push({ id: data.id, title: data.title, url: data.url });
        this.displayData = res.data.slice(0, this.perPage);
        this.rows = this.allData.length;
      });
    });
  },
  methods: {
    paginate(currentPage) {
      const start = (currentPage - 1) * this.perPage;
      this.displayData = this.allData.slice(start, start + this.perPage);
    },
  },
};
</script>

<style></style>
