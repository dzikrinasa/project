<template>
   <a-layout id="components-layout-demo-top-side">
    <a-layout-header class="header">
      <div class="logo"/>
      <a-menu class="menu"
        mode="horizontal"
        :defaultSelectedKeys="['2']"
        :style="{ lineHeight: '60px' }"
      >
        <a-menu-item key="1"><B style="font-size:24px; color:#fff; margin-left:400px"> UNDANGAN.com</B></a-menu-item>
      </a-menu>
    </a-layout-header>
    <a-layout-content style="padding: 0 50px">
      <a-breadcrumb style="margin: 16px 0">
        <a-breadcrumb-item> &nbsp;</a-breadcrumb-item>
      </a-breadcrumb>
      <a-layout style="padding: 24px 0; background: #fff">
        <a-layout-sider width="200" style="background: #fff">
          <a-menu 
            mode="inline"
            style="height: 100%; background: #1A8FFC;"
          >
             <a-button style="margin-bottom:20px; margin-left:20px; margin-top:20px; width:150px" type="default"><a-icon type="form" />DAFTAR</a-button>
           
             <a-button style="margin-bottom:20px; margin-left:20px; margin-top:20px; width:150px" type="default"><a-icon type="login" />MASUK</a-button>
          
            <a-button style="margin-bottom:20px; margin-left:20px; margin-left:20px;margin-left:20px;margin-left:20px;margin-top:20px; width:150px" type="default"><a-icon type="file" />UNDANGAN</a-button>
          


          </a-menu >
        </a-layout-sider>

        <a-layout-content :style="{ padding: '0 24px', minHeight: '280px' }">
        
        <p> <b style="margin-left:350px; margin-top:70px; background-color: #ADD8E6;"> Kode Permohonan Undangan </b> </p>
        <a-input-search placeholder="Isi Kode Permohonan" style="width: 200px ; margin-left: 350px;" @search="onSearch" />
    

        </a-layout-content>
      </a-layout>
    </a-layout-content>
    <a-layout-footer style="margin-left: 565px;">
      Front-End ©2019 Praxis Academy
    </a-layout-footer>
  </a-layout>

  </template>


<script>
import axios from "axios";
import Data from "./form1.vue";
const baseURL ="http://localhost:3000/data"

      export default {
      components: {
        Data
      },

        name: 'app',
        data(){
      return{
        todos:[],
        todoJenis: '',
        todoNama: '',
        todoWaktu: '',
        todoScan: ''
      };

        },
        async created(){
          try{
            const res = await axios.get(baseURL);
            this.todos = res.data;
          }
    catch(e){
      console.error(e);
    }

        },

        methods: {
        async addTodo(){
        const res = await axios.post(baseURL, { jenis: this.todoJenis, nama: this.todoNama, waktu: this.todoWaktu,scan: this.todoScan  });
        this.todos = [...this.todos, res.data];
        this.todoJenis = "";
        this.todoNama = "";
        this.todoWaktu = "";
        this.todoScan = "";
        }

        }
      };
</script>

<style>
#components-layout-demo-top-side .logo {
  width: 120px;
  height: 31px;
  margin: 16px 28px 16px 0;
  float: left;
}
#components-layout-demo-top-side .header {
  background-color:#1A8FFC;
}
#components-layout-demo-top-side .menu{
  background-color:#1A8FFC;
}
 .upload-list-inline >>> .ant-upload-list-item {
    float: left;
    width: 200px;
    margin-right: 8px;
  }
  .upload-list-inline >>> .ant-upload-animate-enter {
    animation-name: uploadAnimateInlineIn;
  }
  .upload-list-inline >>> .ant-upload-animate-leave {
    animation-name: uploadAnimateInlineOut;
  }


</style>


