<template>
    <div class="header">
        <el-col :span="10" class="logo" :class="">WMS管理系统</el-col>
        <el-col :span="10">
            <div class="tools" ><i id="sider-toggle" class="glyphicon glyphicon-menu-hamburger" data-toggle="collapse" data-target="#siderbar"></i></div>
        </el-col>
      <div class="user-info">
        <el-dropdown trigger="click" @command="handleCommand">
            <span class="el-dropdown-link">
                <img class="user-logo" src="../../../static/img/img.jpg">
                {{username}}
            </span>
            <el-dropdown-menu slot="dropdown">
                <el-dropdown-item command="loginout">退出</el-dropdown-item>
            </el-dropdown-menu>
        </el-dropdown>
       </div>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                name: 'linxin',
                sysName: '',
                collapsed: false
            }
        },
        computed:{
            username(){
                let username = sessionStorage.UserName;
                return username ? username : this.name;
            }
        },
        methods:{
            handleCommand(command) {
                if(command == 'loginout'){
                    localStorage.removeItem('ms_username')
                    this.$router.push('/login');
                }
            },
            collapse() {
                this.collapsed = !this.collapsed
            }
        }
    }
    $(document).ready(() => {
        $('#sider-toggle').click(() => {
        
        })
    })
</script>
<style scoped>
    .header {
        position: relative;
        box-sizing: border-box;
        width: 100%;
        height: 50px;
        font-size: 22px;
        line-height: 50px;
        color: #fff;
    }
    .header .logo{
        float: left;
        width:200px;
        text-align: center;
    }
    .user-info {
        float: right;
        padding-right: 50px;
        font-size: 16px;
        color: #fff;
    }
    .user-info .el-dropdown-link{
        position: relative;
        display: inline-block;
        padding-left: 50px;
        color: #fff;
        cursor: pointer;
        vertical-align: middle;
    }
    .user-info .user-logo{
        position: absolute;
        left:0;
        top:5px;
        width:40px;
        height:40px;
        border-radius: 50%;
    }
    .el-dropdown-menu__item{
        text-align: center;
    }
</style>
