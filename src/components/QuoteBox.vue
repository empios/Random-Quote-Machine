<template>
  <div id="quote-box" class="container has-text-centered">
    <div class="column is-vcentered">
      <div class="card">
        <div class="card-content">
          <div class="column">
            <h1 id="text">"{{title}}"</h1>
            <hr>
            <h6 id="author">{{author}}</h6>
          </div>
          <div class="columns">
            <div class="column">
              <a v-bind:href="this.url" id="tweet-quote" class="button is-primary">Tweet!</a>
            </div>
            <div class="column">
              <b-button type="is-danger" id="new-quote" @click="this.handleClick">Get Quote</b-button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'QuoteBox',
  async created(){
    await this.$http.get("https://gist.githubusercontent.com/camperbot/5a022b72e96c4c9585c32bf6a75f62d9/raw/e3c6895ce42069f0ee7e991229064f167fe8ccdc/quotes.json")
    .then((response) => {
      let quote = response.data.quotes[Math.floor((Math.random() * 100) + 1)];
      this.author = quote.author;
      this.title = quote.quote;
      })
  },
  methods: {
    async handleClick(){
    await this.$http.get("https://gist.githubusercontent.com/camperbot/5a022b72e96c4c9585c32bf6a75f62d9/raw/e3c6895ce42069f0ee7e991229064f167fe8ccdc/quotes.json")
    .then((response) => {
      let quote = response.data.quotes[Math.floor((Math.random() * 100) + 1)];
      this.author = quote.author;
      this.title = quote.quote;
      })
    },
  },
  watch: {
    title: function () {
      this.url = 'https://twitter.com/intent/tweet?hashtags=quotes&related=freecodecamp&text=' + encodeURIComponent('"' + this.title + '" ' + this.author);
      }
  },
  data() {
    return{
        author: "",
        title: "",
        url: ""
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
hr{
        height: 2px;
        background-color: aquamarine;
        border: none;
}
</style>
