<template>
  <div class="q-pa-md">
    <q-table
      title="Treats"
      :data="data"
      :columns="columns"
      row-key="name"
      dark
      color="amber"
    />
  </div>
</template>

<style>
</style>


<script>

import project from "../api/project/index";
export default {
    name: 'Project',
  data () {
    return {
      columns: [
        {
          name: 'id',
          required: true,
          label: 'ID',
          align: 'left',
          field: row => row.id,
          sortable: true
        },
        
        {
          name: 'projectName',
          required: true,
          label: 'Nama Project',
          align: 'left',
          field: row => row.projectName,
          sortable: true
        },

        {
          name: 'capacity',
          required: true,
          label: 'Kapasitas',
          align: 'left',
          field: row => row.capacity,
          sortable: true
        },

        {
          name: 'status',
          required: true,
          label: 'Status',
          align: 'left',
          field: row => row.status,
          sortable: true
        },

        {
          name: 'createAt',
          required: true,
          label: 'Stamptime',
          align: 'left',
          field: row => row.createAt,
          sortable: true
        },
      ],
      data:[]
    }
  },
  beforeCreate(){

      let self = this
      project.getProject(window).then(function(datas) {
          return datas
      }).then(function(res){
          console.log(res)
          self.data = res
      }).catch(function(err){
          console.log(err)
      })
  }
}
</script>