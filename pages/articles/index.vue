<template>
  <div>
    <Header />
    <b-container class="my-5">
      <b-row class="w-100">
        <b-col cols="4">
          <b-badge pill class="mb-3 mr-3 pt-2 px-3" v-for="tag in tags" :key="tag.id"><h6>{{ tag.name }}</h6></b-badge>
        </b-col>
        <b-col cols="8">
          <b-card
              img-src="https://picsum.photos/600/300/?image=25"
              img-alt="Image"
              img-top
              tag="article"
              class="mb-2 w-100"
              v-for="article in articles" :key="article.article.id"
            >
              <nuxt-link :to="{name: 'articles-id', params: {id: article.article.id}}" class="text-secondary text-decoration-none"><h3>{{ article.article.name }}</h3></nuxt-link>
              <b-card-text>
                {{ article.article.text }}
              </b-card-text>
              <div class="d-flex justify-content-between">
                <div class="d-flex align-items-center">
                  <svg class="mt-1" version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                    viewBox="0 0 461.312 461.312" style="width: 20px; enable-background:new 0 0 461.312 461.312;" xml:space="preserve">
                    <g>
                      <g>
                        <path d="M230.656,156.416c-40.96,0-74.24,33.28-74.24,74.24s33.28,74.24,74.24,74.24s74.24-33.28,74.24-74.24
                          S271.616,156.416,230.656,156.416z M225.024,208.64c-9.216,0-16.896,7.68-16.896,16.896h-24.576
                          c0.512-23.04,18.944-41.472,41.472-41.472V208.64z" fill="grey"/>
                      </g>
                    </g>
                    <g>
                      <g>
                        <path d="M455.936,215.296c-25.088-31.232-114.688-133.12-225.28-133.12S30.464,184.064,5.376,215.296
                          c-7.168,8.704-7.168,21.504,0,30.72c25.088,31.232,114.688,133.12,225.28,133.12s200.192-101.888,225.28-133.12
                          C463.104,237.312,463.104,224.512,455.936,215.296z M230.656,338.176c-59.392,0-107.52-48.128-107.52-107.52
                          s48.128-107.52,107.52-107.52s107.52,48.128,107.52,107.52S290.048,338.176,230.656,338.176z" fill="grey"/>
                      </g>
                    </g>
                  </svg>
                  <h6 class="text-secondary mb-0 ml-3">{{ article.views.length }}</h6>
                </div>
                <div class="d-flex align-items-center">
                  <h6 class="text-secondary mb-0 mr-3">{{ article.likes.length }}</h6>
                  <b-button variant="transparent" class="shadow-none px-0" @click="addLike(article.article.id)">
                    <svg style="width: 20px;" viewBox="0 -28 512.001 512" xmlns="http://www.w3.org/2000/svg"><path d="m256 455.515625c-7.289062 0-14.316406-2.640625-19.792969-7.4375-20.683593-18.085937-40.625-35.082031-58.21875-50.074219l-.089843-.078125c-51.582032-43.957031-96.125-81.917969-127.117188-119.3125-34.644531-41.804687-50.78125-81.441406-50.78125-124.742187 0-42.070313 14.425781-80.882813 40.617188-109.292969 26.503906-28.746094 62.871093-44.578125 102.414062-44.578125 29.554688 0 56.621094 9.34375 80.445312 27.769531 12.023438 9.300781 22.921876 20.683594 32.523438 33.960938 9.605469-13.277344 20.5-24.660157 32.527344-33.960938 23.824218-18.425781 50.890625-27.769531 80.445312-27.769531 39.539063 0 75.910156 15.832031 102.414063 44.578125 26.191406 28.410156 40.613281 67.222656 40.613281 109.292969 0 43.300781-16.132812 82.9375-50.777344 124.738281-30.992187 37.398437-75.53125 75.355469-127.105468 119.308594-17.625 15.015625-37.597657 32.039062-58.328126 50.167969-5.472656 4.789062-12.503906 7.429687-19.789062 7.429687zm-112.96875-425.523437c-31.066406 0-59.605469 12.398437-80.367188 34.914062-21.070312 22.855469-32.675781 54.449219-32.675781 88.964844 0 36.417968 13.535157 68.988281 43.882813 105.605468 29.332031 35.394532 72.960937 72.574219 123.476562 115.625l.09375.078126c17.660156 15.050781 37.679688 32.113281 58.515625 50.332031 20.960938-18.253907 41.011719-35.34375 58.707031-50.417969 50.511719-43.050781 94.136719-80.222656 123.46875-115.617188 30.34375-36.617187 43.878907-69.1875 43.878907-105.605468 0-34.515625-11.605469-66.109375-32.675781-88.964844-20.757813-22.515625-49.300782-34.914062-80.363282-34.914062-22.757812 0-43.652344 7.234374-62.101562 21.5-16.441406 12.71875-27.894532 28.796874-34.609375 40.046874-3.453125 5.785157-9.53125 9.238282-16.261719 9.238282s-12.808594-3.453125-16.261719-9.238282c-6.710937-11.25-18.164062-27.328124-34.609375-40.046874-18.449218-14.265626-39.34375-21.5-62.097656-21.5zm0 0" fill="#000"/></svg>
                  </b-button>
                </div>
              </div>
            </b-card>
            <b-pagination
              v-model="currentPage"
              :total-rows="rows"
              :per-page="perPage"
              first-text="В начало"
              last-text="В конец"
            ></b-pagination>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Header from '@/components/header'
export default {
  components: {
    Header
  },
  data() {
    return {
      perPage: 5,
      currentPage: 1,
      tags: [],
      articles: []
    }
  },
  mounted() {
    this.loadTags();
    this.loadArticles();
  },
  methods: {
    async loadTags() {
      const data = await this.$axios.$get('/tags');
      this.tags = data;
    },
    async loadArticles() {
      const data = await this.$axios.$get('/articles');
      this.articles = data;

      var cutArticles = this.articles.slice(-10);
      this.articles = cutArticles;

      for(var i = 0; i < this.articles.length; i++) {
        var cutText = this.articles[i].article.text.slice(0, 100) + '...';
        this.articles[i].article.text = cutText;
      }
    },
    async addLike(articleId) {
      const formData = new FormData();
      formData.append("article_id", articleId);
      this.$axios.$post('/likes', formData, {
        headers: {
        'Content-Type': 'multipart/form-data'
      }
      }).then(response => {
        if (response.created_at) {
          //console.log('the like was add')
          this.loadArticles();
        }
      })
    }
  },
  computed: {
    rows() {
      return this.articles.length
    }
  }
}
</script>
