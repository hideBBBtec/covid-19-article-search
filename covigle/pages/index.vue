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
// import Logo from '~/components/Logo.vue'

const items = []

for (let i = 0; i < 100; i++) {
  const item = {}
  item.source = 'biorxiv'
  item.title = 'title' + i
  item.author = 'author' + i
  item.url = 'https://doi.org/10.1101/001727'
  items.push(item)
}

export default {
  components: {
    // Logo
  },
  data() {
    return {
      items,
      now_keyword: '',
      keyword: ''
    }
  },
  methods: {
    search() {
      this.now_keyword = this.keyword
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
