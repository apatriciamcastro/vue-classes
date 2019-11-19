<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxCount="maxQuotes"></app-header>
    <app-add-quote @quoteAdded="newQuote"></app-add-quote>
    <app-quote-grid :quotes="quotes" @deletedQuote="quoteDelete"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a Quote to Delete it!</div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Shared/Header.vue";
import QuoteGrid from "./components/Quotes/QuoteGrid.vue";
import NewQuote from "./components/Quotes/NewQuote.vue";

export default {
  data: function() {
    return {
      quotes: ["A test quote"],
      maxQuotes: 10
    };
  },
  components: {
    "app-quote-grid": QuoteGrid,
    "app-add-quote": NewQuote,
    "app-header": Header
  },
  methods: {
    newQuote(quote) {
      if (this.quotes.length >= this.maxQuotes) {
        return alert("The max value of quotes is 10. Please delete one first!");
      } else {
        this.quotes.push(quote);
      }
    },
    quoteDelete(index) {
      this.quotes.splice(index, 1);
    }
  }
};
</script>

<style>
</style>
