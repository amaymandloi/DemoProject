<template>
    <v-data-table
      :headers="headers"
      :items="Book"
      sort-by="calories"
      class="elevation-1"
    >
      <template v-slot:top>
        <v-toolbar
          flat
        >
          <v-toolbar-title>My CRUD</v-toolbar-title>
          <v-divider
            class="mx-4"
            inset
            vertical
          ></v-divider>
          <v-spacer></v-spacer>
          <v-dialog
            v-model="dialog"
            max-width="500px"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                color="primary"
                dark
                class="mb-2"
                v-bind="attrs"
                v-on="on"
              >
                New Item
              </v-btn>
            </template>
            <v-card>
              <v-card-title>
                <span class="text-h5">{{ formTitle }}</span>
              </v-card-title>
  
              <v-card-text>
                <v-container>
                  <v-row>
                    <v-col
                      cols="12"
                      sm="6"
                      md="4"
                    >
                      <v-text-field
                        v-model="editedItem.name"
                        label="Dessert name"
                      ></v-text-field>
                    </v-col>
                    <v-col
                      cols="12"
                      sm="6"
                      md="4"
                    >
                      <v-text-field
                        v-model="editedItem.calories"
                        label="Calories"
                      ></v-text-field>
                    </v-col>
                    <v-col
                      cols="12"
                      sm="6"
                      md="4"
                    >
                      <v-text-field
                        v-model="editedItem.fat"
                        label="Fat (g)"
                      ></v-text-field>
                    </v-col>
                    <v-col
                      cols="12"
                      sm="6"
                      md="4"
                    >
                      <v-text-field
                        v-model="editedItem.carbs"
                        label="Carbs (g)"
                      ></v-text-field>
                    </v-col>
                    <v-col
                      cols="12"
                      sm="6"
                      md="4"
                    >
                      <v-text-field
                        v-model="editedItem.protein"
                        label="Protein (g)"
                      ></v-text-field>
                    </v-col>
                  </v-row>
                </v-container>
              </v-card-text>
  
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn
                  color="blue darken-1"
                  text
                  @click="close"
                >
                  Cancel
                </v-btn>
                <v-btn
                  color="blue darken-1"
                  text
                  @click="save"
                >
                  Save
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-dialog>
          <v-dialog v-model="dialogDelete" max-width="500px">
            <v-card>
              <v-card-title class="text-h5">Are you sure you want to delete this item?</v-card-title>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="blue darken-1" text @click="closeDelete">Cancel</v-btn>
                <v-btn color="blue darken-1" text @click="deleteItemConfirm">OK</v-btn>
                <v-spacer></v-spacer>
              </v-card-actions>
            </v-card>
          </v-dialog>
        </v-toolbar>
      </template>
      <!-- <template v-slot:item.actions="{ item }"> -->
        <template v-slot:[`item.actions`]="{ item}">
        <v-icon
          small
          class="mr-2"
          @click="editItem(item)"
        >
          mdi-pencil
        </v-icon>
        <v-icon
          small
          @click="deleteItem(item)"
        >
          mdi-delete
        </v-icon>
      </template>
      <template v-slot:no-data>
        <v-btn
          color="primary"
          @click="initialize"
        >
          Reset
        </v-btn>
      </template>
    </v-data-table>
  </template>

<script>
export default {
  data: () => ({
    dialog: false,
    dialogDelete: false,
    headers: [
      {
        text: 'Book_Name',
        align: 'start',
        sortable: false,
        value: 'name',
      },
      { text: 'Author_Name', value: 'Author_Name' },
      { text: 'Published_Date', value: 'Published_Date' },
      { text: 'Pages', value: 'Pages'},
      { text: 'Action', value:'actions'},
    ],
    Book: [],
    editedIndex: -1,
    editedItem: {
      Book_Name: '',
      Author_Name: 0,
      Published_Date: 0,
      Pages: 0,
    },
    defaultItem: {
      Book_Name: '',
      Author_Name: 0,
      Published_Date: 0,
      Pages: 0,
    },
  }),

  computed: {
    formTitle () {
      return this.editedIndex === -1 ? 'New Book' : 'Edit Book'
    },
  },

  watch: {
    dialog (val) {
      val || this.close()
    },
    dialogDelete (val) {
      val || this.closeDelete()
    },
  },

  created () {
    this.initialize()
  },

  methods: {
    initialize () {
      this.Book = [
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
          Published_Date: "12?april/2022",
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
          Published_Date: "12?april/2022",
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
          Published_Date: "12?april/2022",
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
          Published_Date: "12?april/2022",
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
          Published_Date: "12?april/2022",
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
          Published_Date: "12?april/2022",
          Pages: 359,
        },
      ]
    },

    editItem (item) {
      this.editedIndex = this.Book.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialog = true
    },

    deleteItem (item) {
      this.editedIndex = this.Book.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialogDelete = true
    },

    deleteItemConfirm () {
      this.Book.splice(this.editedIndex, 1)
      this.closeDelete()
    },

    close () {
      this.dialog = false
      this.$nextTick(() => {
        this.editedItem = Object.assign({}, this.defaultItem)
        this.editedIndex = -1
      })
    },

    closeDelete () {
      this.dialogDelete = false
      this.$nextTick(() => {
        this.editedItem = Object.assign({}, this.defaultItem)
        this.editedIndex = -1
      })
    },

    save () {
      if (this.editedIndex > -1) {
        Object.assign(this.Book[this.editedIndex], this.editedItem)
      } else {
        this.Book.push(this.editedItem)
      }
      this.close()
    },
  },
}
</script>