<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div v-html="heroContent"></div>
  </div>
</template>

<script>
import { DialogueWiseService } from 'dialoguewise';
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: function () {
    return {
      heroContent: '' 
    }
  },
  mounted: async function () {
    let request = {
    slug: 'hero-section',
    apiKey: 'b1266377591c4f2a9494c3abdd2cac5381D6Z825D26CEBAE8B6rn',
    emailHash: '/kgmM46s1xC56BOFWRZp4j+0bdU19URpXdNT9liAX50=',
  };

  let dialogueWiseService = new DialogueWiseService();
  let res = await dialogueWiseService.getDialogue(request);
  this.heroContent = res['dialogue'][0]['hero-content'];
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
