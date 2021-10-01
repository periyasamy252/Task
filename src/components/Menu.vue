<template>
  <div class="content"></div>
</template>

<script>
import axios from 'axios'
export default  {
  created ()  {
    axios.get('https://https://jsonplaceholder.typicode.com/posts').then((result) =>  {
      console.log(result.data)
    })
  }
}
</script>

<style scoped lang="scss">
</style>
