<template>
  <Layout>
    <v-card
      class="mx-sm-auto"
      v-for="item in $page.articles.edges"
      :key="item.node.id"
      :href="item.node.path"
    >
      <v-img height="500px" :src="item.node.preview_image"> </v-img>

      <v-card-text>
        <h3 class="primary--text font-weight-bold mx-0 display-2 px-xs-5">
          {{ item.node.title }}
        </h3>
        <br />
        <span class="px-xs-5">{{ item.node.author }}</span
        ><br />
        <span class="px-xs-5"
          >Date: {{ item.node.date }} | Time: {{ item.node.timeToRead }} to
          read</span
        >
      </v-card-text>
      <v-btn text color="orange" :href="item.node.path">Read More</v-btn>
    </v-card>
  </Layout>
</template>

<page-query>
  query GetArticles {
    articles: allArticle (perPage: 1, filter: { published: { eq: true }}) {
      edges {
        node {
          id
          path
          date (format: "MMMM D, YYYY")
          preview_image (quality: 90)
          title
          published
          excerpt
        }
      }
    }
  }
</page-query>

<script></script>

<style></style>
