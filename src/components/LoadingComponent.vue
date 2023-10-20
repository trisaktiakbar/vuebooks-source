<template>
  <div v-if="!data" class="row">
    <div class="col text-center my-5">
      <div class="spinner-border text-success" role="status">
        <span class="visually-hidden">Loading...</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["data"],
  name: "LoadingComponent",
};
</script>

<style></style>
