<template>

  <div class="container">
            <div>
              <b-button id="show-btn" class="mt-2 mb-3" variant="primary" @click="onReset; $bvModal.show('bv-modal-example')">Tambah Pegawai</b-button>
<b-modal id="bv-modal-example" hide-footer>
    <template #modal-title>
     Input Data Pegawai
    </template>
    <div class="d-block ">
      <b-form @submit="onSubmit" @reset="onReset" v-if="show">
                     <b-form-group
                     id="input-group-1"
                     label="Id:"
                     label-for="input-1"
                     >
                     <b-form-input
                        id="input-1"
                        v-model="form.id"
                        type="text"
                       readonly
                        placeholder=""
                     ></b-form-input>
                     </b-form-group>

                     <b-form-group
                     id="input-group-2"
                     label="Nama:"
                     label-for="input-2"
                     >
                     <b-form-input
                        id="input-2"
                        v-model="form.nama"
                        type="text"
                        required
                        placeholder=""
                     ></b-form-input>
                     </b-form-group>

                     <b-form-group
                     id="input-group-3"
                     label="Jabatan:"
                     label-for="input-3"
                     >
                     <b-form-input
                        id="input-3"
                        v-model="form.jabatan"
                        type="text"
                        required
                        placeholder=""
                     ></b-form-input>
                     </b-form-group>

                     <b-button type="submit" variant="primary">Submit</b-button>
                     <b-button type="reset" variant="danger">Reset</b-button>
                  </b-form>
     </div>
</b-modal>

               <!--<b-button type="button" variant="success" @click="">Add</b-button>-->
                  <b-table
                     id="my-table"
                     :items="items"
                     :fields="fields"
                     :per-page="perPage"
                     :current-page="currentPage"
                     striped 
                     hover
                  >
                  </b-table>
                  <b-pagination
                     v-model="currentPage"
                     :total-rows="rows"
                     :per-page="perPage"
                     aria-controls="my-table"
                  ></b-pagination>

                  <p class="mt-3">Current Page: {{ currentPage }}</p>
                  
                  <b-card class="mt-3" header="Form Data Result">
                     <pre class="m-0">{{ form }}</pre>
                  </b-card>
             </div>
         </div>
</template>

<script>
//import IndexVue from './components/IndexVue.vue'

export default {
  name: 'App',
  //components: {
  //  IndexVue
  //},
  data() {
      return {
        perPage: 3,
        currentPage: 1,
        fields: [
          'id', 
          'nama', 
          'jabatan',
        ],
        items: [
          
        ],
        form: {
          id: 'slice[1]',
          nama: '',
          jabatan: '',
        },
        show: true,
      }
    },
    computed: {
      rows() {
        return this.items.length
      }
    },
    mounted() {
    if (localStorage.id) {
      this.id = localStorage.id;
    }
    if (localStorage.nama) {
      this.nama = localStorage.nama;
    }
  },
    methods: {
      onSubmit(evt) {
        evt.preventDefault()
        alert(JSON.stringify(this.form))
        this.items.push({ 
          id: this.form.id [1], 
          nama: this.form.nama, 
          jabatan: this.form.jabatan 
          })
      },
      onReset(evt) {
        evt.preventDefault()
        // Reset our form values
        this.form.id = ''
        this.form.nama = ''
        this.form.jabatan = ''
        this.form_action = 'Insert'
        // Trick to reset/clear native browser form validation state
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      }
    }
//END
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /*color: #2c3e50;*/
  margin-top: 60px;
}
#form{
  margin-bottom: 5px;
}
#formselec{
  width: 100%;
}
#label{
  text-align: justify;
}
#body{
  margin: 10px;
}
</style>
