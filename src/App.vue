<template>
  <div id="app">
    <el-container>
      <el-aside width="230px">
        <Header class="header"/>
      </el-aside>
      
        <router-view class="el-main"/>
      
    </el-container>
  </div>
</template>

<script>
import Header from './components/layout/Header'
export default {
  name: "app",
  components: {
    Header
  }
}
</script>

<style>
 * {
   box-sizing: border-box;
   margin: 0;
   padding: 0;
 }

 body {
   font-family: Arial, Helvetica, sans-serif;
   line-height: 1.4;
 }

 .el-aside {
   background: #545c64;
   color: white;
   min-height: 100vh;
 }

 .logo-container {
   padding: 22px;
   background: #434A50;
 }

 .el-menu {
   border-right: 0 !important;
 }

 .el-main {
   background: #EEF1F4;
 }

 .header a {
     color: #fff;
     padding-right: 5px;
     text-decoration: none;
 }

 
</style>
