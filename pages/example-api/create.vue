<template>
  <div class="container">
    <div v-if="status" class="alert alert-success">{{ message }}</div>
    <div class="card">
      <div class="card-header">
        <div class="float-start mt-2">
          Tambahkan Data
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
              />
            </b-form-group>
            <b-form-group
              label="Umur"
            >
              <b-form-input
                v-model="form.umur"
                title="Masukan Umur"
                placeholder="Contoh. 25"
              />
            </b-form-group>
            <b-form-group
              label="Gaji"
            >
              <b-form-input
                v-model="form.salary"
                title="Masukan Nominal Gaji"
                placeholder="Contoh. 320802"
              />
            </b-form-group>
          </div>
        </div>
      </div>
      <div class="card-footer">
        <b-button @click="simpan">Simpan</b-button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'CreatePage',
    layout: 'App',
    data() {
      return{
        title: 'Example Api',
        form: {
          nama: null,
          umur: null,
          salary: null
        },
        message: null,
        status: false,
      }
    },
    methods: {
      async simpan(){
        try {
          const res = await this.$axios.$post('api/v1/create', {
            name: this.form.nama,
            age: this.form.umur,
            salary: this.form.salary,
          })

          if(res.status === 'success'){
            console.log('OK')
            this.status = true
            this.message = res.message

            this.form.nama = null
            this.form.umur = null
            this.form.salary = null
          }
          console.log(res)
        } catch (error) {
          console.log('ERR: ', error)
        }
      }
    }
  }
</script>
