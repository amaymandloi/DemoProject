<template>
    
<v-dialog v-model="dialog" max-width="300px">
    <template v-slot:activator="{ on, attrs }">
      <v-btn color="Black" dark class="mb-2" v-bind="attrs" v-on="on"
        >New Book</v-btn
      >
      {{formTitle}}
    </template>

    <v-card>
      <v-card-title>
        <span class="text-h5">Add new book</span>
      </v-card-title>

      <v-card-text>
        <v-container>
          <v-row>
            <v-text-field
              v-model="editedname.name"
              label="Books_Name"
            ></v-text-field>

            <v-text-field
              v-model="editedname.Author_Name"
              label="Author_Name"
            ></v-text-field>

            <v-text-field
              v-model="editedname.Published_Date"
              label="Published_Date"
            ></v-text-field>

            <v-text-field
              v-model="editedname.Pages"
              label="Pages"
            ></v-text-field>
          </v-row>
        </v-container>
      </v-card-text>

      <!-- Edit Botton Box  -->
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="red" text @click="close" > Cancel </v-btn>

        <v-btn color="success" text @click="saveBook">Save</v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
  
</template>
<script>

export default {
    setup() {
    },
props: [
    "dialog",
    "likes",
    "name",

],

  data: () => ({
    dialogDelete: false,
    name_Name: [],
    editedIndex: -1,
    
    editedname: {
      name: "",
      Author_Name:"" ,
      Published_Date:"" ,
      Pages: "",
    },

    defaultname: {
      Book: "",
      Author_Name: "",
      Published_Date: "",
      Pages: "",
    },

  }),

  methods: {
    saveBook() {
    this.close()
    this.$emit('saveBook', this.editedname)
    this.$nextTick(() => {
        this.editedname = Object.assign({}, this.defaultname);
       
      });
    },

    close() {
    this.$emit('closeBook')
    },

  },
  
}
</script>
