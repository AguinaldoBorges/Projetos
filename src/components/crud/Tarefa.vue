<template>
  <div class="row d-flex justify-content-center">
  <div class="col-sm-8">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">{{title}}</h5>
        <p class="card-text">{{text}}</p>
        <p class="card-text">{{stats}}</p>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  props: ["title", "text", "stats", "xupdate", "xdelete", "xid"],
  methods: {}

};
</script>

<style>
</style>