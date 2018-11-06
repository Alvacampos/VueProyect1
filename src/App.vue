<template>
    <div class="container">
      <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
      <app-new @quoteAdded="newQuote"></app-new>
      <app-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-grid>
      <div class="row">
        <div class="col-sm-12 text-center">
          <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
        </div>
      </div>
    </div>
</template>

<script>
  import QuoteGrid from './components/QuoteGrid.vue';
  import NewQuote from './components/NewQuote.vue';
  import Header from './/components/Header.vue';
  export default {
    data() {
      return {
        quotes: ['Lorem ipsum dolor sit amet, consectetur adipisicing elit.'],
        maxQuotes: 10
      };      
    },
    methods: {
      newQuote(quote) {
        if(this.quotes.length >= this.maxQuotes){
          return alert('Please delete Quotes first');
        }  
        this.quotes.push(quote);       
      },
      deleteQuote(index) {
        this.quotes.splice(index, 1);
      }
    },
    components: {
      'app-grid': QuoteGrid,
      'app-new': NewQuote,
      'app-header': Header
    }
  }
</script>

<style>
</style>
