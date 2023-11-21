<template src="./HelloWorld.html"></template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      urlList: ["https://italiancoders.it",
        "https://www.arcoiris.tv",
        "https://www.twitter.com",],
      actualLista: 0,
      rawHtml: "Test",
      h: window.innerHeight
    }
  },
  computed: {
    compiledHtml: function () {
      return this.rawHtml;
    }
  },
  created() {
    this.rawHtml = "<h1>loading ... </h1>"
    this.roundPage()
    setInterval(() => this.roundPage(), 30000)
  },
  methods: {
    roundPage() {
      this.loadPage()
      this.actualLista++
      if (this.actualLista >= this.urlList.length) {
        this.actualLista = 0;
      }
    },
    loadPage() {
      const urlbase = this.urlList[this.actualLista]
      this.rawHtml = " <iframe width=\"100%\" height=\"" + this.h + "px\" class=\"embed-responsive-item\" src=\"" + urlbase + "\" allowfullscreen></iframe>"
      // this.rawHtml = " <iframe width=\"100%\" height=\"800px\" class=\"embed-responsive-item\" src=\""+url+"\" allowfullscreen></iframe>"
      console.log("Loading ... " + urlbase)
    }
  }
}
</script>
<style>
@import '../assets/stile.css';
</style>
