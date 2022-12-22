<template>
  <div class="container">
    <h4 class="table-title mb-4 mt-4">{{ title }}</h4>
    <button v-on:click="nextPage" class="btn btn-info float-end mb-4" type="button">
      <i class="fas fa-plus-circle"></i> + Add
    </button>
    <table class="table table-bordered align-middle border-dark">
      <thead class="head text-center">
        <tr>
          <th class="id w-25">#</th>
          <th>Name</th>
          <th>Age</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(employee, index) in employees" :key="index">
          <td class="text-center">
            <b-button
              :to="{
                path: 'example-api/show',
                query: {
                  id: employee.id,
                }
              }">
              Show
            </b-button>
            <b-button
              :to="{
                path: 'example-api/edit',
                query: {
                  id: employee.id,
                }
              }" >
              Edit
            </b-button>
          </td>
          <td class="rowname">
            {{ employee.employee_name }}
          </td>
          <td>{{ employee.employee_age }}</td>
        </tr>
      </tbody>
    </table>
  </div>
  </template>

  <script>
    export default {
      name: 'ExampleApiPage',
      layout: 'App',
      data() {
        return{
          title: 'Example Api',
          employees: [],
        }
      },
      created(){
        this.getEmployees()
      },
      methods: {
        nextPage() {
          this.$router.push('/example-api/create')
        },
        async getEmployees(){
          try {
            const { data } = await this.$axios.$get('api/v1/employees')
            this.employees = data
          } catch (error) {
            console.log('ERR: ', error)
          }
        }
      }
    }
  </script>
