// src/App.vue
<template>

  <h1 class="text-2xl font-bold bg-origin-padding">Contacts List</h1>
  <button
    class=" bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded"
    @click="RandomContact()">Random Contacts</button>
  <button
    class="bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded"
    @click="SortbyPopularity()">Sort by Popularity</button>

  <button
    class="bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded"
    @click="SortedNames()">Sort by Name</button>
  <table class="shadow-lg bg-white">
    <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">Ironcontacts</thead>
    <tbody class="bg-white border-b dark:bg-gray-800 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-600">
      <th class="bg-blue-100 border text-left px-8 py-4">Picture</th>
      <th class="bg-blue-100 border text-left px-8 py-4">Name </th>
      <th class="bg-blue-100 border text-left px-8 py-4">Popularity</th>
      <th class="bg-blue-100 border text-left px-8 py-4">Won Oscar</th>
      <th class="bg-blue-100 border text-left px-8 py-4">Won Emmy</th>
      <th class="bg-blue-100 border text-left px-8 py-4">Delete</th>


      <tr v-for="contact in contacts">


        <td class="border px-8 py-4">
          <!-- :to="`/list/${country.alpha3Code}`"> -->
          <img :src="contact.pictureUrl" alt="" />

        </td>
        <td class="border px-8 py-4">{{ contact.name }}</td>
        <td class="border px-8 py-4">{{ contact.popularity }}</td>
        <td class="border px-8 py-4" v-if="contact.wonOscar === true"> <i class="fas fa-trophy"></i>
        </td>
        <td class="border px-8 py-4" v-else>
        <td>"no oscar"</td>
        </td>

        <td class="border px-8 py-4" v-if="(contact.wonEmmy) === true"> <i class="fas fa-trophy"></i>
        </td>
        <td class="border px-8 py-4" v-else>"no emmy"</td>

        <td class="border px-8 py-4"><button
            class="bg-transparent hover:bg-blue-500 text-red-700 font-semibold hover:text-white py-2 px-4 border border-red-500 hover:border-transparent rounded"
            @click="contacts.splice(index, 1)">Delete Contact</button></td>



      </tr>

    </tbody>
  </table>
</template>


<style>

</style>

<script>
import CONTACTS from "./contacts.json";

export default {
  data() {

    return {
      contacts: CONTACTS.splice(0, 5),


    };
  },
  methods: {


      RandomContact() {

        //filter first 
        let RandomContact = this.contacts.push(CONTACTS[Math.floor(Math.random() * CONTACTS.length)]);
        return RandomContact;

      },




    // DeleteContact() {
    //   delete this.contacts
    // },
    SortbyPopularity() {
      this.contacts.sort((a, b) => b.popularity - (a.popularity));


    },

    SortedNames() {

      console.log(this.contacts)

      let NameSort = this.contacts.sort((a, b) => a.name.localeCompare(b.name));



      console.log(this.contacts)
      return NameSort

    },


    //   removeRow: function (index) {
    //     console.log("Removing", index);
    //     this.contacts.splice(index, 1);
    //   },
    // },
  },

};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
