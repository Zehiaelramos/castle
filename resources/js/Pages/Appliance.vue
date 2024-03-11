<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';
</script>

<template>
    <Head title="Aparatos" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">Aparatos</h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6 text-gray-900">You're logged in!</div>
                </div>
            </div>
        </div>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6 text-gray-900">You're logged in!</div>
                </div>
            </div>
        </div>

        <table class="table">
            <thead>
                <tr v-for="appliance in appliances" :key="appliance.id"></tr>
                <td class="py-0 text-center">{{ appliance.id }}</td>
            </thead>
        </table>

    </AuthenticatedLayout>
</template>

<script>
  import axios from 'axios';

  export default {
    name: 'ApplianceComponent',
    data() {
      return {
        appliance: {},
        appliances: {
          id: '',
          name: '',
          description: '',
        },
      };
    },
    created() {
      this.getAppliances()
    },
    methods: {
      getAppliances() {
        axios.get('/appliances')
          .then(resp => {
            this.appliances = resp.data
            console.log('this.appliances: ', resp.data)
          })
      }
    }
  }
</script>
