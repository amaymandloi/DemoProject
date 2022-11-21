<template>
    <v-data-table
      dense
      :headers="headers"
      :items="Book_Name"
      item-key="name"
      class="elevation-1"
    ></v-data-table>
  </template>
  <script>
  export default {
    data: () => ({
      Book_Name: [
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
      ],
      headers: [
        {
          text: 'BOOK_NAME',
          align: 'start',
          sortable: false,
          value: 'name',
        },
        { text: 'Author_Name', value: 'Author_Name' },
        { text: 'Published_Date', value: 'Published_Date' },
        { text: 'Pages', value: 'Pages' },
      ],
    }),
  }
</script>