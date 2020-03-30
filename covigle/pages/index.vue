<template>
  <b-container>
    <b-row>
      <b-col>
        <b-form-input
          v-model="keyword"
          placeholder="Enter keyword"
        ></b-form-input>
      </b-col>
      <b-col cols="12" md="auto">
        <b-button variant="outline-primary" @click="search">Search</b-button>
      </b-col>
    </b-row>
    <b-row>
      <b-col>searching : {{ now_keyword }}</b-col>
    </b-row>
    <b-row>
      <b-col>
        <b-table striped hover :items="items"></b-table>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import axios from 'axios'

// const items = []

// for (let i = 0; i < 100; i++) {
//   const item = {}
//   item.source = 'biorxiv'
//   item.title = 'title' + i
//   item.author = 'author' + i
//   item.url = 'https://doi.org/10.1101/001727'
//   items.push(item)
// }

export default {
  components: {},
  // mounted() {
  //   console.log('mounting...')
  // },
  data() {
    return {
      items: [],
      now_keyword: '',
      keyword: ''
    }
  },
  methods: {
    search() {
      this.$nuxt.$loading.start()
      this.now_keyword = this.keyword
      const template = {
        source: 'biorxiv',
        title: 'title',
        author: 'author',
        journal: 'journal',
        url: 'https://doi.org/10.1101/001727'
      }

      axios
        .post(
          'https://tonedtcbwe.execute-api.ap-northeast-1.amazonaws.com/search',
          { keyword: this.keyword }
        )
        .then((response) => {
          console.log(`get success`, response)
          for (let i = 0; i < Object.keys(response.data.source_x).length; i++) {
            const tmp = {}
            Object.assign(tmp, template)
            tmp.source = response.data.source_x[i]
            tmp.title = response.data.title[i]
            tmp.author = response.data.authors[i]
            tmp.journal = response.data.journal[i]
            tmp.url = response.data.url[i]
            this.items.push(tmp)
          }
          this.$nuxt.$loading.finish()
        })
    }
  }
}
</script>

<style>
/* .container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
} */
</style>
