<template>
    
<v-dialog v-model="dialog" max-width="300px">
    
    <v-card>
      <v-card-title>
        <span class="text-h5">Edit book</span>
      </v-card-title>
     
      <v-card-text>
        <v-container>
          <v-row>
            <v-text-field
              v-model="name"
              label="Books_Name"
            ></v-text-field>

            <v-text-field
              v-model="authorName"
              label="Author_Name"
            ></v-text-field>

            <v-text-field
              v-model="publishedDate"
              label="Published_Date"
            ></v-text-field>

            <v-text-field
              v-model="pages"
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
    "authorName",
    "publishedDate",
    "pages",
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
    const editedname= {
      name: this.name,
      Author_Name: this.authorName ,
      Published_Date: this.publishedDate ,
      Pages: this.pages,
    }
    this.$emit('saveBook', editedname)
    this.$nextTick(() => {
        this.editedname = Object.assign({}, this.defaultname);
        // this.editedIndex = -1;
      });
    },
    close() {
    this.$emit('closeBook')
    },
  },
}
</script>
