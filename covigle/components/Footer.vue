<template>
  <footer>
    <p>data source : {{ source }}</p>
  </footer>
</template>

<script>
const source =
  'COVID-19 Open Research Dataset (CORD-19). ' +
  '2020. Version 2020-03-27. Retrieved from https://pages.semanticscholar.org/coronavirus-research. ' +
  'Accessed 2020-03-28. doi:10.5281/zenodo.3715505'

export default {
  data: () => ({
    source
  })
}
</script>

<style>
footer {
  color: #fff;
  padding: 10px;
  background-color: #2b4257;
  font-size: 15px;
}
</style>
