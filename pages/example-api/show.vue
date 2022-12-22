<template>
  <div class="container">
    <div class="card">
      <div class="card-header">
        <div class="float-start mt-2">
          Detail Employee
        </div>
        <div class="float-end">
          <b-button @click="$router.push('/example-api')" class="bg-secondary">Kembali</b-button>
        </div>
      </div>
      <div class="card-body">
        <div class="row">
          <div class="col-sm-12">
            <b-form-group
              label="Nama Lengkap"
            >
              <b-form-input
                v-model="form.nama"
                title="Masukan Nama Lengkap"
                placeholder="Contoh. Idam Idzin Dimiati"
                disabled
              />
            </b-form-group>
            <b-form-group
              label="Age"
            >
              <b-form-input
                v-model="form.age"
                title="Masukan Nama Lengkap"
                placeholder="Contoh. Idam Idzin Dimiati"
                disabled
              />
            </b-form-group>
            <b-form-group
              label="Salary"
            >
              <b-form-input
                v-model="form.salary"
                title="Masukan Nama Lengkap"
                placeholder="Contoh. Idam Idzin Dimiati"
                disabled
              />
            </b-form-group>
          </div>
        </div>
      </div>
    </div>
  </div>
  </template>

  <script>
    export default {
      name: 'ShowPage',
      layout: 'App',
      data() {
        return{
          title: 'Example Api',
          form: {
            nama: null,
            age: null,
            salary: null
          },
        }
      },
      created() {
        this.getDetail()
      },
      methods: {
        nextPage() {
          this.$router.push('/example-api/create')
        },
        async getDetail(){
          try {
            const id = this.$route.query.id
            const { data } = await this.$axios.$get(`api/v1/employee/${id}`)
            this.form.nama = data.employee_name
            this.form.age = data.employee_age
            this.form.salary = data.employee_salary
          } catch (error) {
            console.log('ERR: ', error)
          }
        }
      }
    }
  </script>
