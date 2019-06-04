<template>
    <div class="manage tc">
      <button>新增</button>
      <div class="input-area">
        <input type="text" placeholder="请输入人员姓名">
        <button>确认</button>
      </div>
      <table>
        <tr>
          <th>姓名</th>
          <th>操作</th>
        </tr>
        <tr>
          <td>张三</td>
          <td>
            <span>编辑</span>
            <span>删除</span>
          </td>
        </tr>
      </table>
      <footer-nav v-bind:class="{'isManage':isNowPage}"></footer-nav>
    </div>
</template>

<script>
  import FooterNav from '../../components/FooterNav'
    export default {
        components:{
          FooterNav
        },
      data(){
          return{
            isNowPage:true,

          }
      }
    }
</script>

<style scoped>
  button{border: 1px solid #000;color:#000;width:50px;line-height: 30px;border-radius: 5px;margin-bottom: 10px;cursor: pointer}
  input{border: 1px solid #000;line-height: 30px}
  table td{width: 50%}
  table td{text-align: center;line-height: 30px;padding:5px 0}
</style>
