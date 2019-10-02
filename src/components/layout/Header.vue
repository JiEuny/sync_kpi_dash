<template>
    <el-aside width="230px">
        <div class="logo-container">
          Dashboard
        </div>

        <el-menu default-active="2" class="el-menu-vertical-demo"
          background-color="#545c64" text-color="#fff" active-text-color="#ffd04b">

          <el-menu-item index="3">
            <i class="el-icon-menu"></i>
            <router-link to="/group">Group Analysis Chart</router-link>
          </el-menu-item>

          <el-menu-item index="4">
            <i class="el-icon-menu"></i>
            <router-link to="/day">Day Analysis Chart</router-link>
          </el-menu-item>

          <el-menu-item index="5">
            <i class="el-icon-menu"></i>
            <router-link to="/time">Time Analysis Chart</router-link>
          </el-menu-item>

        </el-menu>
    </el-aside>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style scoped>

 .header a {
     color: #fff;
     padding-right: 5px;
     text-decoration: none;
 }

</style>