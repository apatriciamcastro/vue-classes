<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <h1>Filters & Mixins</h1>
        <!-- Exercise 1) -->
        <!-- Build a local Filter which reverses the Text it is applied on -->
        <h4>Local Filter</h4>
        <p>{{ text | reverseFilter }}</p>
        <p>{{ name | reverseFilter }}</p>
        <hr />
        <!-- Exercise 2 -->
        <!-- Build a global Filter which counts the length of a word and it appends it -->
        <!-- Like this: "Test" => Gets Filtered to => "Test (4)" -->
        <h4>Global Filter</h4>
        <p>{{ text | add-length }}</p>
        <p>{{ name | add-length }}</p>
        <hr />
        <!-- Exercise 3 -->
        <!-- Do the same as in Exercise 1, now with Computed Properties -->
        <h4>Computed</h4>
        <p>{{ reverseText }}</p>
        <hr />
        <!-- Exercise 4 -->
        <!-- Share the Computed Property rebuilding Exercise 2 via a Mixin -->
        <h4>Mixin</h4>
        <p>{{ lengthAware }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import { lengthMixin } from "./lengthMixin";

export default {
  mixins: [lengthMixin],
  data: function() {
    return {
      text: "Test",
      name: "Patricia"
    };
  },
  filters: {
    reverseFilter(value) {
      return value
        .split("")
        .reverse()
        .join("");
    }
  },
  computed: {
    reverseText() {
      return this.text
        .split("")
        .reverse()
        .join("");
    }
  }
};
</script>

<style>
</style>
