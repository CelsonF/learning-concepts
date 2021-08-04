<template>
  <div>
    <h1 v-bind:style="{textDecoration: decoration}" > Hello {{name}} !</h1>
    <input type="text" v-model="name">
    <br>
    <a :href="link">Link do Curso!</a>
  </div>
</template>

<script>
   export default {
    data: () => ({
      name:'celson',
      link:'https://igorhalfeld.teachable.com/courses/treinamento-completo-e-gratuito-de-vue-js-3-do-iniciante-ao-avancado/lectures/29446833',
      decoration:'underline' 
    })
   }
</script>

<style>

</style>