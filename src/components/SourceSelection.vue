<template>
  <div class="sourceselection">
    <div>
      <div class="jumbotron">

        <h2>
          {{source.name}}
        </h2>

        <div v-if="source">
          <h6 class="source--desc">{{source.description}}</h6>
          <a v-bind:href="source.url" class="btn btn-primary" target="_blank">Go To {{source.name}} Website</a>
        </div>

        <h3>Select News Source</h3>

        <select class="form-control" v-on:change="sourceChanged">
          <option value="">Please select news source ...</option>
          <option v-for="source in sources" v-bind:value="source.id">{{source.name}}</option>
        </select>

        <h1 class="huge">Branded News Browser</h1>

      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'sourceselection',
  data () {
    return {
      sources: [],
      source: ''
    }
  },
  methods: {
    sourceChanged: function(e) {
     for (var i=0; i<this.sources.length; i++) {
       if (this.sources[i].id == e.target.value) {
         this.source = this.sources[i];
       }
     }
     this.$emit('sourceChanged', e.target.value);
    }
  },
  created: function () {
    this.$http.get('https://newsapi.org/v1/sources?language=en')
      .then(response => {
        this.sources = response.data.sources;
      });
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.sourceselection {
  background-color: #0069cc;
  /*padding-bottom: 1rem;*/
}
.jumbotron {
  background-color: transparent;
  padding-bottom: 0;
}
.jumbotron > * {
  font-weight: 200;
}
.source--desc {
  font-size: 24px;
  color: rgba(255, 255, 255, 0.5);
  font-weight: 200;
}
.btn-primary {
  background-color: transparent;
  border-color: white;
}
.btn-primary:hover {
  background-color: rgba(255, 255, 255, 0.15);
}
.huge {
  font-size: 18vw;
  font-weight: 100;
  line-height: .75;
  padding-bottom: 1rem;
  text-transform: uppercase;
}
@media only screen and (min-width: 601px) {
  .huge {
    font-size: 14vw;
  }
}
@media only screen and (min-width: 801px) {
  .huge {
    font-size: 9vw;
  }
}
</style>
