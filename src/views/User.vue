<template>
    <v-simple-table>
      <template v-slot:default>
        <thead id="new">
          <tr>
            <th class="text-left">
              id
            </th>
            <th class="text-left">
              name
            </th>
            <th class="text-left">
                email
            </th>
            <th class="text-left">
            address
            </th>
            <th class="text-left">
                phone
            </th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="item in list"
            :key="item.id"
          >
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.email }}</td>
            <td>{{ item.address }}</td>
            <td>{{ item.phone }}</td>

          </tr>
        </tbody>
      </template>
    </v-simple-table>
  </template>
<script>
export default {
  name: "User",
  data() {
    return {
      list: [],
    };
  },
  async created() {
    const response = await fetch("https://jsonplaceholder.typicode.com/users");
    const list = await response.json();
    this.list = list;
  },
};
</script>

<style>
 .new {
    border: 1px solid black;
 }
</style>
