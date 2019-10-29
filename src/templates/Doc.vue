<template>
  <Layout>
    <h1>
      {{ $page.doc.title }}
    </h1>
     <div class="markdown" v-html="$page.doc.content" />
  </Layout>
</template>

<page-query>
query Doc ($path: String!) {
  doc: doc (path: $path) {
    title
    path
    date (format: "D. MMMM YYYY")
    timeToRead
    content
  }
}
</page-query>

<script>
export default {
  metaInfo() {
    return {
      title: this.$page.doc.title,
      meta: [
        { key: 'description', name: 'description', content: this.$page.doc.description }
      ]
    }
  },
  updated() {
     var headers = document.querySelectorAll(".main h2");
    headers.forEach(l => {
      let id = decodeURIComponent(l.id);

      l.id = removeWeirdChars(id); 
    })
  }
}

function removeWeirdChars(str){
  const substitutions = [
    {weird: 'á', notWeird: 'a'},
    {weird: 'à', notWeird: 'a'},
    {weird: 'ã', notWeird: 'a'},
    {weird: 'ó', notWeird: 'o'},
    {weird: 'ò', notWeird: 'o'},
    {weird: 'é', notWeird: 'e'},
    {weird: 'è', notWeird: 'e'},
    {weird: 'ç', notWeird: 'c'}
  ]
  substitutions.forEach(sb => str = str.split(sb.weird).join(sb.notWeird))
  return str;
}
</script>


<style lang="scss" scoped>
/deep/ > p {
  opacity: .8;
}

/deep/ > h2 {
  padding-top: 100px;
  margin-top: -80px;

  @include respond-above(md) {
    font-size: 2rem;
  }
}

.markdown {
  padding-bottom: 50vh;
}
</style>

