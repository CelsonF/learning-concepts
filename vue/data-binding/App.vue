<template>
  <div>
   <h1> Hello {{name}} </h1>
   <input type="text" v-model="name">
  </div>
</template>

<script>
export default {
data: () => ({
  name:'celson'  
})
}
</script>

<style>

</style>