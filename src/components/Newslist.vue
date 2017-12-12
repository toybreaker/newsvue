<template>
  <div class="newslist">

      <ul class="media-list">
        <li class="media" v-for="article in articles">
          <div class="media-left">
            <a v-bind:href="article.url" target="_blank">
              <img class="media-object" v-bind:src="article.urlToImage">
            </a>
          </div>
          <div class="media-body">
            <h4 class="media-heading"><a v-bind:href="article.url" target="_blank">{{article.title}}</a></h4>
            <!-- <h5>{{article.publishedAt | moment("dddd, Do MMMM YYYY") }} - <i>by {{article.author}}</i></h5> -->
            <h5>{{article.publishedAt | moment("from") }} - <i>by {{article.author}}</i></h5>

            <p>{{article.description}}</p>
          </div>
        </li>
      </ul>

      <a class="totop" href="#top">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
            <path d="M12 8l-6 6 1.41 1.41 4.59-4.58 4.59 4.58 1.41-1.41z" fill="white"/>
            <path d="M0 0h24v24h-24z" fill="none"/>
        </svg>
      </a>

    </div>
</template>

<script>
export default {
  name: 'newslist',
  props: ['source'],
  data () {
    return {
      articles: []
    }
  },
  methods: {
    updateSource: function (source) {
      this.$http.get('https://newsapi.org/v1/articles?source=' + source + '&apiKey=ee42dae025f54ea9b22f4882b2c9c149')
       .then(response => {
         this.articles = response.data.articles;
       });
    },
    convertDate: function () {
      this.article.publishedAt = new Date()
      consolelog = d.toUTCString();

    }
  },
  created: function () {
    this.updateSource(this.source);
  },
  watch: {
    source: function (val) {
      this.updateSource(val);
    }
  }
}

</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .newslist {
    background-color: black;
    background-color: #0069cc;
    margin-bottom: 0;
  }

  .media-object {
    width: 100%;
    padding-bottom: 10px;
  }

  .media {
    border-top: 1px solid white;
    padding-top: 20px;
  }

  .media-body {
    display: block;
    width: 100%;
  }

  .media-heading {
    font-size: 30px;
    line-height: .9;
    text-transform: uppercase;
  }

  .media-heading a {
    color: rgba(255, 255, 255, .5);
  }

  .media-heading a:hover {
    text-decoration: none;
    color: rgba(255, 255, 255, .75);
  }

  .container {
    margin-bottom: 50vh;
    /*padding-bottom: 10vh;*/
  }


  .totop {
    user-select: none;
    z-index: 1001;
    display: block;
    position: relative;
    height: 50px;
    width: 100%;
    cursor: pointer;
    text-align: center;
    margin-bottom: 55vh;
    padding-top: 60vh;
  }
  .totop svg {
    border: 2px white solid;
    position: absolute;
    margin-left: -25px;
    margin-top: -60px;
    height: 50px;
  }


  @media screen and (min-width: 480px) {
    .media-body {
      display: table-cell;
      width: auto;
    }
    .media-object {
      width: 300px;
    }
    .media-heading {
      font-size: 40px;
    }
  }
</style>
