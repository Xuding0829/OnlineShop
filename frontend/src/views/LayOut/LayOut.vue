<template>


 <div class="common-layout">
    <el-container>
      <el-header class="common-header flex-float"> 
           <div class="flex" @click="toWelcome" style="cursor:pointer" title="前往首页">
                <img class="logo" src="../../assets/logo.png" alt="logo">
                <h1 class="title">商城后台管理系统</h1>
           </div>  
           <div @click="toAbout" style="cursor:pointer" title="关于我们">
                <h1 class="title" >Author: 王健彬、李晨海、楼泳锋</h1>
           </div>
            <el-button @click="loginOut">退出</el-button>
      </el-header>
      <el-container>
        <el-aside class="common-aside" width="200px">
            <el-menu
                background-color="none"
                text-color="#fff"
                :router="true"
            >
                <el-sub-menu index="1">
                    <template #title> 
                        <el-icon><Avatar /></el-icon>
                        <span>账号管理</span>
                    </template>
                     <el-menu-item-group>
                        <el-menu-item index="/user">账号列表</el-menu-item> 
                    </el-menu-item-group>
                </el-sub-menu>
                <el-sub-menu index="2">
                    <template #title>
                        <el-icon><UserFilled /></el-icon>
                        <span>角色管理</span>
                    </template>
                     <el-menu-item-group>
                        <el-menu-item index="/roles">角色列表</el-menu-item> 
                    </el-menu-item-group>
                </el-sub-menu>
                <el-sub-menu index="3">
                    <template #title>
                        <el-icon><Box /></el-icon>
                        <span>商品管理</span>
                    </template>
                     <el-menu-item-group>
                        <el-menu-item index="/goods">商品列表</el-menu-item> 
                    </el-menu-item-group>
                </el-sub-menu>
                <el-menu-item index="/about">
                    <template #title> 
                        <el-icon><Bell /></el-icon>
                        <span>About</span> 
                    </template>
                </el-menu-item>
            </el-menu>
        </el-aside>
        <el-main>
            
        <!-- router-view -->
        <router-view></router-view>
        </el-main>
      </el-container>
    <el-footer class="common-footer flex-float" height="30">
        <div>违法和不良信息举报99999999@qq.com  经营许可证：浙A2-20110026 浙ICP备11017770号 copyright© 2016-2017 浙江A&F信息工程学院版权所有</div>
    </el-footer>
    </el-container>
  </div>
  
</template>
<script>
import { useRouter } from 'vue-router'
import { useStore } from "vuex" 
export default {
    name:"layout",
    setup() {
        const store = useStore()
        const router = useRouter()
        const loginOut=()=>{
            localStorage.removeItem("loginData")
            store.commit('setUserInfo', {});
            router.push({
                path:"/login"
            })

        }
        const toWelcome = ()=> {
            router.push({
                path:"/"
            })
        }
        const toAbout = ()=> {
            router.push({
                path:"/about"
            })
        }
        return{
            loginOut,
            toAbout,
            toWelcome
        }
    }
}
</script> 
<style >
    .el-container{
        height: 100vh;
        overflow: hidden;
    }
    .common-header{
        background: rgb(39, 45, 53); 
    } 
    .common-footer{
        background: rgb(111, 120, 148);
        align-items: center;
    }
    .common-aside{
        background: rgb(48, 55, 65);
    }
    .logo{
        width: 80px;
    }
    .title{
        color: #fff;
    }
    .el-main{
        background: #efefef;
    }
</style>