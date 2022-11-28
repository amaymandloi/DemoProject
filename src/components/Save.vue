<template>
    
</template>

<script>

export default {
    save() {
      if (this.editedIndex > -1) {
        Object.assign(this.name[this.editedIndex], this.editedname);
      } else {
        this.name.push(this.editedname);
      }
      this.close();
    },

}
</script>

<style>


</style>