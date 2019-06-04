<template>
    <div class="footer fixed">
      <ul>
        <li><router-link to="/" >首页</router-link></li>
        <li><router-link to="/manage">人员管理</router-link></li>
      </ul>
    </div>
</template>

<script>
    export default {
        name: "FooterNav"
    }
</script>

<style scoped>
li a{display:inline-block;width:100%;height:100%}
  .footer{width:100%;height: 50px;bottom:0}
  ul{display: flex;line-height: 50px}
  ul li{flex: 1;background-color: #f1f1f1}
.isIndex li:first-child{background: #00d1ff;}
.isIndex li:first-child a{color: #fff;}
.isManage li:last-child{background: #00d1ff;}
.isManage li:last-child a{color: #fff;}
</style>
