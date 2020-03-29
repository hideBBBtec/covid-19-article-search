<template>
  <div>
    <header>
      <h1>Covigle</h1>
      <p>{{ description }}</p>
      <p>
        <!-- <HeaderNav /> -->
      </p>
    </header>
  </div>
</template>
<script>
const description = 'Search published papers on covid-19'

export default {
  data: () => ({
    description
  })
  // components: {
  // }
}
</script>
<style>
header {
  color: #fff;
  padding: 20px;
  background-color: #008080;
}
</style>
