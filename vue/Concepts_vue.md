# VueJS 

## Vue CLI 
```https://cli.vuejs.org/```

### Conceitos Básicos do Vue JS   

1. #### Single-File 
   Components são os arquivos nos quais tem a terminação .vue , você pode criar usando o VUE CLI no qual tem o link acima.

2. #### Data-Binding
   Usando v-bind ou ( : ) , passando uma propriedade do html há frente, você consegue usar os dados da model em sua propriedade.
   Exemplo:

   ```
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
   ```

   Usando diretiva v-model você consegue fazer um Two-way data binding vinculando o que estiver no data() com o que está na view usando interpolação de Mustache {{}}