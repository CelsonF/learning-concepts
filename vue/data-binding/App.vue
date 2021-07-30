<template>
  <div>
    <h1 v-bind:style="{textDecoration: decoration}" > Hello {{name}} </h1>
    <input type="text" v-model="name">
  </div>
</template>

<script>
   export default {
    data: () => ({
      name:'celson',
      decoration:'underline' 
    })
   }
</script>

<style>

</style>