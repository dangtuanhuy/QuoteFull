<template>
  <div class="container">
    <!-- //<img src="./assets/logo.png"> -->
    <app-header :quoteCount="quotes.length" :maxQuote="maxQuotes"></app-header>
<app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Click on o Qute to Delete it</div>
      </div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue'
import NewQuote from './components/NewQuote.vue'
import Header from './components/Header.vue'
export default {
  name: 'app',
  data () {
    return {
     quotes: [
       'Just a Quote to see somebody'
     ],
     maxQuotes: 10
    }
  },
  methods:{
    newQuote(quote){
      if(this.quotes.length >= this.maxQuotes){
        return alert('Please delete Quotes first!')
      }
      this.quotes.push(quote);
    },
    deleteQuote(index){
      this.quotes.splice(index,1);
    }
  },
  components:{
    appQuoteGrid: QuoteGrid,
    appNewQuote : NewQuote,
    appHeader: Header
  }
}
</script>

<style lang="scss">

</style>
