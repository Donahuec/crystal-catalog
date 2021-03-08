<template>
  <div class="home">
    <br />
    <br />
    <div class="container">
      <div class="row">
        <div class="col l2">
          <div class="card">
            <div class="card-title">
              <h4>Filter</h4>
            </div>
            <div class="card-content">
              <p>Filters</p>
              <p>Filters</p>
              <p>Filters</p>
              <p>Filters</p>
              <p>Filters</p>
              <p>Filters</p>
              <p>Filters</p>
              <p>Filters</p>
              <p>Filters</p>
              <p>Filters</p>
            </div>
          </div>
        </div>
        <div class="col l10">
          <List msg="Crystal Catalog" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import List from "@/components/List.vue";

export default {
  name: "Home",
  components: {
    List,
  },
};
</script>
