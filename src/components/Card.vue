<template>
    <div>
      <b-card
        :title="item.title"
        :img-src="item.url"
        img-alt="Image"
        img-top
        tag="article"
        style="max-width: 20rem"
        class="mb-2"
      >
        <b-card-text>
          Some quick example text to build on the card title and make up the
          bulk of the card's content.
        </b-card-text>

        <b-button href="#" variant="primary">{{item.id}}</b-button>
      </b-card>
    </div>
</template>

<script>
export default {
    props: ["item"]
};
</script>

<style>
.mb-2 {
    min-height: 600px;
}
</style>