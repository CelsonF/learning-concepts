<template>
  <div>
    <h1> Life cycle hooks</h1>
  </div>
</template>

<script>
//Function hook normaly
import {onMounted} from 'vue'

export default {
  setup() {
   onMounted(() => {
     console.log('Foi montado composition API');
   });
  }
}

// Example Options API
// export default {
//   mounted() {
//     console.log('Foi montado options API')
//   }
// }
</script>

<style>

</style>