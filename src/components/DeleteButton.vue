<template>

       <v-btn
        class="mx-2"
        fab
        dark
        small
        color="primary"
        @click="submit"
      >
        <v-icon dark>mdi-minus</v-icon>
      </v-btn>
 </template>
   <script>
  export default {
    
   methods: {
     submit() {
        
       this.$emit('deleteEvent')
     }
   }
 }
   </script>