<template>
    <div class="manage tc">
      <button v-on:click="add">新增</button>
      <div class="input-area" v-show="showAdd">
        <input type="text" placeholder="请输入人员姓名" v-model="nameValue">
        <button v-on:click="addName">确认</button>
      </div>
      <table>
        <tr>
          <th>姓名</th>
          <th>操作</th>
        </tr>
        <tr v-for="(item,index) in peoples">
          <td>{{item.name}}</td>
          <td v-bind:id="index">
            <span v-on:click="edit">编辑</span>
            <span v-on:click="del">删除</span>
          </td>
        </tr>
      </table>
      <div class="wrap" v-show="showEdit">
        <div class="content">
          <input type="text" placeholder="请输入新姓名" v-model="newName">
          <button v-on:click="cancel">取消</button>
          <button v-on:click="editName">确定</button>
        </div>
      </div>
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
            peoples:[{'name':'flin'},{'name':'fchao'}],
            showAdd:false,
            nameValue:'',
            showEdit:false,
            newName:'',
            editId:0
          }
      },
      methods:{
          add(){
            this.showAdd = true
          },
        addName(){
            var v = this.nameValue
            if(v.trim()==""){
              alert("请输入新增人员姓名")
            }else{
              var data={}
              data.name=v
              this.peoples.push(data)
            }
        },
        del(e){
            var id=e.target.offsetParent.id
            this.peoples.splice(id,1)
        },
        edit(e){
            var id=e.target.offsetParent.id
            this.showEdit=true
            this.editId=id
            this.newName=this.peoples[id].name
        },
        cancel(){
            this.showEdit=false
        },
        editName(){
            var v=this.newName
          if(v.trim()==""){
            alert("请输入姓名")
          }else{
            this.peoples[this.editId].name=this.newName
            this.showEdit=false
          }

        }
      }
    }
</script>

<style scoped>
  button{border: 1px solid #000;color:#000;width:50px;line-height: 30px;border-radius: 5px;margin-bottom: 10px;cursor: pointer}
  input{border: 1px solid #000;line-height: 30px;width:300px}
  table td{width: 50%}
  table td{text-align: center;line-height: 30px;padding:5px 0}
  table span{cursor: pointer}
  .wrap{background: rgba(0,0,0,.1);position: fixed;width: 100%;height: 100%;top: 0;z-index: 99}
  .content{width: 500px;margin: 200px auto 0}
  .content input{background: #fff}
  .content button{width:50px;background: #00d1ff}
</style>
