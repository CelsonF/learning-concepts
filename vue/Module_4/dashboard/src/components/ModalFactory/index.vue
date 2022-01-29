<template>
   <teleport to="body">
     <div 
      v-if="state.isActive"
      class="fixed top-0 left-0 z-50 flex items-center justify-center w-full h-full bg-black opacity-50"
      @click="handleModalToggle({status: false})"
      >
       <div class="fixed mx-10">
            <div class="flex flex-col overflow-hidden bg-white rounded-lg animate__animated animate__fadeInDown animate__faster">
               <div class="flex flex-col px-12 py-0 bg-white">
                 <component :is="state.component"/>
               </div>
            </div>
       </div>
     </div>
   </teleport>
</template>

<script>
import { reactive } from '@vue/reactivity'

const DEFAULT_WIDTH = 'w-3/4 lg:w-1/3'

export default {
 setup() {
     const state = reactive({
         isActive:false,
         component:{
         },
         props: {
         },
         width:DEFAULT_WIDTH
     })
     
     function handleModalToggle({ status}) {
         
     }

     return {
         state
     }
 }
}
</script>

<style>

</style>