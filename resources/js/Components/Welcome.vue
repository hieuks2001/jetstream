<script setup></script>

<template>
    <div>
        <section class="text-gray-600 body-font">
            <div class="container px-5 py-24 mx-auto">
                <div class="flex flex-col text-center w-full mb-10">
                    <h1 class="sm:text-4xl text-3xl font-medium title-font mb-2 text-gray-900">Contact list</h1>
                </div>
                <div class="w-full mx-auto overflow-auto">
                    <a-table :dataSource="contacts.data" :columns="columns"/>
                </div>
            </div>
        </section>
    </div>
</template>


<script>
import axios from 'axios';

import { ref } from 'vue';


  export default {
    data() {
    return {
      contacts: [],
      errors: [],
    
    }
  }, 
  created(){
    axios.get(`http://127.0.0.1:8000/api/contacts`)
    .then(response => {
      this.contacts = response.data.contacts
    })
    .catch(e => {
      this.errors.push(e)
    })
  },

    setup() {
      return {      
        columns: [
          {
            title: 'Name',
            dataIndex: 'name',
            key: 'name',
          },
          {
            title: 'Email',
            dataIndex: 'email',
            key: 'email',
          },
          {
            title: 'Phone number',
            dataIndex: 'phone_number',
            key: 'phone_number',
          },
          {
            title: 'Country',
            dataIndex: 'country',
            key: 'country',
          },
          {
            title: 'Message',
            dataIndex: 'message',
            key: 'message',
          },
        ],
      };
    },
  };
</script>
