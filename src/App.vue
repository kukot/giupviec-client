<template>
<div id="app">
<h1>Therichpost.com</h1>
   
   <table id="tblLaoDong" class="table table-hover table-bordered">
    
  </table>
</div>
  
</template>

<script>
import "jquery/dist/jquery"
//import HelloWorld from './components/HelloWorld.vue'
import "datatables.net-dt/js/dataTables.dataTables"
//import axios from "axios"
import $ from 'jquery'
export default {
  mounted(){
    //API Call
    
      //this.users = res.data;
      $('#tblLaoDong').dataTable({
        serverSide: true,
        ajax: {
            url: 'http://localhost:8081/api/employees',
            type: 'GET',
            length: 10,
            start: 0,
        },
        columns: [
            {data: 'id'},
            {data: null},// name
            {data: 'phoneNumber'},
            {data: 'identityNumber'},           
        ],
        columnDefs: [
            // {
            //     targets: [0, 2, 3],
            //     sortable: false,
            // },
            {
                targets: 0,
                title: 'ID',
                searchable: false,
                sortable: false,
                width: '10%',
                render: function(data) {
                    return data;
                }
            },
            {
                targets: 1,
                title: 'Tên lao động',
                width: '30%',
                render: function(data, type, row) {
                    return row.lastName + ' ' + row.firstName;
                }
            },
            {
                targets: 2,
                title: 'Số điện thoại',
                width: '30%',
                render: function(data) {
                    return data;
                }
            },
            {
                targets: 3,
                title: 'Số CCCD',
                searchable: false,
                width: '30%',
                render: function(data) {
                    return data;
                }
            },
        ]
    })
  },
  data: function() {
        return {
            users:[]
        }
    },
}
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
