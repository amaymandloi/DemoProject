<template>
    <v-dialog v-model="dialog" max-width="350px">
          <v-card>
            <v-card-title class="text-h5">delete this item?</v-card-title>
            <v-card-actions>
              <v-spacer></v-spacer>

              <v-btn color="green" text @click="closeDelete">Cancel</v-btn>
              <v-btn color="red" text @click="deletenameConfirm">OK</v-btn>


              <v-spacer></v-spacer>
            </v-card-actions>
          </v-card>
        </v-dialog>
</template>
<script>

export default {
    props: [
    "dialog",
],

methods: {
    deletenameConfirm() {
    this.$emit('deleteConfirm')
    },
    closeDelete() {
    this.$emit('closeDelete')
    },
  },
}
</script>
