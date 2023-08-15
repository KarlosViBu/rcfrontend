<template>
  <v-container>

  <ApolloQuery :query="query">
    <template slot-scope="{result:{ data }}">
      {{ data }}
      <!-- <div v-for="categoria in data.categories" :key="categoria.id">
        <v-btn
          :to="{
            name: 'category',
            params: { category: categoria.slug },
          }"
          class="my-1"
          >{{ categoria.name }}</v-btn
        >
      </div> -->
    </template>
  </ApolloQuery>
</v-container>
</template>

<script>
import gql from "graphql-tag";
export default {
  data() {
    return {
      query: gql`
        query {
          categories {
            data {
              id
              attributes {
                name
                icon
                slug
                img
              }
            }
          }
        }
      `,
    };
  },
};
</script>
