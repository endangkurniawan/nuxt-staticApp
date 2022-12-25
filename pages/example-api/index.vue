<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-12">
        <div class="card">
          <div class="card-header">
            <div class="float-start mt-1">
              <h4 class="table-title">{{ title }}</h4>
            </div>
            <div class="float-end">
              <button v-on:click="nextPage" class="btn btn-info" type="button">
                <i class="fas fa-plus-circle"></i> + Add
              </button>
            </div>
          </div>
          <div class="card-body">
            <table class="table table-bordered align-middle ">
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
                  <td class="text-center">{{ employee.employee_age }}</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
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
