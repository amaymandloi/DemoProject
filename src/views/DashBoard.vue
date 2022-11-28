<template>
<v-data-table :headers="headers" :items="booksName" sort-by="Author_Name" class="elevation-1">
    <template v-slot:top>
      <v-toolbar flat>
        <v-toolbar-title>Book_Collections</v-toolbar-title>
        <v-spacer></v-spacer>
       
        <BookDialog @saveBook="save"
                    @closeBook="close" 
                    :dialog="dialog">
        </BookDialog>


        <EditBookDialog @saveBook="saveEdit" 
                        @closeBook="closeEdit" 
                        :dialog="editDialog" 
                        :name="editedname.name" 
                        :authorName="editedname.Author_Name" 
                        :publishedDate="editedname.Published_Date" 
                        :pages="editedname.Pages">
        </EditBookDialog>


        <!-- Button_Box -->

        <DeleteBookDialog @deleteConfirm="deletenameConfirm" 
                          @closeDelete="closeDelete" 
                          :dialog="dialogDelete">
        </DeleteBookDialog>

      </v-toolbar>
    </template>

        <!-- action -->

   
  <template v-slot:[`item.actions`]="{ item }">
   
    <EditButtonVue @editEvent="editname(item)"></EditButtonVue>

    <DeleteButton @deleteEvent="deletename(item)"></DeleteButton>
  </template>

</v-data-table>
</template>

<script>

import EditButtonVue from '@/components/EditButton.vue';
import DeleteButton from '@/components/DeleteButton.vue';
import BookDialog from '@/components/BookDialog.vue';
import EditBookDialog from '@/components/EditBookDialog.vue';
import DeleteBookDialog from '@/components/DeleteBookDialog.vue';

export default {
  components: {
    EditButtonVue,
    DeleteButton,
    BookDialog,
    EditBookDialog,
    DeleteBookDialog
  },

  data: () => ({
    dialog: false,
    editDialog: false,
    dialogDelete: false,
    headers: [
      
      {text: "Book_Name",align: "start",sortable: false,value: "name",},
      { text: "Author_Name", value: "Author_Name" },
      { text: "Published_Date", value: "Published_Date" },
      { text: "Pages ", value: "Pages" },
      { text: "Actions", value: "actions", sortable: false },
    ],

    booksName: [],
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

  computed: {
    formTitle() {
       return this.editedIndex === -1 ? 'New name' : 'Edit name'
      },
  },

  watch: {
    dialog(val) {
      val || this.close();
    },
    dialogDelete(val) {
      val || this.closeDelete();
    },
  },

  created() {
    this.initialize();
  },

  methods: {

    changeName(item) {
      
    },
    initialize() {
      this.booksName = [
       {
          name: 'Black Cake',
          Author_Name: "Charmaine Wilkerson",
          Published_Date:"1/Feb/2022" ,
          Pages: 385,
        },
        {
          name: 'Young Mungo',
          Author_Name: "Douglas Stuart",
          Published_Date: "5/April/2022",
          Pages: 390 ,
        },
        {
          name: 'Take MY Hand',
          Author_Name: "Dolen Perkins-Valdez",
          Published_Date: "12/april/2022",
          Pages: 359,
        },
        {
          name: 'The Diamond Eye',
          Author_Name:"Kate Quinn",
          Published_Date:"29/March/2022",
          Pages:435
        },
        {
          name: 'Trust',
          Author_Name:"Hernan Diaz",
          Published_Date:"03/May/2022",
          Pages:416
        },
        {
          name: 'Hester',
          Author_Name:"Laurie Lico Albanese",
          Published_Date:"04/Oct/2022",
          Pages:336
        },
        {
          name: 'Shrines of Gaiety',
          Author_Name:"Kate Atkinson",
          Published_Date:"27/Sep/2022",
          Pages:416
        },
        {
          name: 'Take MY Hand',
          Author_Name: "Dolen Perkins-Valdez",
          Published_Date: "12/april/2022",
          Pages: 359,
        },
        {
          name: 'Small Angels',
          Author_Name:"Lauren Owen",
          Published_Date:"02/Aug/2022",
          Pages:400
        },
        {
          name: 'Take MY Hand',
          Author_Name: "Dolen Perkins-Valdez",
          Published_Date: "12/april/2022",
          Pages: 359,
        },
        {
          name: 'The Fervor',
          Author_Name:"Alma Katsu",
          Published_Date:"26/April/2022",
          Pages:309
        },
        {
          name: 'The Hacienda',
          Author_Name:"Isabel Cañas",
          Published_Date:"03/May/2022",
          Pages:352
        },
        {
          name: 'Take MY Hand',
          Author_Name: "Dolen Perkins-Valdez",
          Published_Date: "12/april/2022",
          Pages: 359,
        },
        {
          name: 'Sundial',
          Author_Name:"Catriona Ward",
          Published_Date:"01/March/2022",
          Pages:435
        },
        {
          name: 'Take MY Hand',
          Author_Name: "Dolen Perkins-Valdez",
          Published_Date: "12/april/2022",
          Pages: 359,
        },
        {
          name: 'The Violence',
          Author_Name:"Delilah S. Dawson",
          Published_Date:"01/Feb/2022",
          Pages:512
        },
        {
          name: 'Take MY Hand',
          Author_Name: "Dolen Perkins-Valdez",
          Published_Date: "12/april/2022",
          Pages: 359,
        },
      ];
    },

    editname(item) {
      this.editedIndex = this.booksName.indexOf(item);
      this.editedname = Object.assign({}, item);
      this.editDialog = true;
      
    },

    deletename(item) {
      
      this.editedIndex = this.booksName.indexOf(item);
      this.editedname = Object.assign({}, item);
      this.dialogDelete = true;
    },

    deletenameConfirm() {
      this.booksName.splice(this.editedIndex, 1);
      this.closeDelete();
    },

    close() {
      this.dialog = false;
      this.$nextTick(() => {
        this.editedname = Object.assign({}, this.defaultname);
        this.editedIndex = -1;
      });
    },
    closeEdit() {
      this.editDialog = false;
      this.$nextTick(() => {
        this.editedname = Object.assign({}, this.defaultname);
        this.editedIndex = -1;
      });
    },

    closeDelete() {
      this.dialogDelete = false;
      this.$nextTick(() => {
        this.editedname = Object.assign({}, this.defaultname);
        this.editedIndex = -1;
      });
    },

    save(item) {
      if (this.editedIndex > -1) {
        Object.assign(this.booksName[this.editedIndex], this.editedname);
      } else {
        this.booksName.push(item);
      }
      this.close();
    },
    saveEdit(item) {
      
      Object.assign(this.booksName[this.editedIndex], item);
      },
  },
};
</script>
